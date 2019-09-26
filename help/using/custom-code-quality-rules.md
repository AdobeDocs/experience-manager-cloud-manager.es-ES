---
title: Reglas de calidad de código personalizadas
seo-title: Reglas de calidad de código personalizadas
description: Siga esta página para conocer las reglas de calidad de código personalizadas ejecutadas por Cloud Manager.
seo-description: Siga esta página para conocer las reglas de calidad de código personalizadas ejecutadas por Adobe Experience Manager Cloud Manager.
uuid: a7feb465-1982-46be-9e57-e67b59849579
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: d2338c74-3278-49e6-a186-6ef62362509f
translation-type: tm+mt
source-git-commit: 4881ff8be97451aa90c3430259ce13faef182e4f

---


# Reglas de calidad de código personalizadas {#custom-code-quality-rules}

En esta página se describen las reglas de calidad de código personalizadas ejecutadas por Cloud Manager creadas en función de las prácticas recomendadas de ingeniería de AEM.

>[!NOTE]
>
>Las muestras de código que se proporcionan aquí tienen fines ilustrativos.

## Reglas de SonarQube {#sonarqube-rules}

La siguiente sección resalta las reglas de SonarQube:

### No utilizar funciones potencialmente peligrosas {#do-not-use-potentially-dangerous-functions}

**Clave**: CQRules:CWE-676

**Tipo**: Vulnerabilidad

**Gravedad**: Mayor

**Since: Version 2018.4.0**

Los métodos ***Thread.stop()*** y ***Thread.interrupt()*** pueden producir problemas difíciles de reproducir y, en algunos casos, vulnerabilidades de seguridad. Their usage should be tightly monitored and validated. In general, message passing is a safer way to accomplish similar goals.

#### Non-Compliant Code {#non-compliant-code}

```java
public class DontDoThis implements Runnable {
  private Thread thread;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    thread.stop();  // UNSAFE!
  }
 
  public void run() {
    while (true) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

#### Compliant Code {#compliant-code}

```java
public class DoThis implements Runnable {
  private Thread thread;
  private boolean keepGoing = true;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    keepGoing = false;
  }
 
  public void run() {
    while (this.keepGoing) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

### Do not use format strings which may be externally controlled {#do-not-use-format-strings-which-may-be-externally-controlled}

**Key: CQRules:CWE-134**

**Type: Vulnerability**

**Severity: Major**

**Since: Version 2018.4.0**

Using a format string from an external source (such a request parameter or user-generated content) can produce can expose an application to denial of service attacks. There are circumstances where a format string may be externally controlled, but is only allowed from trusted sources.

#### Non-Compliant Code {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text");
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### Las solicitudes HTTP siempre deben tener tiempos de espera de conexión y socket {#http-requests-should-always-have-socket-and-connect-timeouts}

**Clave**: CQRules:ConnectionTimeoutFacility

**Tipo**: Error

**Gravedad**: Crítico

**Desde**: Versión 2018.6.0

Al ejecutar solicitudes HTTP desde una aplicación AEM, es fundamental asegurarse de que se han configurado los tiempos de espera adecuados para evitar un consumo de subproceso innecesario. Unfortunately, the default behavior of both Java's default HTTP Client (java.net.HttpUrlConnection) and the commonly used Apache HTTP Components client is to never timeout, so timeouts must be explicitly set. Further, as a best practice, these timeouts should be no more than 60 seconds.

#### Código no compatible {#non-compliant-code-2}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void dontDoThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  HttpClient httpClient = builder.build();

  // do something with the client
}

public void dontDoThisEither() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

#### Código compatible {#compliant-code-1}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void doThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  RequestConfig requestConfig = RequestConfig.custom()
    .setConnectTimeout(5000)
    .setSocketTimeout(5000)
    .build();
  builder.setDefaultRequestConfig(requestConfig);
 
  HttpClient httpClient = builder.build();
   
  // do something with the client
}

public void orDoThis() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
  urlConnection.setConnectTimeout(5000);
  urlConnection.setReadTimeout(5000);
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

### Las API de producto anotadas con @ProviderType no deben ser implementadas o ampliadas por los clientes {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

