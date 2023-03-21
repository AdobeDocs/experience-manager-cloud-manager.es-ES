---
title: Reglas de calidad de código personalizadas
description: Obtenga más información acerca de las reglas de calidad del código personalizadas ejecutadas por Cloud Manager como parte de las pruebas de calidad del código, en función de las prácticas recomendadas de ingeniería de AEM.
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: ef87e13eb81faf5605cdd16c6fd46d5f7b3233a9
workflow-type: tm+mt
source-wordcount: '3531'
ht-degree: 86%

---


# Reglas de calidad de código personalizadas {#custom-code-quality-rules}

Obtenga más información acerca de las reglas de calidad del código personalizadas ejecutadas por Cloud Manager como parte de las [pruebas de calidad del código](/help/using/code-quality-testing.md), en función de las prácticas recomendadas de ingeniería de AEM.

>[!NOTE]
>
>Los ejemplos de código que se proporcionan aquí son solo ilustrativos. Consulte [Documentación de conceptos de SonarQube](https://docs.sonarqube.org/latest/) para conocer sus conceptos y reglas de calidad.

## Reglas de sonarQube {#sonarqube-rules}

La siguiente sección detalla las reglas de SonarQube ejecutadas por Cloud Manager.

### No utilizar funciones potencialmente peligrosas {#do-not-use-potentially-dangerous-functions}

* **Clave**: CQRules: CWE-676
* **Tipo**: Vulnerabilidad
* **Gravedad**: Principal
* **Desde**: Versión 2018.4.0

Los métodos `Thread.stop()` y `Thread.interrupt()` pueden ocasionar problemas difíciles de reproducir y, a veces, vulnerabilidades de seguridad. Su utilización debe ser objeto de un estricto seguimiento y validación. En general, transmitir mensajes es una manera más segura de lograr objetivos similares.

#### Código no compatible {#non-compliant-code}

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

#### Código conforme {#compliant-code}

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

### No usar cadenas de formato que puedan estar controladas externamente {#do-not-use-format-strings-which-may-be-externally-controlled}

* **Clave**: CQRules:CWE-134
* **Tipo**: Vulnerabilidad
* **Gravedad**: Principal
* **Desde**: versión 2018.4.0

El uso de una cadena de formato de una fuente externa (como un parámetro de solicitud o contenido generado por el usuario) puede exponer una aplicación a ataques de denegación de servicio. Hay circunstancias en las que una cadena de formato puede estar controlada externamente, pero solo se permite desde fuentes de confianza.

#### Código no compatible {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### Las solicitudes HTTP siempre deben tener tiempos de espera de conexión y socket {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Clave**: CQRules:ConnectionTimeoutMechanism
* **Tipo**: Error
* **Gravedad**: Crítico
* **Desde**: Versión 2018.6.0

Al ejecutar solicitudes HTTP desde una aplicación de AEM, es fundamental asegurarse de que se han configurado los tiempos de espera adecuados para evitar un consumo innecesario de procesos secundarios. Desafortunadamente, el comportamiento predeterminado de ambos clientes HTTP predeterminados de Java™, `java.net.HttpUrlConnection`, y el cliente de componentes HTTP de Apache que se utiliza con frecuencia nunca agotará el tiempo de espera, por lo que se deben establecer explícitamente los tiempos de espera. Como práctica recomendada, estos tiempos de espera no deben superar los 60 segundos.

#### Código no conforme {#non-compliant-code-2}

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

### Los objetos ResourceResolver siempre deben cerrarse {#resourceresolver-objects-should-always-be-closed}

* **Clave**: CQRules:CQBP-72
* **Tipo**: Code Smell
* **Gravedad**: Principal
* **Desde**: Versión 2018.4.0

Objetos `ResourceResolver` obtenidos de recursos del sistema de consumo `ResourceResolverFactory`. Aunque existen medidas para recuperar estos recursos cuando `ResourceResolver` ya no está en uso, es más eficiente cerrar explícitamente cualquier objeto `ResourceResolver` llamando al método `close()`.

Una idea errónea común es que `ResourceResolver` Los objetos creados con una sesión de JCR existente no deben cerrarse explícitamente o que, al hacerlo, hayan cerrado la sesión de JCR subyacente. No suele ser el caso. Independientemente de cómo se abra `ResourceResolver`, debe cerrarse cuando ya no se utiliza. Dado que `ResourceResolver` implementa la interfaz `Closeable`, también es posible utilizar la sintaxis `try-with-resources` en lugar de invocar explícitamente `close()`.

#### Código no compatible {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### Código compatible {#compliant-code-2}

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

### No utilice las rutas del servlet de Sling para registrar servlets {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Clave**: CQRules:CQBP-75
* **Tipo**: Code Smell
* **Gravedad**: Principal
* **Desde**: Versión 2018.4.0

Como se describe en la sección [Documentación de Sling](https://sling.apache.org/documentation/the-sling-engine/servlets.html), se desaconsejan los servlets de enlace por rutas. Los servlets enlazados a rutas no pueden utilizar controles de acceso JCR estándar y, como resultado, requieren un rigor de seguridad adicional. En lugar de utilizar servlets enlazados a rutas, se recomienda crear nodos en el repositorio y registrar servlets por tipo de recurso.

#### Código no conforme {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Las excepciones capturadas deben registrarse o activarse, no ambas {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **Clave**: CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2018.4.0

En general, una excepción debe registrarse exactamente una vez. El registro de excepciones varias veces puede causar confusión, ya que no está claro cuántas veces se produjo una excepción. El patrón más común que lleva a esto es registrar y arrojar una excepción capturada.

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

#### Código conforme {#compliant-code-3}

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

### Evitar las instrucciones de registro seguidas inmediatamente por las sentencias de lanzamiento {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **Clave**: CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2018.4.0

Otro patrón común que se debe evitar es registrar un mensaje y luego iniciar inmediatamente una excepción. Esto generalmente indica que el mensaje de excepción termina duplicado en los archivos de registro.

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

### Evite iniciar sesión en la información al administrar solicitudes del GET o del HEAD {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Clave**: CQRules:CQBP-44—LogInfoInGetOrHeadRequests
* **Tipo**: Code Smell
* **Gravedad**: Menor

En general, el nivel de registro INFO debe utilizarse para demarcar acciones importantes y, de forma predeterminada, AEM está configurado para registrar a nivel INFO o superior. Los métodos GET y HEAD solo deben ser operaciones de solo lectura y, por lo tanto, no constituyen acciones importantes. Es probable que el registro en el nivel INFO como respuesta a solicitudes de GET o HEAD cree un ruido de registro significativo, lo que dificulta la identificación de información útil en los archivos de registro. El registro al administrar solicitudes de GET o HEAD debe realizarse en los niveles WARN o ERROR cuando algo ha salido mal o en los niveles DEBUG o TRACE si sería útil disponer de información más detallada sobre la solución de problemas.

>[!NOTE]
>
>Esto no se aplica al registro de tipo access.log para cada solicitud.

#### Código no conforme {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### Código compatible {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### No utilice Exception.getMessage() como primer parámetro de un enunciado de registro {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Clave**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2018.4.0

Como práctica recomendada, los mensajes de registro deben proporcionar información contextual sobre dónde se ha producido una excepción en la aplicación. Aunque el contexto también se puede determinar mediante el uso de trazos de pila, en general, el mensaje de registro será más fácil de leer y comprender. Como resultado, al registrar una excepción, es una mala práctica utilizar el mensaje de la excepción como mensaje de registro. El mensaje de excepción contiene lo que ha salido mal, mientras que el mensaje de registro debe utilizarse para indicar a un lector de registro qué estaba haciendo la aplicación cuando se produjo la excepción. El mensaje de excepción se sigue registrando. Al especificar su propio mensaje, los registros son más fáciles de entender.

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

### El inicio de sesión en Bloques de captura debe estar en el nivel WARN o ERROR {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **Clave**: CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2018.4.0

Como sugiere el nombre, las excepciones de Java™ siempre deben usarse en circunstancias excepcionales. Como resultado, cuando se captura una excepción, es importante asegurarse de que los mensajes de registro se registren en el nivel adecuado: ADVERTENCIA o ERROR. Esto garantiza que esos mensajes aparezcan correctamente en los registros.

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

* **Clave**: CQRules:CQBP-44---ExceptionPrintStackTrace
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: versión 2018.4.0

El contexto es fundamental para comprender los mensajes de registro. El uso de `Exception.printStackTrace()` hace que solo el trazo de pila se envíe al flujo de error estándar, lo que provoca que se pierda todo el contexto. Además, en una aplicación multiproceso como AEM si se imprimen varias excepciones utilizando este método en paralelo, sus trazos de pila pueden superponerse, lo que genera una confusión significativa. Las excepciones solo deben registrarse a través del marco de trabajo de registro.

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

#### Código compatible {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### No enviar a salida estándar o error estándar {#do-not-output-to-standard-output-or-standard-error}

* **Clave**: CQRules:CQBP-44—LogLevelConsolePrinters
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: versión 2018.4.0

El registro en AEM siempre se debe realizar a través del marco de trabajo de registro, SLF4J. La salida directa a los flujos de error estándar o de salida estándar pierde la información estructural y contextual proporcionada por el marco de registro y, a veces, puede causar problemas de rendimiento.

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

#### Código compatible {#compliant-code-9}

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

* **Clave**: CQRules:CQBP-71
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: versión 2018.4.0

En general, las rutas que comienzan por `/libs` y `/apps` no deben estar codificadas, ya que las rutas a las que se refieren generalmente se almacenan como rutas relativas a la ruta de búsqueda de Sling (que está configurada en `/libs,/apps` de forma predeterminada). El uso de la ruta absoluta puede introducir defectos sutiles que solo aparecerían más adelante en el ciclo de vida del proyecto.

#### Código no compatible {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### Código conforme {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### El planificador de Sling no debe utilizarse {#sonarqube-sling-scheduler}

* **Clave**: CQRules:AMSCORE-554
* **Tipo**: Compatibilidad de Code Smell/Cloud Service
* **Gravedad**: Menor
* **Desde**: Versión 2020.5.0

El planificador de Sling no debe utilizarse para tareas que requieren una ejecución garantizada. Los trabajos programados de Sling garantizan la ejecución y son más adecuados para los entornos agrupados y no agrupados.

Consulte [Documentación sobre eventos de Apache Sling y gestión de trabajos](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) para obtener más información sobre cómo se gestionan los trabajos de Sling en entornos agrupados.

### Las API en desuso de AEM no deben usarse {#sonarqube-aem-deprecated}

* **Clave**: AMSCORE-553
* **Tipo**: Compatibilidad de Code Smell/Cloud Service
* **Gravedad**: Menor
* **Desde**: Versión 2020.5.0

La superficie de la API de AEM está en constante revisión para identificar las API para las que se desaconseja el uso y que, por lo tanto, se consideran obsoletas.

A menudo, estas API están en desuso al usar el Java™ estándar *@Deprecated* anotación y, como tal, identificada por `squid:CallToDeprecatedMethod`.

Sin embargo, hay casos en los que una API está en desuso en el contexto de AEM, pero puede que no esté en desuso en otros contextos. Esta regla identifica esta segunda clase.

## Reglas de contenido OakPAL {#oakpal-rules}

La siguiente sección detalla las comprobaciones OakPAL ejecutadas por Cloud Manager.

>[!NOTE]
>
>OakPAL es un marco de trabajo, que valida paquetes de contenido usando un repositorio Oak independiente. Fue desarrollado por un socio de AEM y ganador del premio de 2019 AEM Rockstar Norteamérica.

### Los clientes no deben implementar ni ampliar las API de producto anotadas con @ProviderType {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Clave**: CQBP-84
* **Tipo**: Error
* **Gravedad**: Crítico
* **Desde**: Versión 2018.7.0

La API AEM contiene interfaces y clases de Java™ que solo están pensadas para utilizarse, pero no para implementarse, mediante código personalizado. Por ejemplo, la interfaz de `com.day.cq.wcm.api.Page` solo lo implementa AEM.

Cuando se agregan nuevos métodos a estas interfaces, esos métodos adicionales no afectan al código existente que utiliza estas interfaces y, como resultado, la adición de nuevos métodos a estas interfaces se considera compatible con versiones anteriores. Sin embargo, si el código personalizado implementa una de estas interfaces, dicho código personalizado ha introducido un riesgo de compatibilidad con versiones anteriores para el cliente.

Las interfaces y clases que solo se pretende implementar mediante AEM se anotan con `org.osgi.annotation.versioning.ProviderType` o, a veces, una anotación heredada similar `aQute.bnd.annotation.ProviderType`. Esta regla identifica los casos en los que se implementa una interfaz de este tipo o en los que una clase se amplía mediante código personalizado.

#### Código no conforme {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Los paquetes de clientes no deben crear ni modificar nodos en /libs {#oakpal-customer-package}

* **Clave**: BannedPath
* **Tipo**: error
* **Gravedad**: bloqueador
* **Desde**: versión 2019.6.0

Una práctica recomendada clásica es que el árbol de contenido `/libs` en el repositorio de contenido de AEM debe ser considerado de solo lectura por los clientes. Modificar nodos y propiedades en `/libs` crea un riesgo significativo para las actualizaciones principales y secundarias. Modificaciones a `/libs` sólo se realiza por Adobe a través de canales oficiales.

### Los paquetes no deben contener configuraciones OSGi duplicadas {#oakpal-package-osgi}

* **Clave**: DuplicateOsgiConfigurations
* **Tipo**: Error
* **Gravedad**: Principal
* **Desde**: Versión 2019.6.0

Un problema común que ocurre en proyectos complejos es que el mismo componente OSGi se configura varias veces. Esto crea una ambigüedad sobre qué configuración es operable. Esta regla es &quot;según el modo de ejecución&quot; ya que solo identificará problemas en los que el mismo componente se haya configurado varias veces en el mismo modo de ejecución o combinación de modos de ejecución.

#### Código no compatible {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Código compatible {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Las carpetas de configuración e instalación solo deben contener nodos OSGi {#oakpal-config-install}

* **Clave**: ConfigAndInstallShouldOnlyContainOsgiNodes
* **Tipo**: Error
* **Gravedad**: Principal
* **Desde**: Versión 2019.6.0

Por motivos de seguridad, las rutas que contienen `/config/` y `/install/` solo pueden leerlas los usuarios administrativos en AEM y solo deben utilizarse para la configuración OSGi y los paquetes OSGi. Colocar otros tipos de contenido en rutas que contienen estos segmentos resulta en un comportamiento de la aplicación que varía involuntariamente entre usuarios administrativos y no administrativos.

Un problema común es el uso de nodos llamados `config` en los cuadros de diálogo de componentes o al especificar la configuración del editor de texto enriquecido para la edición en línea. Para resolver esto, se debe cambiar el nombre del nodo infractor por uno conforme. Para la configuración del editor de texto enriquecido, utilice la propiedad `configPath` en el nodo `cq:inplaceEditing` para especificar la nueva ubicación.

#### Código no compatible {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Código compatible {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### Los paquetes no deben superponerse {#oakpal-no-overlap}

* **Clave**: PackageOverlaps
* **Tipo**: Error
* **Gravedad**: Principal
* **Desde**: versión 2019.6.0

Similar a la regla [Los paquetes no deben contener configuraciones OSGi duplicadas,](#oakpal-package-osgi) este es un problema frecuente en proyectos complejos en los que varios paquetes de contenido independientes escriben la misma ruta de acceso de nodo. Aunque las dependencias de paquetes de contenido se pueden utilizar para garantizar un resultado coherente, es mejor evitar superposiciones por completo.

### El modo de creación predeterminado no debe ser la IU clásica {#oakpal-default-authoring}

* **Clave**: ClassicUIAuthoringMode
* **Tipo**: Compatibilidad de Code Smell/Cloud Service
* **Gravedad**: Menor
* **Desde**: Versión 2020.5.0

La configuración OSGi `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` define el modo de creación predeterminado en AEM. Dado que la IU clásica ha quedado obsoleta desde AEM 6.4, ahora se plantea un problema cuando el modo de creación predeterminado se configura en la IU clásica.

### Los componentes con cuadros de diálogo deben tener cuadros de diálogo de IU táctil {#oakpal-components-dialogs}

* **Clave**: ComponentWithOnlyClassicUIDialog
* **Tipo**: Compatibilidad de Code Smell/Cloud Service
* **Gravedad**: Menor
* **Desde**: versión 2020.5.0

Los componentes de AEM que tienen un cuadro de diálogo de interfaz de usuario clásica siempre deben tener un cuadro de diálogo de IU táctil correspondiente, tanto para proporcionar una experiencia de creación óptima como para ser compatibles con el modelo de implementación de Cloud Service, donde la interfaz de usuario clásica no es compatible. Esta regla verifica los siguientes escenarios:

* Un componente con un cuadro de diálogo de IU clásica (es decir, un nodo `dialog` secundario) debe tener un cuadro de diálogo correspondiente de la interfaz de usuario táctil (es decir, un nodo `cq:dialog` secundario).
* Un componente con un cuadro de diálogo de diseño de IU clásica (es decir, un nodo `design_dialog`) debe tener un cuadro de diálogo de diseño de la interfaz de usuario táctil correspondiente (es decir, un nodo `cq:design_dialog` secundario).
* Un componente con un cuadro de diálogo de IU clásica y un cuadro de diálogo de diseño de IU clásica debe tener un cuadro de diálogo de IU táctil correspondiente y un cuadro de diálogo de diseño de IU táctil correspondiente.

La documentación de Herramientas de modernización AEM proporciona información y herramientas sobre cómo convertir componentes de la IU clásica a la IU táctil. Consulte [la documentación de Herramientas de modernización AEM](https://opensource.adobe.com/aem-modernize-tools/) para obtener más información.

### Los paquetes no deben mezclar contenido mutable e inmutable {#oakpal-packages-immutable}

* **Clave**: ImmutableMutableMixedPackage
* **Tipo**: Compatibilidad de Code Smell/Cloud Service
* **Gravedad**: Menor
* **Desde**: Versión 2020.5.0

Para ser compatible con el modelo de implementación del Cloud Service, los paquetes de contenido individuales deben contener contenido para las áreas inmutables del repositorio (es decir, `/apps` y `/libs`) o el área mutable (es decir, todo lo que no está en `/apps` o `/libs`), pero no ambas. Por ejemplo, un paquete que incluye ambos `/apps/myco/components/text and /etc/clientlibs/myco` no es compatible con Cloud Service y provoca que se informe de un problema.

Consulte [Documentación de la estructura del proyecto AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=es) para obtener más información.

>[!NOTE]
>
>La regla [Los paquetes de cliente no deben crear ni modificar nodos en /libs](#oakpal-customer-package) siempre se aplica.

### No se deben utilizar agentes de replicación inversa {#oakpal-reverse-replication}

* **Clave**: ReverseReplication
* **Tipo**: Compatibilidad de Code Smell/Cloud Service
* **Gravedad**: Menor
* **Desde**: versión 2020.5.0

La compatibilidad con la replicación inversa no está disponible en las implementaciones de Cloud Service, como se describe en [Notas de la versión: Eliminación de agentes de replicación.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html?lang=es#replication-agents)

Los clientes que utilicen la replicación inversa deben ponerse en contacto con Adobe para obtener soluciones alternativas.

### Los recursos contenidos en las bibliotecas cliente habilitadas para proxy deben estar en una carpeta denominada Recursos {#oakpal-resources-proxy}

* **Clave**: ClientlibProxyResource
* **Tipo**: Error
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

Las bibliotecas de cliente de AEM pueden contener recursos estáticos como imágenes y fuentes. Como se describe en el [Uso de la documentación de las bibliotecas del lado cliente,](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=es#using-preprocessors) cuando se utilizan bibliotecas cliente proxy, estos recursos estáticos deben estar contenidos en una carpeta secundaria denominada `resources` para que se haga referencia de forma efectiva en las instancias de publicación.

#### Código no compatible {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### Código compatible {#compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### Uso de procesos de flujo de trabajo incompatibles con Cloud Service {#oakpal-usage-cloud-service}

* **Clave**: CloudServiceIncompatibleWorkflowProcess
* **Tipo**: hueco de código
* **Gravedad**: bloqueador
* **Desde**: versión 2021.2.0

Con el cambio a los microservicios de activos para el procesamiento de activos en AEM Cloud Service, varios procesos de flujo de trabajo que se utilizaban en versiones On-Premise y de AMS de AEM han dejado de ser compatibles o son innecesarios.

La herramienta de migración en el [Repositorio de GitHub de AEM Assets as a Cloud Service](https://github.com/adobe/aem-cloud-migration) se puede utilizar para actualizar modelos de flujo de trabajo durante la migración a AEM as a Cloud Service.

### Se desaconseja el uso de plantillas estáticas en favor de plantillas editables {#oakpal-static-template}

* **Clave**: StaticTemplateUsage
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

Aunque históricamente el uso de plantillas estáticas ha sido común en AEM proyectos, se recomiendan las plantillas editables, ya que proporcionan la mayor flexibilidad y admiten funciones adicionales que no están presentes en plantillas estáticas. Encontrará más información en el documento [Plantillas de página: editables.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/templates/page-templates-editable.html?lang=es)

La migración de plantillas estáticas a editables se puede automatizar en gran medida mediante las [Herramientas de modernización de AEM.](https://opensource.adobe.com/aem-modernize-tools/)

### Se desaconseja el uso de componentes de base heredados {#oakpal-usage-legacy}

* **Clave**: LegacyFoundationComponentUsage
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: versión 2021.2.0

Los componentes básicos heredados (es decir, los componentes en `/libs/foundation`) llevan en desuso varias versiones de AEM a favor de los [Componentes principales.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=es) Se desaconseja el uso de los componentes básicos heredados como base para los componentes personalizados, ya sea por superposición o herencia, y deben convertirse al componente principal correspondiente.

Esta conversión puede facilitarse mediante las [Herramientas de modernización de AEM.](https://opensource.adobe.com/aem-modernize-tools/)

### Solo se deben utilizar los nombres y el orden de los modos de ejecución admitidos {#oakpal-supported-runmodes}

* **Clave**: SupportedRunmode
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

AEM Cloud Service aplica una política de nomenclatura estricta para los nombres de modo de ejecución y un orden estricto para dichos modos de ejecución. La lista de modos de ejecución admitidos se encuentra en la [Implementación en AEM documentación as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=es#runmodes) y cualquier desviación de esto se identifica como un problema.

### Los nodos de definición del índice de búsqueda personalizada deben ser secundarios directos de /oak:index {#oakpal-custom-search}

* **Clave**: OakIndexLocation
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: versión 2021.2.0

AEM Cloud Service requiere que las definiciones de índice de búsqueda personalizadas (es decir, nodos de tipo `oak:QueryIndexDefinition`) sean nodos secundarios directos de `/oak:index`. Los índices de otras ubicaciones deben moverse para que sean compatibles con AEM Cloud Service. Puede encontrar más información sobre los índices de búsqueda en la [documentación de búsqueda de contenido e indexación.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=es)

### Los nodos de definición de índice de búsqueda personalizada deben tener una compatVersion de 2 {#oakpal-custom-search-compatVersion}

* **Clave**: IndexCompatVersion
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: versión 2021.2.0

AEM Cloud Service requiere que las definiciones de índice de búsqueda personalizadas (es decir, nodos de tipo `oak:QueryIndexDefinition`) tengan la propiedad `compatVersion` establecida en `2`. AEM Cloud Service no admite ningún otro valor. Puede encontrar más información sobre los índices de búsqueda en la [documentación de búsqueda de contenido e indexación.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=es)

### Los nodos descendientes de los nodos de definición de índice de búsqueda personalizada deben ser del tipo nt:unstructured {#oakpal-descendent-nodes}

* **Clave**: IndexDescendantNodeType
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

Se pueden producir problemas difíciles de solucionar cuando un nodo de definición de índice de búsqueda personalizado tiene nodos secundarios sin ordenar. Para evitarlos, se recomienda que todos los nodos descendientes de un nodo `oak:QueryIndexDefinition` sean de tipo `nt:unstructured`.

### Los nodos de definición de índice de búsqueda personalizada deben contener un nodo secundario denominado indexRules que tenga nodos secundarios. {#oakpal-custom-search-index}

* **Clave**: IndexRulesNode
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: versión 2021.2.0

Un nodo de definición de índice de búsqueda personalizada definido correctamente debe contener un nodo secundario denominado `indexRules` que, a su vez, debe tener al menos un secundario. Puede encontrar más información en la [documentación de Oak.](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

### Los nodos de definición del índice de búsqueda personalizada deben seguir las convenciones de nombres {#oakpal-custom-search-definitions}

* **Clave**: IndexName
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: versión 2021.2.0

AEM Cloud Service requiere que las definiciones de índice de búsqueda personalizadas (es decir, nodos de tipo `oak:QueryIndexDefinition`) tengan un nombre que siga un patrón específico descrito en [Búsqueda e indexación de contenido.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=es#how-to-use)

### Los nodos de definición de índice de búsqueda personalizada deben utilizar el tipo de índice Lucene  {#oakpal-index-type-lucene}

* **Clave**: IndexType
* **Tipo**: hueco de código
* **Gravedad**: Menor
* **Desde**: versión 2021.2.0

AEM Cloud Service requiere que las definiciones de índice de búsqueda personalizadas (es decir, nodos de tipo `oak:QueryIndexDefinition`) tengan la propiedad `type` con el valor establecido en `lucene`. La indexación mediante tipos de índice heredados debe actualizarse antes de la migración a AEM Cloud Service. Consulte la [Documentación de búsqueda de contenido e indexación](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=es#how-to-use) para obtener más información.

### Los nodos de definición de índice de búsqueda personalizada no deben contener una propiedad denominada Semilla {#oakpal-property-name-seed}

* **Clave**: IndexSeedProperty
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: versión 2021.2.0

AEM Cloud Service prohíbe que las definiciones de índice de búsqueda personalizadas (es decir, los nodos de tipo `oak:QueryIndexDefinition`) contengan una propiedad denominada `seed`. La indexación que utiliza esta propiedad debe actualizarse antes de la migración a AEM Cloud Service. Consulte la [Documentación de búsqueda de contenido e indexación](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=es#how-to-use) para obtener más información.

### Los nodos de definición de índice de búsqueda personalizada no deben contener una propiedad denominada “reindex” {#oakpal-reindex-property}

* **Clave**: IndexReindexProperty
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: versión 2021.2.0

AEM Cloud Service prohíbe que las definiciones de índice de búsqueda personalizadas (es decir, los nodos de tipo `oak:QueryIndexDefinition`) contengan una propiedad denominada `reindex`. La indexación que utiliza esta propiedad debe actualizarse antes de la migración a AEM Cloud Service. Consulte la [Documentación de búsqueda de contenido e indexación](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=es#how-to-use) para obtener más información.

## Herramienta de optimización de Dispatcher {#dispatcher-optimization-tool-rules}

En la sección siguiente se enumeran las comprobaciones de la Herramienta de optimización de Dispatcher (DOT) ejecutadas por Cloud Manager. Siga los vínculos para cada comprobación de su definición y detalles de GitHub.

* [Tokens inesperados de configuración de Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [Presupuesto no coincidente de configuración de Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [Falta la llave de configuración de Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [Llave adicional de configuración de Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Falta la propiedad obligatoria de configuración de Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Propiedad Configuración de Dispatcher obsoleta](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [Configuración de Dispatcher no encontrada](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [Archivo de inclusión de configuración Httpd no encontrado](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Configuración general de Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [La caché del conjunto de servidores de publicación de Dispatcher debe tener activado serveStaleOnError](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [Los filtros de conjunto de servidores de publicación de Dispatcher deben contener las reglas de denegación predeterminadas de la versión 6.x.x del arquetipo de AEM](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [La propiedad statfileslevel de caché de conjunto de servidores de publicación de Dispatcher debe ser >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [La propiedad gracePeriod de conjunto de servidores de publicación de Dispatcher debe ser >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [Cada conjunto de servidores de Dispatcher debe tener un nombre único](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [La caché de la granja de servidores de publicación de Dispatcher debe tener las reglas ignoreUrlParams configuradas de forma lista de permitidos](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [Los filtros de granja de publicación de Dispatcher deben especificar los selectores de Sling permitidos de forma lista de permitidos](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [Los filtros de granja de publicación de Dispatcher deben especificar los patrones de sufijo de Sling permitidos de forma lista de permitidos](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [No utilice la directiva &quot;Requerir todo concedido&quot; en una sección de Directorio VirtualHost con una ruta de directorio raíz](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
