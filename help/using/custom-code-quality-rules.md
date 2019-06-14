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
source-git-commit: f8cea9d52ebb01d7f5291d4dfcd82011da8dacc2

---


# Reglas de calidad de código personalizado {#custom-code-quality-rules}

Esta página describe las reglas de calidad de código personalizadas ejecutadas por Cloud Manager creadas en función de las prácticas recomendadas de Ingeniería de AEM.

>[!NOTE]
>
>Las muestras de código proporcionadas aquí son sólo para fines ilustrativos.

## Sonarqube Rules {#sonarqube-rules}

La siguiente sección resalta las reglas de sonarchbe:

### No utilizar funciones potencialmente peligrosas {#do-not-use-potentially-dangerous-functions}

**Clave**: Cqrules: CWE -676

**Tipo**: Vulnerabilidad

**Gravedad**: Mayor

**Desde**: Versión 2018.4.0

Los métodos ***Thread. stop ()*** y ***Thread. interrupt ()*** pueden producir problemas difíciles de reproducir y, en algunos casos, vulnerabilidades de seguridad. Su uso debe monitorearse y validarse de manera estricta. En general, el paso de mensajes es una manera más segura de lograr objetivos similares.

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

#### Código compatible {#compliant-code}

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

### No utilice cadenas de formato que puedan estar controladas externamente {#do-not-use-format-strings-which-may-be-externally-controlled}

**Clave**: Cqrules: CWE -134

**Tipo**: Vulnerabilidad

**Gravedad**: Mayor

**Desde**: Versión 2018.4.0

El uso de una cadena de formato de una fuente externa (como un parámetro de solicitud o contenido generado por usuarios) puede exponer una aplicación a ataques de denegación de servicio. Existen circunstancias en las que una cadena de formato puede estar controlada externamente, pero solo se permite desde fuentes de confianza.

#### Código no compatible {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text");
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### Las solicitudes HTTP deben tener siempre el socket y los tiempos de espera de conexión {#http-requests-should-always-have-socket-and-connect-timeouts}

**Clave**: Cqrules: Connectiontimeoutcomponent

**Tipo**: Error

**Gravedad**: Crítico

**Desde**: Versión 2018.6.0

Cuando se ejecutan solicitudes HTTP desde una aplicación AEM, es fundamental asegurarse de que los tiempos de espera adecuados estén configurados para evitar consumo ininnecesario de procesos. Desafortunadamente, el comportamiento predeterminado del cliente HTTP predeterminado de Java (java.net.Ht tpurlconnection) y del cliente de componentes Apache HTTP de uso habitual es nunca el tiempo de espera, por lo que los tiempos de espera deben establecerse explícitamente. Además, como práctica recomendada, estos tiempos de espera no deben exceder los 60 segundos.

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

### Los clientes no deberían implementar ni ampliar las API de producto anotadas con @ addertype {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

**Clave**: CQBP -84, CQBP -84-dependencias

**Tipo**: Error

**Gravedad**: Crítico

**Desde**: Versión 2018.7.0

La API de AEM contiene interfaces y clases Java que solo están pensadas para utilizarse, pero no implementadas, por código personalizado. Por ejemplo, la interfaz *com.day.cq.wc m. api. La página* está diseñada para implementarse solo por ***AEM***.

Cuando se agregan nuevos métodos a estas interfaces, estos métodos adicionales no afectan al código existente que utiliza estas interfaces y, como resultado, la adición de nuevos métodos a estas interfaces se considera compatible con versiones anteriores. Sin embargo, si el código ***personalizado implementa*** una de estas interfaces, dicho código personalizado ha introducido un riesgo de compatibilidad con versiones anteriores para el cliente.

Las interfaces (y las clases) que solo están pensadas para su implementación por AEM se anotan con *org. osgi. annotation. versioning. providertype* (o, en algunos casos, con una anotación heredada similar *aqute. bnd. annotation. providertype*). Esta regla identifica los casos en que se implementa una interfaz de este tipo (o una clase) por código personalizado.

#### Código no compatible {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Los objetos resourceresolver deben cerrarse siempre {#resourceresolver-objects-should-always-be-closed}

**Clave**: Cqrules: CQBP -72

**Tipo**: Huelgar código

**Gravedad**: Mayor

**Desde**: Versión 2018.4.0

Resourceresolver objetos obtenidos de resourceresolverfactory consumen recursos del sistema. Aunque existen medidas para reclamar estos recursos cuando resourceresolver ya no está en uso, es más eficaz cerrar explícitamente cualquier objeto resourceresolver abierto llamando al método close ().

Una mala idea relativamente común es que los objetos resourceresolver creados con una sesión JCR existente no deben cerrarse explícitamente o que al hacerlo se cierre la sesión JCR subyacente. Este no es el caso: sin importar cómo se abra resourceresolver, debe cerrarse cuando ya no se utilice. Como resourceresolver implementa la interfaz Closeable, también es posible utilizar la sintaxis try-with-resources en lugar de invocar explícitamente close ().

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

### No utilizar rutas Sling servlet para registrar servlets {#do-not-use-sling-servlet-paths-to-register-servlets}

**Clave**: Cqrules: CQBP -75

**Tipo**: Huelgar código

**Gravedad**: Mayor

**Desde**: Versión 2018.4.0