**Clave**: CQBP-84, dependencias CQBP-84

**Tipo**: Error

**Gravedad**: Crítico

**Desde**: Versión 2018.7.0

La API de AEM contiene interfaces y clases de Java que solo están pensadas para utilizarse, pero no implementadas, mediante código personalizado. Por ejemplo, la interfaz *com.day.cq.wcm.api.Page* está diseñada para que la implemente solo ****** AEM.

Cuando se añaden nuevos métodos a estas interfaces, esos métodos adicionales no afectan al código existente que utiliza estas interfaces y, como resultado, la adición de nuevos métodos a estas interfaces se considera compatible con versiones anteriores. Sin embargo, si el código personalizado ***implementa*** una de estas interfaces, dicho código personalizado ha introducido un riesgo de compatibilidad con versiones anteriores para el cliente.

Las interfaces (y clases) que solo AEM pretende implementar se anotan con *org.osgi.anottation.versioning.ProviderType* (o, en algunos casos, una anotación heredada similar *a Qute.bnd.anottation.ProviderType*). Esta regla identifica los casos en los que una interfaz de este tipo se implementa (o una clase se amplía) mediante código personalizado.

#### Código no compatible {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Los objetos ResourceResolver siempre deben cerrarse {#resourceresolver-objects-should-always-be-closed}

**Clave**: CQRules:CQBP-72

**Tipo**: Huele de código

**Gravedad**: Mayor

**Desde**: Versión 2018.4.0

Los objetos ResourceResolver obtenidos de ResourceResolverFactory consumen recursos del sistema. Aunque existen medidas para recuperar estos recursos cuando ResourceResolver ya no se utiliza, es más eficaz cerrar explícitamente cualquier objeto ResourceResolver abierto llamando al método close().

Una idea errónea relativamente común es que los objetos ResourceResolver creados con una sesión de JCR existente no deben cerrarse explícitamente o que, al hacerlo, se cerrará la sesión de JCR subyacente. Este no es el caso, independientemente de cómo se abra un ResourceResolver, debe cerrarse cuando ya no se utilice. Dado que ResourceResolver implementa la interfaz Closeable, también es posible utilizar la sintaxis try-with-resources en lugar de invocar explícitamente close().

#### Non-Compliant Code {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### Compliant Code {#compliant-code-2}

```java
public void doThis(Session session) throws Exception {
  ResourceResolver resolver = null;
  try {
    resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
    // do something with the resolver
  } finally {
    if (resolver != null) {
      resolver.close();
    }
  }
}

public void orDoThis(Session session) throws Exception {
  try (ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object) session))){
    // do something with the resolver
  }
}
```

### Do not use Sling servlet paths to register servlets {#do-not-use-sling-servlet-paths-to-register-servlets}

**Key: CQRules:CQBP-75**

**Type: Code Smell**

**Severity: Major**

**Desde**: Versión 2018.4.0

