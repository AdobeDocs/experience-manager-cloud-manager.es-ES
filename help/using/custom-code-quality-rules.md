---
title: Reglas de calidad de código personalizado
seo-title: Reglas de calidad de código personalizado
description: Siga esta página para obtener información sobre las reglas de calidad de código personalizadas ejecutadas por Cloud Manager.
seo-description: Siga esta página para obtener información sobre las reglas de calidad de código personalizadas ejecutadas por Adobe Experience Manager Cloud Manager.
uuid: a 7 feb 465-1982-46 be -9 e 57-e 67 b 59849579
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: d 2338 c 74-3278-49 e 6-a 186-6 ef 62362509 f
translation-type: tm+mt
source-git-commit: f76b8e6a036ab920f11fb913d3ad29818f1e153f

---


# Custom Code Quality Rules {#custom-code-quality-rules}

Esta página describe las reglas de calidad de código personalizadas ejecutadas por Cloud Manager creadas en función de las prácticas recomendadas de Ingeniería de AEM.

>[!NOTE]
>
>Las muestras de código proporcionadas aquí son sólo para fines ilustrativos.

## SonarQube Rules {#sonarqube-rules}

La siguiente sección resalta las reglas de sonarchbe:

### Do not use potentially dangerous functions {#do-not-use-potentially-dangerous-functions}

**Clave**: Cqrules: CWE -676

**Tipo**: Vulnerabilidad

**Gravedad**: Mayor

**Desde**: Versión 2018.4.0

The methods ***Thread.stop()*** and ***Thread.interrupt()*** can produce hard-to-reproduce issues and, in some cases, security vulnerabilities. Su uso debe monitorearse y validarse de manera estricta. En general, el paso de mensajes es una manera más segura de lograr objetivos similares.

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

**Clave**: Cqrules: CWE -134

**Tipo**: Vulnerabilidad

**Gravedad**: Mayor

**Desde**: Versión 2018.4.0

El uso de una cadena de formato de una fuente externa (como un parámetro de solicitud o contenido generado por usuarios) puede exponer una aplicación a ataques de denegación de servicio. Existen circunstancias en las que una cadena de formato puede estar controlada externamente, pero solo se permite desde fuentes de confianza.