Como se describe en la [documentación Sling](http://sling.apache.org/documentation/the-sling-engine/servlets.html), los servlets de enlaces por rutas se desaconsejan. Los servlets enlazados por rutas no pueden utilizar controles de acceso JCR estándar y, como resultado, requieren un rigor de seguridad adicional. En lugar de utilizar servlets enlazados por rutas, se recomienda crear nodos en el repositorio y registrar servlets por tipo de recurso.

#### Código no compatible {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Las excepciones capturadas deben registrarse o arrojarse, pero no {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

**Clave**: Cqrules: CQBP -44—Catchandeitherlogorthrow

**Tipo**: Huelgar código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

En general, se debe registrar una excepción una vez. Registrar las excepciones varias veces puede causar confusión, ya que no está claro cuántas veces ha tenido lugar una excepción. Patrón más común que lleva a esto y genera una excepción detectada.

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

### Evite tener una sentencia de registro inmediatamente seguida de una sentencia throw {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

**Clave**: Cqrules: CQBP -44—Consecutivelylogandthrow

**Tipo**: Huelgar código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

Otro patrón común para evitar es registrar un mensaje y, a continuación, emitir inmediatamente una excepción. Esto suele indicar que el mensaje de excepción terminará duplicado en los archivos de registro.

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

### Evite el registro en INFORMACIÓN al tratar las solicitudes GET o HEAD {#avoid-logging-at-info-when-handling-get-or-head-requests}

**Clave**: Cqrules: CQBP -44—Loginfoingetorheadrequests

**Tipo**: Huelgar código

**Gravedad**: Menor

En general, el nivel de registro de información debe utilizarse para delimitar acciones importantes y, de forma predeterminada, AEM está configurado para registrarse en el nivel INFO o superior. Los métodos GET y HEAD solo deben ser operaciones de solo lectura y, por lo tanto, no constituyen acciones importantes. El registro en el nivel de información como respuesta a las solicitudes GET o HEAD probablemente cree un ruido de registro significativo que dificulte la identificación de información útil en los archivos de registro. El registro al gestionar las solicitudes GET o HEAD debe estar en los niveles WARN o ERROR cuando algo incorrecto o en los niveles DEBUG o TRACE si información de solución de problemas más profunda resulta útil.

>[!CAUTION]
>
>Esto no se aplica al registro de access. log-type para cada solicitud.

#### Código no compatible {#non-compliant-code-8}

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

### No utilizar Exception. getmessage () como el primer parámetro de una sentencia de registro {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

**Clave**: Cqrules: CQBP -44—Exceptiongetmessageisfirstlogparam

**Tipo**: Huelgar código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

Como práctica recomendada, los mensajes de registro deben proporcionar información contextual sobre dónde se ha producido una excepción. Aunque el contexto también se puede determinar mediante el uso de huellas de pila, en general el mensaje de registro será más fácil de leer y comprender. Como resultado, al registrar una excepción, se recomienda utilizar el mensaje de excepción como mensaje de registro; el mensaje de excepción contendrá lo que salió mal, mientras que el mensaje de registro debe utilizarse para informar a un lector de registro de lo que estaba haciendo la aplicación cuando se produjo la excepción. El mensaje de excepción seguirá registrándose; al especificar su propio mensaje, los registros solo serán fáciles de entender.

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

### El inicio de sesión catch debe estar en el nivel WARN o ERROR {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

**Clave**: Cqrules: CQBP -44—Wrongloglevelincatchblock

**Tipo**: Huelgar código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

Como sugiere el nombre, las excepciones de Java deben utilizarse siempre en *circunstancias excepcionales* . Como resultado, cuando se captura una excepción, es importante asegurarse de que los mensajes de registro se registran en el nivel adecuado, ya sea WARN o ERROR. Esto garantiza que esos mensajes aparezcan correctamente en los registros.

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

### No imprima huellas de pila en la consola {#do-not-print-stack-traces-to-the-console}

**Clave**: Cqrules: CQBP -44—Exceptionprintstacktrace

**Tipo**: Huelgar código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

Como se ha mencionado, el contexto es crítico al comprender los mensajes de registro. Usar Exception. printstacktrace () hace que **sólo** la pila trace se incluya en el flujo de error estándar, perdiendo así todo el contexto. Además, en una aplicación multiproceso como AEM si se imprimen varias excepciones mediante este método en paralelo, sus traces de pila pueden superponerse lo cual produce una confusión significativa. Las excepciones solo deben registrarse a través del marco de registro.

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

### No generar en Salida estándar o Error estándar {#do-not-output-to-standard-output-or-standard-error}

**Clave**: Cqrules: CQBP -44—loglevelconsolflagprinters

**Tipo**: Huelgar código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

El inicio de sesión en AEM debe realizarse siempre mediante el marco de registro (SLF 4 J). La salida directa a los flujos de error estándar o estándar pierde la información estructural y contextual proporcionada por el marco de registro y, en algunos casos, puede provocar problemas de rendimiento.

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

### Evite codificar /apps y /libs rutas {#avoid-hardcoded-apps-and-libs-paths}

**Clave**: Cqrules: CQBP -71

**Tipo**: Huelgar código

**Gravedad**: Menor

**Desde**: Versión 2018.4.0

En general, las rutas que comienzan con /libs y /apps no deben estar codificadas como las rutas a las que hacen referencia más comúnmente como rutas relativas a la ruta de búsqueda Sling (que se establece en /libs o en aplicaciones de forma predeterminada). El uso de la ruta absoluta puede introducir defectos sutiles que solo aparecerían más adelante en el ciclo vital del proyecto.

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