As described in the Sling documentation, bindings servlets by paths is discouraged. [](http://sling.apache.org/documentation/the-sling-engine/servlets.html) Path-bound servlets cannot use standard JCR access controls and, as a result, require additional security rigor. Rather than using path-bound servlets, it is recommended to create nodes in the repository and register servlets by resource type.

#### Non-Compliant Code {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Las excepciones capturadas deben registrarse o emitirse, pero no ambas {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

**Clave**: CQRules:CQBP-44—CatchAndOrLogOrThrow

**Tipo**: Huele de código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

In general, an exception should be logged exactly one time. Logging exceptions multiple times can cause confusion as it is unclear how many times an exception occurred. El patrón más común que lleva a esto es registrar y lanzar una excepción capturada.

#### Código no compatible {#non-compliant-code-6}

```java
public void dontDoThis() throws Exception {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
    throw e;
  }
}
```

#### Código compatible {#compliant-code-3}

```java
public void doThis() {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
  }
}

public void orDoThis() throws MyCustomException {
  try {
    someOperation();
  } catch (Exception e) {
    throw new MyCustomException(e);
  }
}
```

### Evite tener una instrucción de registro seguida inmediatamente de una sentencia de lanzamiento {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

**Clave**: CQRules:CQBP-44—ConsecutivamenteLogAndThrow

**Tipo**: Huele de código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

Otro patrón común que hay que evitar es registrar un mensaje y luego emitir inmediatamente una excepción. Esto generalmente indica que el mensaje de excepción terminará duplicado en los archivos de registro.

#### Código no compatible {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### Código compatible {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### Evite iniciar sesión en INFO al administrar solicitudes GET o HEAD {#avoid-logging-at-info-when-handling-get-or-head-requests}

**Clave**: CQRules:CQBP-44—LogInfoInGetOrHeadRequests

**Tipo**: Huele de código

**Gravedad**: Menor

En general, el nivel de registro INFO debe utilizarse para delimitar acciones importantes y, de forma predeterminada, AEM está configurado para iniciar sesión en el nivel INFO o superior. Los métodos GET y HEAD sólo deben ser operaciones de sólo lectura y por lo tanto no constituyen acciones importantes. Es probable que el registro en el nivel INFO en respuesta a las solicitudes GET o HEAD cree un ruido de registro significativo, lo que dificulta la identificación de información útil en los archivos de registro. El registro al administrar las solicitudes GET o HEAD debe estar en los niveles WARN o ERROR cuando algo ha salido mal o en los niveles DEBUG o TRACE si resulta útil obtener información más detallada sobre la solución de problemas.

>[!CAUTION]
>
>Esto no se aplica al registro de tipo access.log para cada solicitud.

#### Non-Compliant Code {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### Compliant Code {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### No use Exception.getMessage() como primer parámetro de una instrucción de registro {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

**Key: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam**

**Type: Code Smell**

**Severity: Minor**

**Since: Version 2018.4.0**

Como práctica recomendada, los mensajes de registro deben proporcionar información contextual sobre dónde se produjo una excepción en la aplicación. Aunque el contexto también se puede determinar mediante el uso de trazos de pila, en general el mensaje de registro será más fácil de leer y comprender. Como resultado, al registrar una excepción, es una mala práctica utilizar el mensaje de excepción como mensaje de registro: el mensaje de excepción contendrá lo que salió mal, mientras que el mensaje de registro debe utilizarse para indicar a un lector de registro qué estaba haciendo la aplicación cuando se produjo la excepción. Se seguirá registrando el mensaje de excepción; al especificar su propio mensaje, los registros serán más fáciles de entender.

#### Código no compatible {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### Código compatible {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### El inicio de sesión en bloques catch debe estar en el nivel WARN o ERROR {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

**Clave**: CQRules:CQBP-44—WrongLogLevelInCatchBlock

**Tipo**: Huele de código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

Como sugiere el nombre, las excepciones de Java siempre deben usarse en circunstancias *excepcionales* . Como resultado, cuando se detecta una excepción, es importante asegurarse de que los mensajes de registro se registran en el nivel adecuado, ya sea WARN o ERROR. Esto garantiza que esos mensajes aparezcan correctamente en los registros.

#### Código no compatible {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### Código compatible {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### No imprimir trazos de pila en la consola {#do-not-print-stack-traces-to-the-console}

**Clave**: CQRules:CQBP-44—ExceptionPrintStackTrace

**Tipo**: Huele de código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

Como se ha mencionado anteriormente, el contexto es fundamental para comprender los mensajes de registro. El uso de Exception.printStackTrace() hace que **solo** el seguimiento de pila se envíe al flujo de error estándar, con lo que se pierde todo el contexto. Además, en una aplicación con varios subprocesos como AEM, si se imprimen varias excepciones mediante este método en paralelo, sus trazos de pila pueden superponerse, lo que produce una confusión significativa. Las excepciones solo se deben registrar a través del módulo de registro.

#### Código no compatible {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### Compliant Code {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Do not output to Standard Output or Standard Error {#do-not-output-to-standard-output-or-standard-error}

**Key: CQRules:CQBP-44—LogLevelConsolePrinters**

**Tipo**: Huele de código

**Severity: Minor**

**Desde**: Versión 2018.4.0

El inicio de sesión en AEM siempre debe realizarse a través del marco de registro (SLF4J). La salida directa a los flujos de error estándar o de salida estándar pierde la información estructural y contextual proporcionada por el marco de registro y, en algunos casos, puede causar problemas de rendimiento.

#### Código no compatible {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### Compliant Code {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Evite las rutas /apps y /libs codificadas {#avoid-hardcoded-apps-and-libs-paths}

**Clave**: CQRules:CQBP-71

**Tipo**: Huele de código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

En general, las rutas que comienzan con /libs y /apps no deben codificarse de forma rígida, ya que las rutas a las que hacen referencia se almacenan normalmente como rutas relativas a la ruta de búsqueda Sling (que se establece en /libs,/apps de forma predeterminada). El uso de la ruta absoluta puede introducir defectos sutiles que solo aparecerían más adelante en el ciclo vital del proyecto.

#### Código no compatible {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### Código compatible {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```


## Reglas de contenido OakPAL {#oakpal-rules}

Debajo de las comprobaciones OakPAL ejecutadas por Cloud Manager.

>[!NOTE]
>OakPAL es un marco de trabajo desarrollado por un socio de AEM (y ganador de AEM Rockstar Norteamérica en 2019) que valida los paquetes de contenido mediante un repositorio Oak independiente.

### Los paquetes de clientes no deben crear ni modificar nodos en /libs {#oakpal-customer-package}

**Clave**: BannedPath

**Tipo**: Error

**Gravedad**: Bloqueador

**Desde**: Versión 2019.6.0

Desde hace tiempo, se recomienda que los clientes consideren el árbol de contenido /libs del repositorio de contenido de AEM como de solo lectura. Modifying nodes and properties under /libs creates significant risk for major and minor updates. ** Las modificaciones a */libs* solo deben realizarlas Adobe a través de canales oficiales.

### Los paquetes no deben contener configuraciones OSGi duplicadas {#oakpal-package-osgi}

**Clave**: DuplicateOsgiConfigurations

**Type: Bug**

**Severity: Major**

**Since: Version 2019.6.0**

Un problema común que se produce en proyectos complejos es que el mismo componente OSGi se configura varias veces. Esto crea una ambigüedad en cuanto a la configuración que puede funcionar. Esta regla tiene en cuenta el modo de ejecución, ya que solo identificará problemas en los que el mismo componente se haya configurado varias veces en el mismo modo de ejecución (o combinación de modos de ejecución).

#### Código no compatible {#non-compliant-code-osgi}

```+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Código compatible {#compliant-code-osgi}

```+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Las carpetas de configuración e instalación solo deben contener nodos OSGi {#oakpal-config-install}

**Clave**: ConfigAndInstallMustOnlyContainOsgiNodes

**Tipo**: Error

**Gravedad**: Mayor

**Desde**: Versión 2019.6.0

Por motivos de seguridad, las rutas que contienen */config/ y /install/* solo las pueden leer los usuarios administrativos en AEM y solo deben utilizarse para la configuración OSGi y los paquetes OSGi. Colocar otros tipos de contenido bajo rutas que contengan estos segmentos resulta en un comportamiento de aplicación que varía involuntariamente entre usuarios administrativos y no administrativos.

Un problema común es el uso de nodos denominados `config` dentro de los cuadros de diálogo de componentes o al especificar la configuración del editor de texto enriquecido para la edición en línea. Para resolver esto, se debe cambiar el nombre del nodo infractor por un nombre compatible. Para la configuración del editor de texto enriquecido, utilice la `configPath` propiedad del `cq:inplaceEditing` nodo para especificar la nueva ubicación.

#### Código no compatible {#non-compliant-code-config-install}

```
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Código compatible {#compliant-code-config-install}

```
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### Los paquetes no deben superponerse {#oakpal-no-overlap}

**Clave**: PackageOverlaps

**Tipo**: Error

**Gravedad**: Mayor

**Desde**: Versión 2019.6.0

De manera similar a *los paquetes no deben contener configuraciones* OSGi duplicadas, este es un problema común en proyectos complejos en los que la misma ruta de nodo está escrita por varios paquetes de contenido independientes. Aunque se pueden utilizar dependencias de paquetes de contenido para garantizar un resultado coherente, es mejor evitar las superposiciones por completo.
