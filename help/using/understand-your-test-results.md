---
title: Comprender los resultados de la prueba
seo-title: Comprender los resultados de la prueba
description: Obtenga más información sobre las tres puertas de nivel mientras se ejecuta una canalización en Cloud Manager
seo-description: Siga esta página para obtener más información sobre tres puertas de nivel mientras ejecuta una canalización, análisis de código, rendimiento y pruebas de seguridad para validar el programa en Cloud Manager.
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4
translation-type: tm+mt
source-git-commit: b5233e1932888b515d8dc26a6493cbd26686bc3c
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 7%

---


# Comprender los resultados de la prueba {#understand-your-test-results}

Durante la ejecución de la canalización, se capturan varias métricas y se comparan con los Indicadores de rendimiento clave (KPI) definidos por el propietario del negocio o con los estándares establecidos por Adobe Managed Services.

Estos se registran utilizando el sistema de enlace de tres niveles definido en esta sección.

## Puerta de tres niveles al ejecutar una canalización {#three-tier-gates-while-running-a-pipeline}

Hay tres puertas en la canalización:

* Calidad de código
* Pruebas de rendimiento
* Pruebas de seguridad

Para cada una de estas puertas, hay una estructura de tres niveles para los problemas identificados por la puerta.

* **Crítico** : Son problemas identificados por la puerta que causan un fallo inmediato de la canalización.
* **Importante** : Son problemas identificados por la puerta que hacen que la canalización introduzca un estado pausado. Un administrador de implementación, un administrador de proyectos o un propietario de empresa pueden anular los problemas, en cuyo caso la canalización continúa, o pueden aceptar los problemas, en cuyo caso la canalización se detiene con un error.
* **Información** : Son problemas identificados por la puerta que se proporcionan exclusivamente con fines informativos y no tienen impacto en la ejecución de la canalización.

>[!NOTE]
>
>En una canalización de solo calidad de código, no se pueden anular los errores importantes en la puerta de prueba de calidad de código, ya que el paso Prueba de calidad de código es el último paso de la canalización.

## Prueba de calidad de código {#code-quality-testing}

Este paso evalúa la calidad del código de la aplicación. Es el objetivo central de una canalización solo de calidad de código y se ejecuta inmediatamente después del paso de compilación en todas las canalizaciones que no sean de producción y producción. Consulte [Configuración de la canalización CI-CD](/help/using/configuring-pipeline.md) para obtener más información sobre los distintos tipos de canalizaciones.

### Entender la prueba de calidad del código {#understanding-code-quality-testing}

En la prueba de calidad del código, se analiza el código fuente para asegurarse de que cumple determinados criterios de calidad. Actualmente, esto se implementa mediante una combinación de SonarQube, un examen a nivel de paquete de contenido usando OakPAL y la validación de Dispatcher usando la Herramienta de Optimización de Dispatcher. Hay más de 100 reglas que combinan reglas genéricas de Java y reglas específicas de AEM. Algunas de las reglas específicas del AEM se crean en función de las prácticas recomendadas de AEM ingeniería y se denominan [Reglas de calidad de código personalizado](/help/using/custom-code-quality-rules.md).

>[!NOTE]
>Puede descargar la lista completa de reglas [aquí](/help/using/assets/CodeQuality-rules-AMS.xlsx).

Los resultados de este paso se entregan como *Clasificación*. La tabla siguiente resume las clasificaciones de varios criterios de prueba:

