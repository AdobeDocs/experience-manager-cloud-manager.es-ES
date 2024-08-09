---
title: Reglas de calidad de código personalizadas
description: Descubra los detalles específicos de las reglas de calidad de código personalizadas ejecutadas por Cloud Manager durante las pruebas de calidad del código. Estas reglas se basan en las prácticas recomendadas de AEM Engineering.
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '3482'
ht-degree: 93%

---


# Reglas de calidad del código personalizadas {#custom-code-quality-rules}

Obtenga más información acerca de las reglas de calidad del código personalizadas ejecutadas por Cloud Manager AEM como parte de [pruebas de calidad del código](/help/using/code-quality-testing.md), según las prácticas recomendadas de ingeniería de.

>[!NOTE]
>
>Los ejemplos de código que se proporcionan aquí son solo ilustrativos. Consulte la [documentación de conceptos de SonarQube](https://docs.sonarsource.com/sonarqube/latest/) para obtener información sobre los conceptos y las reglas de calidad.

>[!NOTE]
>
>Las reglas completas de SonarQube no están disponibles para su descarga debido a la información de Adobe registrada. Puede descargar la lista completa de reglas [mediante este vínculo](/help/assets/CodeQuality-rules-latest-AMS.xlsx). Continúe leyendo este documento para obtener descripciones y ejemplos de las reglas.

## Reglas de SonarQube {#sonarqube-rules}

La siguiente sección detalla las reglas de SonarQube ejecutadas por Cloud Manager.

### No utilizar funciones potencialmente peligrosas {#do-not-use-potentially-dangerous-functions}

* **Clave**: CQRules: CWE-676
* **Tipo**: Vulnerabilidad
* **Gravedad**: Principal
* **Desde**: Versión 2018.4.0

Los métodos `Thread.stop()` y `Thread.interrupt()` pueden ocasionar problemas difíciles de reproducir y, a veces, vulnerabilidades de seguridad. Su utilización debe ser objeto de un estricto seguimiento y validación. En general, transmitir mensajes es una manera más segura de lograr objetivos similares.

#### Código no conforme {#non-compliant-code}

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

* **Clave**: CQRules: CWE-134
* **Tipo**: Vulnerabilidad
* **Gravedad**: Principal
* **Desde**: Versión 2018.4.0

El uso de una cadena de formato de una fuente externa (como un parámetro de solicitud o contenido generado por el usuario) puede exponer una aplicación a ataques de denegación de servicio. Hay circunstancias en las que una cadena de formato puede estar controlada externamente, pero solo se permite desde fuentes de confianza.

#### Código no conforme {#non-compliant-code-1}

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

Al ejecutar solicitudes HTTP desde una aplicación de AEM, es esencial que se hayan configurado los tiempos de espera adecuados para evitar un consumo de hilos innecesario. Lamentablemente, tanto el cliente HTTP predeterminado de Java™, `java.net.HttpUrlConnection`, como el cliente de componentes HTTP de Apache que se utiliza con frecuencia no tienen un tiempo de espera predeterminado. Por lo tanto, los tiempos de espera deben configurarse explícitamente. Como práctica recomendada, estos tiempos de espera no deben superar los 60 segundos.

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

#### Código conforme {#compliant-code-1}

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

### Los objetos `ResourceResolver` siempre deben cerrarse {#resourceresolver-objects-should-always-be-closed}

* **Clave**: CQRules:CQBP-72
* **Tipo**: Code Smell
* **Gravedad**: Principal
* **Desde**: Versión 2018.4.0

`ResourceResolver` Los objetos obtenidos de `ResourceResolverFactory` consumen recursos del sistema. Aunque existen medidas para recuperar estos recursos cuando un objeto `ResourceResolver` ya no está en uso, es más eficaz cerrar explícitamente cualquier objeto `ResourceResolver` abierto invocando la función método `close()`.

Una idea errónea frecuente es que los objetos `ResourceResolver` creados con una sesión de JCR existente no deben cerrarse explícitamente. Otra idea errónea es que al cerrar estos objetos, se cierra la sesión de JCR subyacente. No suele ser el caso. Independientemente de cómo se abra `ResourceResolver`, debe cerrarse cuando ya no se utiliza. Dado que `ResourceResolver` implementa la interfaz `Closeable`, también es posible utilizar la sintaxis `try-with-resources` en lugar de invocar explícitamente `close()`.

#### Código no conforme {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### Código conforme {#compliant-code-2}

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

### No utilizar las rutas del servlet de Sling para registrar servlets {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Clave**: CQRules:CQBP-75
* **Tipo**: Code Smell
* **Gravedad**: Principal
* **Desde**: Versión 2018.4.0

Como se describe en la [Documentación de Sling](https://sling.apache.org/documentation/the-sling-engine/servlets.html), se desaconseja enlazar los servlets por rutas. Los servlets enlazados a rutas no pueden utilizar controles de acceso JCR estándar y, como resultado, requieren un rigor de seguridad adicional. En lugar de utilizar servlets enlazados a rutas, se recomienda crear nodos en el repositorio y registrar servlets por tipo de recurso.

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

En general, una excepción debe registrarse exactamente una vez. El registro de excepciones varias veces puede causar confusión porque no está claro cuántas veces se produjo una excepción. El patrón más común que lleva a este problema es registrar y arrojar una excepción capturada.

#### Código no conforme {#non-compliant-code-6}

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

Otro patrón común que se debe evitar es registrar un mensaje y luego iniciar inmediatamente una excepción. Este problema generalmente indica que el mensaje de excepción termina duplicado en los archivos de registro.

#### Código no conforme {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### Código conforme {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### Evitar iniciar sesión en la información al gestionar solicitudes GET o HEAD {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Clave**: CQRules:CQBP-44—LogInfoInGetOrHeadRequests
* **Tipo**: Code Smell
* **Gravedad**: Menor

En general, el nivel de registro INFO debe utilizarse para demarcar acciones importantes y, de forma predeterminada, AEM está configurado para registrar a nivel INFO o superior. Los métodos GET y HEAD solo deben ser operaciones de solo lectura y, por lo tanto, no constituyen acciones importantes. Es probable que el registro en el nivel INFO como respuesta a solicitudes de GET o HEAD cree un ruido de registro significativo, lo que dificulta la identificación de información útil en los archivos de registro. Al administrar solicitudes de GET o HEAD, el registro debe realizarse en los niveles ADVERTENCIA o ERROR si algo ha salido mal. Para obtener información más detallada sobre la solución de problemas, el registro debe realizarse en los niveles DEPURACIÓN o TRACE.

>[!NOTE]
>
>Este flujo de trabajo no se aplica al registro de access.log-type para cada solicitud.

#### Código no conforme {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### Código conforme {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### No usar `Exception.getMessage()` como primer parámetro de un enunciado de registro {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Clave**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2018.4.0

Como práctica recomendada, los mensajes de registro deben proporcionar información contextual sobre dónde se ha producido una excepción en la aplicación. Aunque el contexto también se puede determinar mediante el uso de trazos de pila, en general, el mensaje de registro será más fácil de leer y comprender. Como resultado, al registrar una excepción, es una mala práctica utilizar el mensaje de la excepción como mensaje de registro. El mensaje de excepción debe detallar qué ha fallado. Por su parte, el mensaje de registro debe informar al lector sobre lo que la aplicación estaba haciendo cuando se produjo la excepción. El mensaje de excepción se sigue registrando. Al especificar su propio mensaje, los registros son más fáciles de entender.

#### Código no conforme {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### Código conforme {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### El registro en bloques de captura debe estar en el nivel WARN o ERROR {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **Clave**: CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2018.4.0

Como sugiere el nombre, las excepciones de Java™ siempre deben usarse en circunstancias excepcionales. Como resultado, cuando se captura una excepción, es importante asegurarse de que los mensajes de registro se registren en el nivel adecuado: ADVERTENCIA o ERROR. Esto garantiza que esos mensajes aparezcan correctamente en los registros.

#### Código no conforme {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### Código conforme {#compliant-code-7}

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
* **Desde**: Versión 2018.4.0

El contexto es fundamental para comprender los mensajes de registro. El uso de `Exception.printStackTrace()` hace que solo el trazo de pila se envíe al flujo de error estándar, lo que provoca que se pierda todo el contexto. Además, en una aplicación multiproceso como AEM, si se imprimen varias excepciones utilizando este método en paralelo, sus trazos de pila pueden superponerse, lo que genera una confusión significativa. Las excepciones solo deben registrarse en el marco de registro.

#### Código no conforme {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### Código conforme {#compliant-code-8}

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
* **Desde**: Versión 2018.4.0

El registro en AEM siempre se debe realizar a través del marco de trabajo de registro, SLF4J. La salida directa a los flujos de error estándar o de salida estándar pierde la información estructural y contextual proporcionada por el marco de trabajo de registro y, a veces, puede causar problemas de rendimiento.

#### Código no conforme {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### Código conforme {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Evitar las rutas `/apps` y `/libs` codificadas {#avoid-hardcoded-apps-and-libs-paths}

* **Clave**: CQRules:CQBP-71
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2018.4.0

Las rutas que comienzan por `/libs` y `/apps` generalmente no deberían estar codificadas. Estas rutas se suelen almacenar en relación con la ruta de búsqueda de Sling, que tiene el valor predeterminado `/libs,/apps`. El uso de la ruta absoluta puede introducir defectos sutiles que solo aparecerían más adelante en el ciclo de vida del proyecto.

#### Código no conforme {#non-compliant-code-13}

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

### El planificador de Sling no debe usarse {#sonarqube-sling-scheduler}

* **Clave**: CQRules:AMSCORE-554
* **Tipo**: compatibilidad de Code Smell / Cloud Service
* **Gravedad**: Menor
* **Desde**: Versión 2020.5.0

El planificador de Sling no debe utilizarse para tareas que requieren una ejecución garantizada. Los trabajos programados de Sling garantizan la ejecución y son más adecuados para los entornos agrupados y no agrupados.

Consulte [Documentación sobre eventos de Apache Sling y administración de trabajos](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) para obtener más información sobre cómo se administran los trabajos de Sling en entornos agrupados.

### Las API en desuso de AEM no deben usarse {#sonarqube-aem-deprecated}

* **Clave**: AMSCORE-553
* **Tipo**: compatibilidad de Code Smell / Cloud Service
* **Gravedad**: Menor
* **Desde**: Versión 2020.5.0

La superficie de la API de AEM está en constante revisión para identificar las API para las que se desaconseja el uso y que, por lo tanto, se consideran obsoletas.

A menudo, estas API están en desuso al utilizar la anotación *@Deprecated* de Java™ estándar y, como tal, identificada por `squid:CallToDeprecatedMethod`.

Sin embargo, hay casos en los que una API está en desuso en el contexto de AEM, pero puede que no esté en desuso en otros contextos. Esta regla identifica esta segunda clase.

## Reglas de contenido OakPAL {#oakpal-rules}

La siguiente sección detalla las comprobaciones OakPAL ejecutadas por Cloud Manager.

>[!NOTE]
>
>OakPAL es un marco de trabajo, que valida paquetes de contenido usando un repositorio Oak independiente. Fue desarrollado por un socio de AEM, ganador del premio de 2019 AEM Rockstar Norteamérica.

### Los clientes no deben implementar ni ampliar las API de producto anotadas con @ProviderType {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Clave**: CQBP-84
* **Tipo**: Error
* **Gravedad**: Crítico
* **Desde**: Versión 2018.7.0

La API de AEM contiene interfaces y clases de Java™ que solo están pensadas para utilizarse mediante código personalizado, pero no para implementarse. Por ejemplo, solo AEM implementa la interfaz `com.day.cq.wcm.api.Page`.

La adición de nuevos métodos a estas interfaces no afecta al código existente, por lo que la adición de nuevos métodos es compatible con versiones anteriores. Sin embargo, si el código personalizado implementa una de estas interfaces, dicho código personalizado ha introducido un riesgo de compatibilidad con versiones anteriores para el cliente.

AEM anota interfaces y clases destinadas únicamente a su implementación con `org.osgi.annotation.versioning.ProviderType` o, en ocasiones, la anotación heredada `aQute.bnd.annotation.ProviderType`. Esta regla detecta las instancias en las que el código personalizado implementa una interfaz de este tipo o amplía una clase.

#### Código no conforme {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Los paquetes de clientes no deben crear ni editar nodos en `/libs` {#oakpal-customer-package}

* **Clave**: BannedPath
* **Tipo**: Error
* **Gravedad**: bloqueador
* **Desde**: Versión 2019.6.0

Una práctica recomendada clásica es que el árbol de contenido `/libs` en el repositorio de contenido de AEM debe ser considerado de solo lectura por los clientes. Modificar nodos y propiedades en `/libs` crea un riesgo significativo para las actualizaciones principales y secundarias. Adobe solo debe realizar las ediciones en `/libs` a través de canales oficiales.

### Los paquetes no deben contener configuraciones OSGi duplicadas {#oakpal-package-osgi}

* **Clave**: DuplicateOsgiConfigurations
* **Tipo**: Error
* **Gravedad**: Principal
* **Desde**: Versión 2019.6.0

Un problema frecuente que ocurre en proyectos complejos es que el propio componente OSGi se configura varias veces. Este problema crea ambigüedad sobre la configuración que se puede utilizar. Esta regla es “según el modo de ejecución”, ya que solo identifica problemas en los que el mismo componente se haya configurado varias veces en el mismo modo de ejecución o combinación de modos de ejecución.

#### Código no conforme {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Código conforme {#compliant-code-osgi}

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

Por motivos de seguridad, las rutas que contienen `/config/` y `/install/` solo pueden leerlas los usuarios administrativos en AEM y solo deben utilizarse para la configuración OSGi y los paquetes OSGi. Al colocar otros tipos de contenido en rutas que contienen estos segmentos, se produce un comportamiento de la aplicación que varía involuntariamente entre usuarios administrativos y no administrativos.

Un problema frecuente es el uso de nodos denominados `config` en cuadros de diálogo de componentes o al especificar la configuración del editor de texto enriquecido para la edición en línea. Para resolver este problema, se debe cambiar el nombre del nodo infractor por uno conforme. Para la configuración del editor de texto enriquecido, utilice la propiedad `configPath` en el nodo `cq:inplaceEditing` para especificar la nueva ubicación.

#### Código no conforme {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Código conforme {#compliant-code-config-install}

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
* **Desde**: Versión 2019.6.0

Similar a la regla [Los paquetes no deben contener configuraciones OSGi duplicadas](#oakpal-package-osgi), este es un problema frecuente en proyectos complejos en los que varios paquetes de contenido independientes escriben la misma ruta de acceso de nodo. Aunque el uso de dependencias de paquetes de contenido se puede utilizar para garantizar un resultado coherente, es mejor evitar las superposiciones por completo.

### El modo de creación predeterminado no debe ser la IU clásica {#oakpal-default-authoring}

* **Clave**: ClassicUIAuthoringMode
* **Tipo**: compatibilidad de Code Smell / Cloud Service
* **Gravedad**: Menor
* **Desde**: Versión 2020.5.0

La configuración OSGi `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` define el modo de creación predeterminado en AEM. Dado que la IU clásica ha quedado obsoleta desde AEM 6.4, ahora se generará un problema cuando el modo de creación predeterminado esté configurado en la IU clásica.

### Los componentes con cuadros de diálogo deben tener cuadros de diálogo de IU táctil {#oakpal-components-dialogs}

* **Clave**: ComponentWithOnlyClassicUIDialog
* **Tipo**: compatibilidad de Code Smell / Cloud Service
* **Gravedad**: Menor
* **Desde**: Versión 2020.5.0

Los componentes de AEM que tienen un cuadro de diálogo de interfaz de usuario clásica también deben tener un cuadro de diálogo de IU táctil para proporcionar una experiencia de creación óptima y compatibilidad con el modelo de implementación de Cloud Service, el cual no es compatible con la interfaz de usuario clásica. Esta regla verifica los siguientes escenarios:

* Un componente con un cuadro de diálogo de IU clásica (es decir, un nodo `dialog` secundario) debe tener un cuadro de diálogo correspondiente de la interfaz de usuario táctil (es decir, un nodo `cq:dialog` secundario).
* Un componente con un cuadro de diálogo de diseño de IU clásica (es decir, un nodo `design_dialog`) debe tener un cuadro de diálogo de diseño de IU táctil correspondiente (es decir, un nodo secundario `cq:design_dialog`).
* Un componente con un cuadro de diálogo y de diseño de IU clásica debe tener un cuadro de diálogo de IU táctil y un cuadro de diálogo de diseño de IU táctil correspondiente.

La documentación de Herramientas de modernización AEM proporciona información y herramientas sobre cómo convertir componentes de la IU clásica a la IU táctil. Consulte la [documentación de Herramientas de modernización de AEM](https://opensource.adobe.com/aem-modernize-tools/) para obtener más información.

### No se deben utilizar agentes de replicación inversa {#oakpal-reverse-replication}

* **Clave**: ReverseReplication
* **Tipo**: compatibilidad de Code Smell / Cloud Service
* **Gravedad**: Menor
* **Desde**: Versión 2020.5.0

La compatibilidad con la replicación inversa no está disponible en las implementaciones de Cloud Service, como se describe en [Notas de la versión: eliminación de agentes de replicación](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes#replication-agents).

Los clientes que utilizan la replicación inversa deben ponerse en contacto con Adobe para obtener soluciones alternativas.

### Los recursos contenidos en las bibliotecas cliente habilitadas para proxy deben estar en una carpeta denominada Recursos {#oakpal-resources-proxy}

* **Clave**: ClientlibProxyResource
* **Tipo**: Error
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

Las bibliotecas cliente de AEM pueden contener recursos estáticos como imágenes y fuentes. Como se describe en [Uso de la documentación de las bibliotecas del cliente](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/implementing/developing/introduction/clientlibs#using-preprocessors), cuando se usan bibliotecas cliente proxy, estos recursos estáticos deben estar contenidos en una carpeta secundaria llamada `resources` para que se haga referencia de forma efectiva en las instancias de publicación.

#### Código no conforme {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### Código conforme {#compliant-proxy-enabled}

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
* **Tipo**: Code Smell
* **Gravedad**: bloqueador
* **Desde**: Versión 2021.2.0

Con el cambio a los microservicios de activos para el procesamiento de activos en AEM Cloud Service, varios procesos de flujo de trabajo que se utilizaban en versiones On-Premise y de AMS de AEM han dejado de ser compatibles o son innecesarios.

La herramienta de migración de [Repositorio de GitHub de AEM Assets as a Cloud Service](https://github.com/adobe/aem-cloud-migration) se puede utilizar para actualizar los modelos de flujo de trabajo durante la migración a AEM as a Cloud Service.

### No se recomienda el uso de plantillas estáticas en lugar de plantillas editables {#oakpal-static-template}

* **Clave**: StaticTemplateUsage
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

Si bien el uso de plantillas estáticas siempre ha sido común, históricamente, en Proyectos AEM, se recomienda encarecidamente el uso de plantillas editables, ya que proporcionan la mayor flexibilidad y admiten funciones adicionales que no están presentes en las plantillas estáticas. Encontrará más información en [Plantillas de página - Documentación editable](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/implementing/developing/platform/templates/page-templates-editable).

AEM La migración de plantillas estáticas a editables se puede automatizar en gran medida mediante las [Herramientas de modernización de la](https://opensource.adobe.com/aem-modernize-tools/).

### Se desaconseja el uso de componentes de base heredados {#oakpal-usage-legacy}

* **Clave**: LegacyFoundationComponentUsage
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

AEM Los componentes básicos heredados (es decir, los componentes de `/libs/foundation`) han quedado obsoletos durante varias versiones a favor de los [componentes principales](https://experienceleague.adobe.com/es/docs/experience-manager-core-components/using/introduction). Se desaconseja el uso de los componentes básicos heredados como base para los componentes personalizados, ya sea por superposición o herencia, y deben convertirse al componente principal correspondiente.

[Las herramientas de modernización de AEM](https://opensource.adobe.com/aem-modernize-tools/) pueden facilitar esta conversión.

### Los nodos de definición de índice de búsqueda personalizada deben ser tareas secundarias directas de `/oak:index` {#oakpal-custom-search}

* **Clave**: OakIndexLocation
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

AEM Cloud Service requiere que las definiciones de índice de búsqueda personalizadas (es decir, nodos de tipo `oak:QueryIndexDefinition`) sean nodos secundarios directos de `/oak:index`. Los índices de otras ubicaciones deben moverse para que sean compatibles con AEM Cloud Service. Encontrará más información sobre los índices de búsqueda en la [Documentación sobre búsqueda de contenido e indexación](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/operations/indexing).

### Los nodos de definición de índice de búsqueda personalizada deben tener una compatVersion de 2 {#oakpal-custom-search-compatVersion}

* **Clave**: IndexCompatVersion
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

AEM Cloud Service requiere que las definiciones de índice de búsqueda personalizadas (es decir, nodos de tipo `oak:QueryIndexDefinition`) tengan la propiedad `compatVersion` establecida en `2`. AEM Cloud Service no admite ningún otro valor. Encontrará más información sobre los índices de búsqueda en la [Documentación sobre búsqueda de contenido e indexación](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/operations/indexing).

### Los nodos descendientes de los nodos de definición de índice de búsqueda personalizada deben ser de tipo `nt:unstructured` {#oakpal-descendent-nodes}

* **Clave**: IndexDescendantNodeType
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

Pueden producirse problemas difíciles de solucionar cuando un nodo de definición de índice de búsqueda personalizada tiene nodos secundarios sin ordenar. Para evitarlos esos nodos, Adobe recomienda que todos los nodos descendientes de un nodo `oak:QueryIndexDefinition` sean de tipo `nt:unstructured`.

### Los nodos de definición de índice de búsqueda personalizada deben contener un nodo secundario denominado `indexRules` que tenga tareas secundarias {#oakpal-custom-search-index}

* **Clave**: IndexRulesNode
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

Un nodo de definición de índice de búsqueda personalizada definido correctamente debe contener un nodo secundario denominado `indexRules` que, a su vez, debe tener al menos una tarea secundaria. Encontrará más información en la [documentación de Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### Los nodos de definición de índices de búsqueda personalizada deben seguir las convenciones de nombres {#oakpal-custom-search-definitions}

* **Clave**: IndexName
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

AEM Cloud Service requiere que las definiciones de índice de búsqueda personalizadas (es decir, nodos de tipo `oak:QueryIndexDefinition`) tengan un nombre que siga un patrón específico como se describe en [Búsqueda e indexación de contenido](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use).

### Los nodos de definición de índice de búsqueda personalizada deben utilizar el índice de tipo Lucene {#oakpal-index-type-lucene}

* **Clave**: IndexType
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

AEM Cloud Service requiere que las definiciones de índice de búsqueda personalizadas (es decir, nodos de tipo `oak:QueryIndexDefinition`) tengan la propiedad `type` con el valor establecido en `lucene`. La indexación mediante tipos de índice heredados debe actualizarse antes de la migración a AEM Cloud Service. Consulte la [Documentación de búsqueda de contenido e indexación](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) para obtener más información.

### Los nodos de definición de índice de búsqueda personalizada no deben contener una propiedad denominada `seed` {#oakpal-property-name-seed}

* **Clave**: IndexSeedProperty
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

AEM Cloud Service prohíbe que las definiciones de índice de búsqueda personalizadas (es decir, los nodos de tipo `oak:QueryIndexDefinition`) contengan una propiedad denominada `seed`. La indexación que utiliza esta propiedad debe actualizarse antes de la migración a AEM Cloud Service. Consulte la [Documentación de búsqueda de contenido e indexación](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) para obtener más información.

### Los nodos de definición de índice de búsqueda personalizada no deben contener una propiedad denominada `reindex` {#oakpal-reindex-property}

* **Clave**: IndexReindexProperty
* **Tipo**: Code Smell
* **Gravedad**: Menor
* **Desde**: Versión 2021.2.0

AEM Cloud Service prohíbe que las definiciones de índice de búsqueda personalizadas (es decir, los nodos de tipo `oak:QueryIndexDefinition`) contengan una propiedad denominada `reindex`. La indexación que utiliza esta propiedad debe actualizarse antes de la migración a AEM Cloud Service. Consulte la [Documentación de búsqueda de contenido e indexación](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use) para obtener más información.

### Los nodos de definición de índice no deben implementarse en el paquete de contenido de la IU {#oakpal-ui-content-package}

* **Clave**: IndexNotUnderUIContent
* **Tipo**: mejora
* **Gravedad**: Menor
* **Desde**: Versión 2024.6.0

AEM Cloud Service prohíbe que las definiciones de índice de búsqueda personalizadas (nodos de tipo `oak:QueryIndexDefinition`) se implementen en el paquete de contenido de la interfaz de usuario.

>[!WARNING]
>
>Se le insta a abordar este problema lo antes posible, porque hará que las canalizaciones fallen a partir de la [versión de agosto de 2024 de Cloud Manager](/help/release-notes/current.md).

### La definición de índice de texto completo personalizada del tipo `damAssetLucene` debe llevar correctamente el prefijo `damAssetLucene` {#oakpal-dam-asset-lucene}

* **Clave**: CustomFulltextIndexesOfTheDamAssetCheck
* **Tipo**: mejora
* **Gravedad**: Menor
* **Desde**: Versión 2024.6.0

AEM Cloud Service prohíbe que las definiciones de índice de texto completo personalizadas de tipo `damAssetLucene` lleven un prefijo distinto de `damAssetLucene`.

>[!WARNING]
>
>Se le insta a abordar este problema lo antes posible, porque hará que las canalizaciones fallen a partir de la [versión de agosto de 2024 de Cloud Manager](/help/release-notes/current.md).

### Los nodos de definición de índice no deben contener propiedades con el mismo nombre {#oakpal-index-property-name}

* **Clave**: DuplicateNameProperty
* **Tipo**: mejora
* **Gravedad**: Menor
* **Desde**: Versión 2024.6.0

AEM Cloud Service prohíbe que las definiciones de índice de búsqueda personalizadas (es decir, los nodos de tipo `oak:QueryIndexDefinition`) contengan propiedades con el mismo nombre

>[!WARNING]
>
>Se le insta a abordar este problema lo antes posible, porque hará que las canalizaciones fallen a partir de la [versión de agosto de 2024 de Cloud Manager](/help/release-notes/current.md).

### Está prohibido personalizar ciertas definiciones de índice predefinido {#oakpal-customizing-ootb-index}

* **Clave**: RestrictIndexCustomization
* **Tipo**: mejora
* **Gravedad**: Menor
* **Desde**: Versión 2024.6.0

AEM Cloud Service prohíbe las modificaciones no autorizadas de los siguientes índices OOTB:

* `nodetypeLucene`
* `slingResourceResolver`
* `socialLucene`
* `appsLibsLucene`
* `authorizables`
* `pathReference`

>[!WARNING]
>
>Se le insta a abordar este problema lo antes posible, porque hará que las canalizaciones fallen a partir de la [versión de agosto de 2024 de Cloud Manager](/help/release-notes/current.md).

### La configuración de los tokenizadores en los analizadores debe crearse con el nombre `tokenizer` {#oakpal-tokenizer}

* **Clave**: AnalyzerTokenizerConfigCheck
* **Tipo**: mejora
* **Gravedad**: Menor
* **Desde**: Versión 2024.6.0

AEM Cloud Service prohíbe la creación de tokenizadores con nombres incorrectos en los analizadores. Los tokenizadores siempre se deben definir como `tokenizer`.

### La configuración de las definiciones de indexación no debe contener espacios {#oakpal-indexing-definitions-spaces}

* **Clave**: PathSpacesCheck
* **Tipo**: mejora
* **Gravedad**: Menor
* **Desde**: Versión 2024.7.0

AEM Cloud Service prohíbe la creación de definiciones de indexación que contengan propiedades con espacios.

## Herramienta de optimización de Dispatcher {#dispatcher-optimization-tool-rules}

En la sección siguiente se enumeran las comprobaciones de la Herramienta de optimización de Dispatcher (DOT) ejecutadas por Cloud Manager. Siga los vínculos para cada comprobación de su definición y detalles de GitHub.

* [Tokens inesperados de configuración de Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [Presupuesto no coincidente de configuración de Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [Falta la llave de configuración de Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [Llave adicional de configuración de Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Falta la propiedad obligatoria de configuración de Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Propiedad de configuración de Dispatcher en desuso](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [Configuración de Dispatcher no encontrada](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [Archivo de configuración de Httpd no encontrado](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Configuración general de Dispatcher](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [La caché del conjunto de servidores de publicación de Dispatcher debe tener `serveStaleOnError` activado](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [Los filtros de conjunto de servidores de publicación de Dispatcher deben contener las reglas de denegación predeterminadas de la versión 6.x.x del arquetipo de AEM](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [La propiedad `statfileslevel` de la caché del conjunto de servidores de publicación de Dispatcher debe ser >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [La propiedad `gracePeriod` del conjunto de servidores de publicación de Dispatcher debe ser >= 2](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [Cada conjunto de servidores de Dispatcher debe tener un nombre único](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [La caché del conjunto de servidores de publicación de Dispatcher debe tener sus reglas `ignoreUrlParams` configuradas en forma de lista de permitidos](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [Los filtros del conjunto de servidores de publicación de Dispatcher deben especificar los selectores Sling permitidos en forma de lista de permitidos](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [Los filtros del conjunto de servidores de publicación de Dispatcher deben especificar los patrones de sufijos de Sling permitidos en forma de lista de permitidos](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [No utilice la directiva “Requerir todo concedido” en una sección del Directorio VirtualHost con una ruta de acceso de directorio raíz](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