#### Non-Compliant Code {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text");
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP requests should always have socket and connect timeouts {#http-requests-should-always-have-socket-and-connect-timeouts}

**Clave**: Cqrules: Connectiontimeoutcomponent

**Tipo**: Error

**Gravedad**: Crítico

**Desde**: Versión 2018.6.0

Cuando se ejecutan solicitudes HTTP desde una aplicación AEM, es fundamental asegurarse de que los tiempos de espera adecuados estén configurados para evitar consumo ininnecesario de procesos. Desafortunadamente, el comportamiento predeterminado del cliente HTTP predeterminado de Java (java.net.Ht tpurlconnection) y del cliente de componentes Apache HTTP de uso habitual es nunca el tiempo de espera, por lo que los tiempos de espera deben establecerse explícitamente. Además, como práctica recomendada, estos tiempos de espera no deben exceder los 60 segundos.

#### Non-Compliant Code {#non-compliant-code-2}

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

#### Compliant Code {#compliant-code-1}

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

### Product APIs annotated with @ProviderType should not be implemented or extended by customers {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

**Clave**: CQBP -84, CQBP -84-dependencias

**Tipo**: Error

**Gravedad**: Crítico

**Desde**: Versión 2018.7.0

La API de AEM contiene interfaces y clases Java que solo están pensadas para utilizarse, pero no implementadas, por código personalizado. For example, the interface *com.day.cq.wcm.api.Page* is designed to be implemented by ***AEM only***.

Cuando se agregan nuevos métodos a estas interfaces, estos métodos adicionales no afectan al código existente que utiliza estas interfaces y, como resultado, la adición de nuevos métodos a estas interfaces se considera compatible con versiones anteriores. However, if custom code ***implements*** one of these interfaces, that custom code has introduced a backwards-compatibility risk for the customer.

Interfaces (and classes) which are only intended to be implemented by AEM are annotated with *org.osgi.annotation.versioning.ProviderType* (or, in some cases, a similar legacy annotation *aQute.bnd.annotation.ProviderType*). Esta regla identifica los casos en que se implementa una interfaz de este tipo (o una clase) por código personalizado.

#### Non-Compliant Code {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### ResourceResolver objects should always be closed {#resourceresolver-objects-should-always-be-closed}

**Clave**: Cqrules: CQBP -72

**Tipo**: Huelgar código

**Gravedad**: Mayor

**Desde**: Versión 2018.4.0

Resourceresolver objetos obtenidos de resourceresolverfactory consumen recursos del sistema. Aunque existen medidas para reclamar estos recursos cuando resourceresolver ya no está en uso, es más eficaz cerrar explícitamente cualquier objeto resourceresolver abierto llamando al método close ().

Una mala idea relativamente común es que los objetos resourceresolver creados con una sesión JCR existente no deben cerrarse explícitamente o que al hacerlo se cierre la sesión JCR subyacente. Este no es el caso: sin importar cómo se abra resourceresolver, debe cerrarse cuando ya no se utilice. Como resourceresolver implementa la interfaz Closeable, también es posible utilizar la sintaxis try-with-resources en lugar de invocar explícitamente close ().

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

**Clave**: Cqrules: CQBP -75

**Tipo**: Huelgar código

**Gravedad**: Mayor

**Desde**: Versión 2018.4.0

As described in the [Sling documentation](http://sling.apache.org/documentation/the-sling-engine/servlets.html), bindings servlets by paths is discouraged. Los servlets enlazados por rutas no pueden utilizar controles de acceso JCR estándar y, como resultado, requieren un rigor de seguridad adicional. En lugar de utilizar servlets enlazados por rutas, se recomienda crear nodos en el repositorio y registrar servlets por tipo de recurso.

#### Non-Compliant Code {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Caught Exceptions should be logged or thrown, but not both {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

**Clave**: Cqrules: CQBP -44—Catchandeitherlogorthrow

**Tipo**: Huelgar código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

En general, se debe registrar una excepción una vez. Registrar las excepciones varias veces puede causar confusión, ya que no está claro cuántas veces ha tenido lugar una excepción. Patrón más común que lleva a esto y genera una excepción detectada.

#### Non-Compliant Code {#non-compliant-code-6}

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

#### Compliant Code {#compliant-code-3}

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

### Avoid having a log statement immediately followed by a throw statement {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

**Clave**: Cqrules: CQBP -44—Consecutivelylogandthrow

**Tipo**: Huelgar código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

Otro patrón común para evitar es registrar un mensaje y, a continuación, emitir inmediatamente una excepción. Esto suele indicar que el mensaje de excepción terminará duplicado en los archivos de registro.

#### Non-Compliant Code {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### Compliant Code {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### Avoid logging at INFO when handling GET or HEAD requests {#avoid-logging-at-info-when-handling-get-or-head-requests}

**Clave**: Cqrules: CQBP -44—Loginfoingetorheadrequests

**Tipo**: Huelgar código

**Gravedad**: Menor

En general, el nivel de registro de información debe utilizarse para delimitar acciones importantes y, de forma predeterminada, AEM está configurado para registrarse en el nivel INFO o superior. Los métodos GET y HEAD solo deben ser operaciones de solo lectura y, por lo tanto, no constituyen acciones importantes. El registro en el nivel de información como respuesta a las solicitudes GET o HEAD probablemente cree un ruido de registro significativo que dificulte la identificación de información útil en los archivos de registro. El registro al gestionar las solicitudes GET o HEAD debe estar en los niveles WARN o ERROR cuando algo incorrecto o en los niveles DEBUG o TRACE si información de solución de problemas más profunda resulta útil.

>[!CAUTION]
>
>Esto no se aplica al registro de access. log-type para cada solicitud.

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

### Do not use Exception.getMessage() as the first parameter of a logging statement {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

**Clave**: Cqrules: CQBP -44—Exceptiongetmessageisfirstlogparam

**Tipo**: Huelgar código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

Como práctica recomendada, los mensajes de registro deben proporcionar información contextual sobre dónde se ha producido una excepción. Aunque el contexto también se puede determinar mediante el uso de huellas de pila, en general el mensaje de registro será más fácil de leer y comprender. Como resultado, al registrar una excepción, se recomienda utilizar el mensaje de excepción como mensaje de registro; el mensaje de excepción contendrá lo que salió mal, mientras que el mensaje de registro debe utilizarse para informar a un lector de registro de lo que estaba haciendo la aplicación cuando se produjo la excepción. El mensaje de excepción seguirá registrándose; al especificar su propio mensaje, los registros solo serán fáciles de entender.

#### Non-Compliant Code {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### Compliant Code {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Logging in catch blocks should be at the WARN or ERROR level {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

**Clave**: Cqrules: CQBP -44—Wrongloglevelincatchblock

**Tipo**: Huelgar código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

As the name suggests, Java exceptions should always be used in *exceptional* circumstances. Como resultado, cuando se captura una excepción, es importante asegurarse de que los mensajes de registro se registran en el nivel adecuado, ya sea WARN o ERROR. Esto garantiza que esos mensajes aparezcan correctamente en los registros.

#### Non-Compliant Code {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### Compliant Code {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Do not print stack traces to the console {#do-not-print-stack-traces-to-the-console}

**Clave**: Cqrules: CQBP -44—Exceptionprintstacktrace

**Tipo**: Huelgar código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

Como se ha mencionado, el contexto es crítico al comprender los mensajes de registro. Using Exception.printStackTrace() causes **only** the stack trace to be output to the standard error stream thereby losing all context. Además, en una aplicación multiproceso como AEM si se imprimen varias excepciones mediante este método en paralelo, sus traces de pila pueden superponerse lo cual produce una confusión significativa. Las excepciones solo deben registrarse a través del marco de registro.

#### Non-Compliant Code {#non-compliant-code-11}

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

**Clave**: Cqrules: CQBP -44—loglevelconsolflagprinters

**Tipo**: Huelgar código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

El inicio de sesión en AEM debe realizarse siempre mediante el marco de registro (SLF 4 J). La salida directa a los flujos de error estándar o estándar pierde la información estructural y contextual proporcionada por el marco de registro y, en algunos casos, puede provocar problemas de rendimiento.

#### Non-Compliant Code {#non-compliant-code-12}

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

### Avoid Hardcoded /apps and /libs Paths {#avoid-hardcoded-apps-and-libs-paths}

**Clave**: Cqrules: CQBP -71

**Tipo**: Huelgar código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

En general, las rutas que comienzan con /libs y /apps no deben estar codificadas como las rutas a las que hacen referencia más comúnmente como rutas relativas a la ruta de búsqueda Sling (que se establece en /libs o en aplicaciones de forma predeterminada). El uso de la ruta absoluta puede introducir defectos sutiles que solo aparecerían más adelante en el ciclo vital del proyecto.

#### Non-Compliant Code {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### Compliant Code {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```


## OakPAL Content Rules {#oakpal-rules}

Se encuentra debajo de las comprobaciones oakpal ejecutadas por Cloud Manager.

>[!NOTE]
>Oakpal es un marco desarrollado por un partner AEM Partner (y ganador de 2019 AEM Rockstar North America) que valida los paquetes de contenido con un repositorio independiente de Oak.

### Customer Packages Should Not Create or Modify Nodes Under /libs {#oakpal-customer-package}

**Clave**: Bannedpaths

**Tipo**: Error

**Gravedad**: Bloqueador

**Desde**: Versión 2019.6.0

Es recomendable que el /libs de contenido de Adobe en el repositorio de contenido de AEM sea considerado solo lectura por clientes. Modifying nodes and properties under */libs* creates significant risk for major and minor updates. Modifications to */libs* should only be made by Adobe through official channels.

### Packages Should Not Contain Duplicate OSGi Configurations {#oakpal-package-osgi}

**Clave**: Duplicateosgiconfigurations

**Tipo**: Error

**Gravedad**: Mayor

**Desde**: Versión 2019.6.0

Un problema común que ocurre en proyectos complejos es donde el mismo componente osgi está configurado varias veces. Esto crea una ambigüedad con respecto a la configuración que se operará. Esta regla es «runmode-aware», ya que solo identificará los problemas donde el mismo componente se configura varias veces en el mismo modo de ejecución (o combinación de modos de ejecución).

#### Non Compliant Code {#non-compliant-code-osgi}

```+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Compliant Code {#compliant-code-osgi}

```+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Config and Install Folders Should Only Contain OSGi Nodes {#oakpal-config-install}

**Clave**: Configandinstallshouldonlycontainosginodes

**Tipo**: Error

**Gravedad**: Mayor

**Desde**: Versión 2019.6.0

For security reasons, paths containing */config/ and /install/* are only readable by administrative users in AEM and should be used only for OSGi configuration and OSGi bundles. Colocar otros tipos de contenido en rutas que contienen estos segmentos produce un comportamiento de aplicación que varía de forma involuntaria entre los usuarios administrativos y no administrativos.

### Packages Should Not Overlap {#oakpal-no-overlap}

**Clave**: Packageoverlaps

**Tipo**: Error

**Gravedad**: Mayor

**Desde**: Versión 2019.6.0

Similar to the *Packages Should Not Contain Duplicate OSGi Configurations* this is a common problem on complex projects where the same node path is written to by multiple separate content packages. Si bien utilizar dependencias de paquetes de contenido se puede utilizar para garantizar un resultado coherente, es mejor evitar solapamientos por completo.