| Nombre | Definición | Categoría | Umbral de error |
|--- |--- |--- |--- |
| Clasificación de seguridad | A = 0 Vulnerabilidad <br/>B = al menos 1 Vulnerabilidad menor<br/> C = al menos 1 Vulnerabilidad mayor <br/>D = al menos 1 Vulnerabilidad crítica <br/>E = al menos 1 Vulnerabilidad del bloqueador | Importante | &lt; B |
| Clasificación de fiabilidad | A = 0 Error <br/>B = al menos 1 Error menor <br/>C = al menos 1 Error mayor <br/>D = al menos 1 Error crítico<br/>E = al menos 1 Error del bloqueador | Importante | &lt; C |
| Puntuación de mantenimiento | El coste de corrección pendiente de los olores de código es: <br/><ul><li>&lt;> </li><li>entre el 6% y el 10% la calificación es a B </li><li>entre el 11% y el 20% la calificación es C </li><li>entre el 21 y el 50 % la calificación es D</li><li>cualquier valor superior al 50% es una E</li></ul> | Importante | &lt; A |
| Cobertura | Una combinación de cobertura de línea de prueba unitaria y cobertura de condición utilizando esta fórmula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)` <br/>donde: CT = condiciones que se han evaluado en &#39;true&#39; al menos una vez al ejecutar pruebas unitarias <br/>CF = condiciones que se han evaluado en &#39;false&#39; al menos una vez al ejecutar pruebas unitarias <br/>LC = líneas cubiertas = líneas_to_cover - uncovered_lines <br/><br/> B = número total de condiciones <br/>EL = número total de líneas ejecutables (lines_to_cover) | Importante | &lt; 50% |
| Pruebas unitarias omitidas | Número de pruebas unitarias omitidas. | Información | > 1 |
| Problemas abiertos | Tipos de problemas generales: Vulnerabilidades, errores y huecos de código | Información | > 0 |
| Líneas duplicadas | Número de líneas involucradas en bloques duplicados. <br/>Para que un bloque de código se considere duplicado:  <br/><ul><li>**Proyectos que no son de Java:**</li><li>Debe haber al menos 100 tokens sucesivos y duplicados.</li><li>Estos tokens deben propagarse al menos en: </li><li>30 líneas de código para COBOL </li><li>20 líneas de código para ABAP </li><li>10 líneas de código para otros idiomas</li><li>**Proyectos Java:**</li><li> Debe haber al menos 10 afirmaciones sucesivas y duplicadas, independientemente del número de tokens y líneas.</li></ul> <br/>Las diferencias en la sangría y en los literales de cadena se ignoran al detectar duplicados. | Información | > 1% |
| Compatibilidad del Cloud Service | Número de problemas de compatibilidad con Cloud Service identificados. | Información | > 0 |


>[!NOTE]
>
>Consulte [Definiciones de métricas](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) para obtener definiciones más detalladas.

>[!NOTE]
>
>Para obtener más información sobre las reglas de calidad de código personalizadas ejecutadas por [!UICONTROL Cloud Manager], consulte [Reglas de calidad de código personalizado](custom-code-quality-rules.md).

### Tratamiento de falsos positivos {#dealing-with-false-positives}

El proceso de digitalización de la calidad no es perfecto y a veces identifica incorrectamente los problemas que no son realmente problemáticos. Esto se denomina &quot;falso positivo&quot;.

En estos casos, el código fuente se puede anotar con la anotación estándar Java `@SuppressWarnings` que especifica el ID de regla como atributo de anotación. Por ejemplo, un problema común es que la regla SonarQube para detectar contraseñas codificadas puede ser agresiva sobre cómo se identifica una contraseña codificada.

Para ver un ejemplo específico, este código sería bastante común en un proyecto AEM que tiene código para conectarse a algún servicio externo:

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube entonces generará una vulnerabilidad Blocker. Después de revisar el código, identifique que esta no es una vulnerabilidad y pueda anotarla con el id de regla adecuado.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Sin embargo, por otro lado, si el código era realmente así:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

A continuación, la solución correcta es quitar la contraseña codificada.

>[!NOTE]
>
>Aunque se recomienda hacer que la anotación `@SuppressWarnings` sea lo más específica posible, es decir, anotar solo la sentencia o bloque específico que causa el problema, es posible realizar anotaciones a nivel de clase.

## Pruebas de seguridad {#security-testing}

[!UICONTROL Cloud Manager] ejecuta el paso existente  ***AEM Security Heath*** Checkson después de la implementación e informa del estado a través de la interfaz de usuario. Los resultados se agregan de todas las instancias AEM del entorno.

Si alguna de las **Instancias** informa de un error en una comprobación de estado determinada, toda la **Entorno** falla en esa comprobación de estado. Al igual que con las pruebas de calidad y rendimiento del código, estas comprobaciones de estado se organizan en categorías y se notifican utilizando el sistema de tres niveles. La única distinción es que no hay umbral en el caso de las pruebas de seguridad. Todos los controles de salud simplemente se aprueban o no.

En la tabla siguiente se enumeran las comprobaciones actuales:

| **Nombre** | **Implementación de comprobación de estado** | **Categoría** |
|---|---|---|
| Deserialización firewall Adjuntar preparación de API está en un estado aceptable | Disposición de la API de anexo de cortafuegos de deserialización | Importante |
| El firewall de deserialización funciona | Cortafuegos de deserialización funcional | Importante |
| Deserialización del firewall cargado | Cortafuegos de deserialización cargado | Importante |
| La implementación de AuthorizableNodeName no expone el ID autorizado en el nombre/ruta del nodo. | Generación del nombre de nodo con autorización | Importante |
| Se han cambiado las contraseñas predeterminadas | Cuentas de inicio de sesión predet. | Importante |
| El servlet de GET predeterminado de Sling está protegido de ataques DOS. | Sling Get Servlet | Importante |
| El controlador de script Java de Sling está configurado correctamente | Sling Java Script Handler | Importante |
| El controlador de script JSP de Sling está configurado correctamente | Controlador de script JSP de Sling | Importante |
| SSL está configurado correctamente | Configuración SSL | Importante |
| No se encontraron directivas de perfil de usuario obviamente inseguras | Acceso predet. del perfil de usuario | Importante |
| El filtro de referente de Sling está configurado para evitar ataques de CSRF | Filtro de referente de Sling | Importante |
| El Administrador de bibliotecas HTML de Adobe Granite está configurado correctamente | Configuración del administrador de bibliotecas HTML de CQ | Importante |
| El paquete de soporte CRXDE está deshabilitado | Compatibilidad con CRXDE | Importante |
| El paquete y el servlet Sling DavEx están desactivados | Comprobación de estado de DavEx | Importante |
| El contenido de muestra no está instalado | Paquetes de contenido de ejemplo | Importante |
| Tanto el filtro de solicitud WCM como el filtro de depuración WCM están desactivados | Configuración de filtros WCM | Importante |
| El paquete y el servlet Sling WebDAV están correctamente configurados | Comprobación de estado de WebDAV | Importante |
| El servidor web está configurado para evitar el secuestro de clics | Configuración de servidor web | Importante |
| La replicación no utiliza el usuario &quot;admin&quot; | Replicación y usuarios de transporte | Información |

## Pruebas de rendimiento {#performance-testing}

*La* prueba de rendimiento en  [!UICONTROL Cloud Manager] se implementa mediante una prueba de 30 minutos.

Durante la configuración de la canalización, el administrador de implementación puede decidir cuánto tráfico dirigir a cada bloque.

Puede obtener más información sobre los controles de compartimento en [Configuración de la canalización de CI/CD](configuring-pipeline.md).

>[!NOTE]
>
>Para configurar el programa y definir los KPI, consulte [Configuración del programa](setting-up-program.md).

En la tabla siguiente se resume la matriz de prueba de rendimiento utilizando el sistema de navegación de tres niveles:

| **Métrica** | **Categoría** | **Umbral de error** |
|---|---|---|
| Tasa de error de solicitud de página % | Importante | >= 2% |
| Tasa de uso de CPU | Importante | >= 80 % |
| Tiempo de espera de IO de disco | Importante | >= 50% |
| Tiempo de respuesta del percentil 95 | Importante | >= KPI a nivel de programa |
| Tiempo de respuesta máximo | Importante | >= 18 segundos |
| Vistas de página por minuto | Importante | &lt; Program-level=&quot;&quot; KPI=&quot;&quot;> |
| Uso del ancho de banda del disco | Importante | >= 90% |
| Utilización del ancho de banda de red | Importante | >= 90 % |
| Solicitudes por minuto | Información | >= 6000 |

### Gráficos de resultados de pruebas de rendimiento {#performance-testing-results-graphs}

Se han añadido nuevos gráficos y opciones de descarga al cuadro de diálogo Resultados de la prueba de rendimiento .

Cuando se abre el cuadro de diálogo Prueba de rendimiento, los paneles de métricas se pueden expandir para mostrar un gráfico, proporcionar un vínculo a una descarga o ambos.

Para la [!UICONTROL Cloud Manager] versión 2018.7.0, esta funcionalidad está disponible para las siguientes métricas:

* **Uso de CPU**
   * Un gráfico de la utilización de la CPU durante el periodo de prueba.

* **Tiempo de espera de E/S de disco**
   * Un gráfico del tiempo de espera de E/S de disco durante el período de prueba.

* **Tasa de error de página**
   * Gráfico de errores de página por minuto durante el periodo de prueba.
   * Un archivo CSV enumera las páginas que han producido un error durante la prueba.

* **Uso del ancho de banda del disco**
   * Gráfico de la utilización del ancho de banda del disco durante el periodo de prueba.

* **Utilización del ancho de banda de red**
   * Gráfico de la utilización del ancho de banda de red durante el periodo de prueba.

* **Tiempo de respuesta máximo**
   * Un gráfico del tiempo de respuesta pico por minuto durante el periodo de prueba.

* **Tiempo de respuesta del percentil 95**
   * Gráfico del tiempo de respuesta del percentil 95 por minuto durante el periodo de prueba.
   * Archivo CSV que enumera las páginas cuyo tiempo de respuesta del percentil 95 ha superado el KPI definido.

Las imágenes siguientes muestran los gráficos de prueba de rendimiento:

![](assets/understand_test-results-screen1.png)

![](assets/screen_shot_2018-09-05at83933pm.png)

