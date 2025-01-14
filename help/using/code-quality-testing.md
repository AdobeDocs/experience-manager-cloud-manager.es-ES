---
title: Prueba de calidad del código
description: Descubra cómo funcionan las pruebas de calidad del código de las canalizaciones y cómo pueden mejorar la calidad de las implementaciones.
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: f5e6ac81c6454730850bb7e884d82be48d2f8525
workflow-type: ht
source-wordcount: '2793'
ht-degree: 100%

---


# Prueba de calidad del código {#code-quality-testing}

Descubra cómo funcionan las pruebas de calidad del código de las canalizaciones y cómo pueden mejorar la calidad de las implementaciones.

## Introducción {#introduction}

Durante la ejecución de canalización, el software captura una serie de métricas. A continuación, estas métricas se comparan con los indicadores clave de rendimiento (KPI) definidos por el propietario de la empresa. O bien, se comparan con los estándares establecidos por Adobe Managed Services.

Estos resultados se notifican mediante un sistema de clasificación de tres niveles.

## Clasificaciones en tres niveles {#three-tiered-ratings}

Hay tres puertas en la canalización:

* Calidad de código
* Pruebas de rendimiento
* Pruebas de seguridad

Para cada una de estas puertas, hay una estructura de tres niveles para los problemas identificados por la puerta.

* **Crítico**: problemas que causan un fallo inmediato de la canalización.
* **Importante**: problemas que hacen que la canalización entre en estado de pausa. Un administrador de implementación, un administrador de proyectos o un propietario de empresa pueden anular los problemas. En tal caso, la canalización se ejecuta según lo previsto. De forma alternativa, pueden aceptar los problemas, lo cual haría que la canalización se detenga con un error. La anulación de errores importantes está sujeta a un [tiempo de espera](/help/using/code-deployment.md#timeouts).
* **Información**: problemas que se proporcionan exclusivamente con fines informativos y que no afectan a la ejecución de canalización.

>[!NOTE]
>
>En una canalización de solo calidad de código, no se pueden anular los errores importantes en la puerta de calidad del código, ya que el paso de prueba de calidad del código es el último paso de la canalización.

## Prueba de calidad del código {#code-quality-testing-step}

Este paso de prueba evalúa la calidad del código de la aplicación, que es el propósito principal de una canalización de solo calidad de código. Esto se ejecuta inmediatamente después del paso de generación en todas las canalizaciones que sean y no sean de producción. Para obtener más información, vaya a [Configuración de canalizaciones que no sean de producción](/help/using/non-production-pipelines.md).

Las pruebas de calidad del código analizan el código fuente para asegurarse de que cumple determinados criterios de calidad.

El software lo implementa mediante una combinación de análisis de SonarQube, un examen de nivel de paquete de contenido mediante OakPAL y una validación de Dispatcher mediante la herramienta de optimización de Dispatcher.

Hay más de 100 reglas que combinan reglas genéricas de Java y reglas específicas de AEM. Algunas de las reglas específicas de AEM se crean en función de las prácticas recomendadas de AEM Engineering y se denominan [reglas de calidad de código personalizadas](/help/using/custom-code-quality-rules.md).

Puede descargar la lista completa de reglas [mediante este vínculo](/help/assets/CodeQuality-rules-latest-AMS.xlsx).

>[!IMPORTANT]
>
>A partir del jueves, 13 de febrero de 2025 (Cloud Manager 2025.2.0), la Calidad del código de Cloud Manager utilizará una versión actualizada de SonarQube 9.9 y una lista actualizada de reglas que puede [descargar aquí](/help/assets/CodeQuality-rules-latest-AMS-2024-12-0.xlsx).

Los resultados de las pruebas de calidad del código se muestran como una clasificación resumida en esta tabla.

| Nombre | Definición | Categoría | Umbral de error |
| --- | --- | --- | --- |
| Clasificación de seguridad | A = Sin vulnerabilidades<br/>B = Al menos una vulnerabilidad menor<br/>C = Al menos una vulnerabilidad importante<br/>D = Al menos una vulnerabilidad esencial<br/>E = Al menos una vulnerabilidad de bloqueo | Esencial | &lt; B |
| Clasificación de fiabilidad | A = No hay errores<br/>B = Al menos un error menor <br/>C = Al menos un error importante<br/>D = Al menos un error esencial<br/>E = Al menos un error de bloqueo | Importante | &lt; C |
| Clasificación de mantenimiento | Definido por el coste de corrección pendiente de los olores de código como un porcentaje del tiempo que ya ha pasado a la aplicación<br/><ul><li>A = &lt;=5 %</li><li>B = 6-10 %</li><li>C = 11-20 %</li><li>D = 21-50 %</li><li>E = >50 %</li></ul> | Importante | &lt; A |
| Cobertura | Definido por una combinación de cobertura de línea de prueba unitaria y cobertura de condición mediante la fórmula: <br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` = Condiciones que se han evaluado como `true` al menos una vez al ejecutar las pruebas unitarias</li><li>`CF` = Condiciones que se han evaluado como `false` al menos una vez al ejecutar las pruebas unitarias</li><li>`LC` = Líneas cubiertas = líneas_por_cubrir - líneas_descubiertas</li><li>`B` = número total de condiciones</li><li>`EL` = número total de líneas ejecutables (líneas_por_cubrir)</li></ul> | Importante | &lt; 50% |
| Pruebas unitarias omitidas | Número de pruebas unitarias omitidas | Información | > 1 |
| Problemas abiertos | Tipos de problemas generales: Vulnerabilidades, errores y huecos de código | Información | > 0 |
| Líneas duplicadas | Se define como el número de líneas involucradas en bloques duplicados. Un bloque de código se considera duplicado en las siguientes condiciones.<br>Proyectos que no son de Java:<ul><li>Debe haber al menos 100 tokens sucesivos y duplicados.</li><li>Estos tokens deben propagarse por lo menos: </li><li>30 líneas de código para COBOL </li><li>20 líneas de código para ABAP </li><li>10 líneas de código para otros idiomas</li></ul>Proyectos Java:<ul></li><li> Debe haber al menos 10 instrucciones sucesivas y duplicadas, independientemente del número de tokens y líneas.</li></ul>Las diferencias en la sangría, así como en los literales de cadena, se omiten al detectar duplicados. | Información | > 1 % |
| Compatibilidad de Cloud Service | Número de problemas de compatibilidad de Cloud Service identificados | Información | > 0 |

>[!NOTE]
>
>Para obtener información más detallada, consulte [Definiciones de métricas de SonarQube](https://docs.sonarsource.com/sonarqube-server/latest/user-guide/code-metrics/metrics-definition/).

>[!NOTE]
>
>Para obtener más información sobre las reglas de calidad de código personalizadas ejecutadas por [!UICONTROL Cloud Manager], consulte [Reglas de calidad de código personalizadas](custom-code-quality-rules.md).

### Tratar con falsos positivos {#dealing-with-false-positives}

El proceso de análisis de la calidad no es perfecto y a veces identifica incorrectamente problemas que no son realmente problemáticos. Este escenario se denomina como falso positivo.

En estos casos, el código fuente se puede anotar con la anotación de Java estándar `@SuppressWarnings` que especifica el ID de regla como atributo de anotación. Por ejemplo, un falso positivo común es que la regla SonarQube para detectar contraseñas codificadas puede ser agresiva sobre cómo se identifica una contraseña codificada.

El siguiente código es bastante común en un proyecto de AEM, que tiene código para conectarse a algún servicio externo.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube aumentará entonces la vulnerabilidad del bloqueador. Pero después de revisar el código, se reconoce que este problema no supone una vulnerabilidad y se puede anotar el código con el ID de regla adecuado.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Sin embargo, si el código era realmente como se indica a continuación:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

A continuación, la solución correcta es quitar la contraseña codificada.

>[!NOTE]
>
>La práctica recomendada es hacer que la anotación `@SuppressWarnings` sea lo más específica posible. Es decir, anote únicamente la instrucción o el bloque específicos que causan el problema. Sin embargo, es posible realizar anotaciones en el nivel de clase. Hacerlo permite una supresión más amplia de las advertencias.

## Pruebas de seguridad {#security-testing}

[!UICONTROL Cloud Manager] ejecuta las comprobaciones de estado de seguridad de AEM existentes en el entorno de ensayo después de la implementación, e informa del estado a través de la IU. Los resultados se agregan de todas las instancias AEM del entorno.

Estas mismas comprobaciones de estado se pueden ejecutar en cualquier momento a través de la consola web o el tablero de operaciones.

Si alguno de los casos indica un error en una comprobación de estado determinada, todo el entorno falla en esa comprobación de estado. Al igual que con las pruebas de calidad y el rendimiento de código, estas comprobaciones de estado se organizan en categorías y se comunican utilizando el sistema de acceso de tres niveles. La única distinción es que no hay umbral si hay pruebas de seguridad. Todas las comprobaciones de estado se aprueban o no.

La siguiente tabla enumera las comprobaciones de estado.

| Nombre | Implementación de la comprobación de estado | Categoría |
|---|---|---|
| Adjuntar preparación de API del cortafuegos de deserialización está en un estado aceptable. | [Disposición de la API de anexo de cortafuegos de deserialización](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | Esencial |
| El cortafuegos de deserialización funciona. | [Cortafuegos de deserialización funcional](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | Esencial |
| Se ha cargado el cortafuegos de deserialización. | [Cortafuegos de deserialización cargado](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/security/mitigating-serialization-issues#security) | Esencial |
| La implementación `AuthorizableNodeName` no expone el ID autorizado en el nombre o la ruta del nodo. | [Generación del nombre de nodo con autorización](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/security/security-checklist#security) | Esencial |
| Se han cambiado las contraseñas predeterminadas. | [Cuentas de inicio de sesión predeterminado](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/security/security#users-and-groups-in-aem) | Esencial |
| El servlet de GET predeterminado de Sling está protegido de ataques DOS. | Sling Get Servlet | Esencial |
| El controlador Sling JavaScript está configurado correctamente. | Controlador Sling JavaScript | Esencial |
| El controlador Sling JSP Script está configurado correctamente. | Controlador Sling JSP Script | Esencial |
| SSL está configurado correctamente. | Configuración SSL | Esencial |
| Obviamente, no se encuentran políticas de perfil de usuario inseguras. | Acceso predeterminado del perfil de usuario | Esencial |
| El filtro Referente de Sling está configurado para evitar ataques de CSRF. | [Filtro de remitente del reenvío de Sling](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/security/security-checklist#security) | Importante |
| El Administrador de bibliotecas HTML de Adobe Granite está configurado correctamente. | Configuración del administrador de bibliotecas HTML de CQ | Importante |
| El paquete de soporte CRXDE está deshabilitado. | Compatibilidad con CRXDE | Importante |
| El paquete y el servlet Sling DavEx están deshabilitados. | Comprobación de estado de DavEx | Importante |
| El contenido de muestra no está instalado. | Paquetes de contenido de ejemplo | Importante |
| El filtro de solicitud de gestión de contenidos web y el filtro de depuración de gestión de contenidos web están desactivados. | [Configuración de filtros de gestión de contenidos web](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/implementing/deploying/configuring/osgi-configuration-settings#configuring) | Importante |
| El paquete y el servlet Sling WebDAV están correctamente configurados. | Comprobación de estado de WebDAV | Importante |
| El servidor web está configurado para evitar el secuestro de clics (clickjacking). | Configuración de servidor web | Importante |
| La replicación no emplea el usuario `admin`. | Replicación y usuarios de transporte | Información |

## Pruebas de rendimiento {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager ejecuta pruebas de rendimiento para programas de AEM Sites. La prueba de rendimiento se ejecuta durante aproximadamente 30 minutos. Hace circular usuarios virtuales (contenedores) que simulan que los usuarios reales acceden a páginas en entornos de ensayo para emular el tráfico. Estas páginas se encuentran mediante un rastreador.

#### Usuarios virtuales {#virtual-users}

Cloud Manager mueve usuarios virtuales o contenedores según los indicadores clave de rendimiento (KPI) (tiempo de respuesta y vistas de página por minuto) establecidos por la función **Propietario empresarial**. Estos KPI se establecen al [crear o editar el programa](/help/getting-started/program-setup.md).

Según los indicadores clave de rendimiento (KPI) definidos, se pondrán en marcha hasta diez contenedores que simulen usuarios reales. Las páginas seleccionadas para la prueba se dividen y se asignan a cada usuario virtual.

#### Rastreador {#crawler}

Antes del inicio del período de prueba de 30 minutos, Cloud Manager rastrea el entorno de ensayo utilizando un conjunto de una o más URL semilla configuradas por el ingeniero de éxito del cliente. Empezando por estas URL, el HTML de cada página se inspecciona y los vínculos se atraviesan siguiendo un equilibrio de carga en amplitud.

* De forma predeterminada, este proceso de rastreo está limitado a un máximo de 5000 páginas.
* El número máximo de páginas que se van a probar se puede sobrescribir configurando la [variable de canalización](/help/getting-started/build-environment.md#pipeline-variables) `CM_PERF_TEST_CRAWLER_MAX_PAGES`.
   * Los valores permitidos son `2000`-`7000`.
* Las solicitudes del rastreador tienen un tiempo de espera fijo de 10 segundos.

#### Conjuntos de páginas para pruebas {#page-sets}

Tres conjuntos de páginas seleccionan las páginas. Cloud Manager utiliza los registros de acceso de las instancias de AEM en los entornos de producción y ensayo para determinar los siguientes depósitos.

* **Páginas populares activas**: garantiza que se prueban las páginas más populares a las que acceden los clientes activos. Cloud Manager lee el registro de acceso y determina las 25 páginas más visitadas por los clientes activos para generar una lista de las principales `Popular Live Pages`. La intersección de estas páginas que también están presentes en el entorno de ensayo se rastrean luego en el entorno de ensayo.

* **Otras páginas activas**: garantiza que se prueben las páginas que no están dentro de las 25 más populares, que pueden no tener demasiadas visitas, pero que se deben verificar. De forma similar a lo que sucede con las páginas populares activas, se extraen del registro de acceso y también deben estar presentes en el entorno de ensayo.

* **Nuevas páginas**: prueba páginas nuevas que pueden haberse implementado en el entorno de ensayo y que aún no están en producción, pero que se deben verificar.

##### Distribución del tráfico entre conjuntos de páginas seleccionados {#distribution-of-traffic}

Puede elegir entre uno y los tres conjuntos de la pestaña **Pruebas** de su [configuración de canalización](/help/using/production-pipelines.md). La distribución del tráfico se basa en el número de conjuntos seleccionados. Es decir, si se escogen los tres, se destinará a cada conjunto el 33 % del total de vistas de página. Si se seleccionan dos, va el 50 % a cada conjunto. Si se selecciona uno, el 100 % del tráfico se destina a ese conjunto.

Consideremos este ejemplo.

* Hay una división 50/50 entre las páginas en directo más populares y los conjuntos de páginas nuevas.
* Otras páginas activas no se utilizan.
* El conjunto de páginas nuevas contiene 3000 páginas.
* El KPI de *vistas de página por minuto* se establece en 200.

Durante el período de prueba de 30 minutos, sucede lo siguiente:

* Cada una de las 25 páginas del conjunto de páginas populares activas se ha visitado 120 veces: `((200 * 0.5) / 25) * 30 = 120`
* Cada una de las 3000 páginas del conjunto de páginas nuevas se ha visitado una vez: `((200 * 0.5) / 3000) * 30 = 1`

#### Prueba e informe {#testing-reporting}

Cloud Manager ejecuta pruebas de rendimiento para programas de AEM Sites solicitando páginas como un usuario no autenticado de forma predeterminada en el servidor de publicación de ensayo durante un período de prueba de 30 minutos. Mide las métricas generadas por el usuario virtual (tiempo de respuesta, tasa de errores, vistas por minuto, etc.) para cada página, así como varias métricas de nivel de sistema (CPU, memoria, datos de red) para todas las instancias.

En la tabla siguiente se resume la matriz de prueba de rendimiento utilizando el sistema de acceso de tres niveles.

| Métrica | Categoría | Umbral de error |
|---|---|---|
| Tasa de error de solicitud de página | Esencial | >= 2% |
| Tasa de uso de CPU | Esencial | >= 80% |
| Tiempo de espera de IO de disco | Esencial | >= 50% |
| Tiempo de respuesta del percentil 95 | Importante | >= KPI de nivel de programa |
| Tiempo de respuesta máximo | Importante | >= 18 segundos |
| Vistas de página por minuto | Importante | &lt; KPI de nivel de programa |
| Utilización del ancho de banda del disco | Importante | >= 90% |
| Utilización del ancho de banda de red | Importante | >= 90% |
| Solicitudes por minuto | Información | >= 6000 |

Consulte la sección [Pruebas de rendimiento autenticadas](#authenticated-performance-testing) para obtener más información sobre el uso de la autenticación básica para las pruebas de rendimiento de Sites y Assets.

>[!NOTE]
>
>Las instancias de autor y publicación se supervisan durante la prueba. Si no se obtiene ninguna métrica para una instancia, esa métrica se comunica como desconocida y el paso correspondiente falla.

#### Pruebas de rendimiento autenticadas {#authenticated-performance-testing}

Si es necesario, los clientes de AMS con sitios autenticados pueden especificar un nombre de usuario y una contraseña que Cloud Manager utilizará para acceder al sitio web durante las pruebas de rendimiento de los sitios.

El nombre de usuario y la contraseña se especifican como variables de canalización con los nombres `CM_PERF_TEST_BASIC_USERNAME` y `CM_PERF_TEST_BASIC_PASSWORD`.

El nombre de usuario debe almacenarse en una variable `string` y la contraseña debe almacenarse en una variable `secretString`. Si se especifican estas dos variables, cada solicitud del rastreador de prueba de rendimiento y de los usuarios virtuales de prueba contendrá estas credenciales como autenticación básica de HTTP.

Para establecer estas variables utilizando la CLI de Cloud Manager, ejecute lo siguiente:

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

Consulte la documentación de API de [Variables de canalización de usuarios de parches](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchPipelineVariables) para aprender a utilizar la API.

### AEM Assets {#aem-assets}

Cloud Manager ejecuta pruebas de rendimiento para programas de AEM Assets cargando recursos repetidamente durante 30 minutos.

#### Requisito de incorporación {#onboarding-requirement}

Para las pruebas de rendimiento de Assets, el ingeniero de éxito del cliente creará un usuario y contraseña de `cloudmanager` durante la incorporación del autor al entorno de ensayo. Los pasos de la prueba de rendimiento requieren un usuario llamado `cloudmanager` y la contraseña asociada configurada por su CSE.

Este método debe permanecer en la instancia de autor con sus permisos inalterados. Su modificación o eliminación puede provocar errores en las pruebas de rendimiento de Assets.

#### Imágenes y recursos para pruebas {#assets-for-testing}

Los clientes pueden cargar sus propios recursos para realizar pruebas. Esto se puede hacer desde la pantalla **Configuración de canalización** o **Editar**. Los formatos de imagen frecuentes, como JPEG, PNG, GIF y BMP, son compatibles con los archivos Photoshop, Illustrator y Postscript.

Si no se carga ninguna imagen, Cloud Manager utiliza una imagen predeterminada y documentos de PDF para realizar las pruebas.

#### Distribución de recursos para pruebas {#distribution-of-assets}

La distribución de cuántos recursos de cada tipo se cargan por minuto se establece en la pantalla **Configuración de canalización** o **Editar**.

Por ejemplo, si se utiliza una división 70/30 y se cargan 10 activos por minuto, se cargarán siete imágenes y tres documentos por minuto.

#### Prueba e informe {#testing-and-reporting}

Cloud Manager crea una carpeta en la instancia de autor utilizando el nombre de usuario y la contraseña según la configuración del CSE. A continuación, los recursos se cargan en la carpeta mediante una biblioteca de código abierto. Las pruebas ejecutadas por el paso de prueba de Assets se escriben mediante una [biblioteca de código abierto](https://github.com/adobe/toughday2). Tanto el tiempo de procesamiento de cada recurso como diversas métricas de nivel de sistema se miden en la duración de las pruebas de 30 minutos. Esta función puede cargar imágenes y documentos de PDF.

>[!TIP]
>
>Consulte [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) para obtener más información. Consulte [Configuración del programa](/help/getting-started/program-setup.md) para obtener información sobre cómo configurar el programa y definir los KPI.

### Gráficos de resultados de pruebas de rendimiento {#performance-testing-results-graphs}

Hay varias métricas disponibles en el **Cuadro de diálogo Prueba de rendimiento**.

![Lista de métricas](/help/assets/understand_test-results-screen1.png)

Los paneles de métricas se pueden expandir para mostrar un gráfico, proporcionar un vínculo a una descarga o ambos.

![Métricas expandidas como un gráfico](/help/assets/screen_shot_2018-09-05at83933pm.png)

Esta funcionalidad está disponible para las siguientes métricas.

* **Utilización de CPU**: un gráfico de la utilización de la CPU durante el período de prueba

* **Tiempo de espera de E/S de disco**: un gráfico de tiempo de espera de E/S de disco durante el período de prueba

* **Tasa de error de página**: un gráfico de errores de página por minuto durante el período de prueba
   * Un archivo CSV que enumera las páginas que han producido un error durante la prueba

* **Utilización del ancho de banda del disco**: un gráfico de la utilización del ancho de banda del disco durante el período de prueba

* **Utilización del ancho de banda de red**: un gráfico de la utilización del ancho de banda de la red durante el período de prueba

* **Tiempo de respuesta máximo**: un gráfico del tiempo de respuesta máximo por minuto durante el período de prueba

* **Tiempo de respuesta del percentil 95**: gráfico del tiempo de respuesta del percentil 95 por minuto durante el período de prueba
   * Un archivo CSV que enumera las páginas cuyo tiempo de respuesta del percentil 95 ha superado el KPI definido

## Optimización del análisis de paquetes de contenido {#content-package-scanning-optimization}

Como parte del proceso de análisis de calidad, Cloud Manager realiza un análisis de los paquetes de contenido producidos por la compilación de Maven. Cloud Manager ofrece optimizaciones para acelerar este proceso, que son efectivas cuando se observan ciertas restricciones de empaquetado.

La optimización clave es para proyectos que generan un solo paquete «todo», que contiene otros paquetes de contenido producidos por la compilación, que se marcan como omitidos. Cuando Cloud Manager detecta este escenario, en lugar de desempaquetar el paquete “todo”, los paquetes de contenido individuales se analizan directamente y se ordenan según las dependencias. Por ejemplo, considere la siguiente salida de compilación.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (skipped-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (skipped-content-package)

Si los únicos elementos dentro de `myco-all-1.0.0-SNAPSHOT.zip` son los dos paquetes de contenido omitidos, entonces los dos paquetes incrustados se analizarán en lugar del paquete de contenido “todo”.

Para los proyectos que producen decenas de paquetes incrustados, se ha demostrado que esta optimización ahorra más de 10 minutos por ejecución de canalización.

Se puede producir un caso especial cuando el paquete de contenido “todo” contiene una combinación de paquetes de contenido omitidos y paquetes OSGi. Por ejemplo, si `myco-all-1.0.0-SNAPSHOT.zip` contenía los dos paquetes incrustados mencionados anteriormente, así como uno o más paquetes OSGi, entonces se construye un nuevo paquete de contenido mínimo con solo los paquetes OSGi. Este paquete siempre tiene el nombre `cloudmanager-synthetic-jar-package`, y los paquetes contenidos se colocan en `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
>
>* Esta optimización no afecta a los paquetes que se implementan en AEM.
>* La coincidencia entre paquetes de contenido incrustado y omitido se basa en los nombres de archivo. Esta optimización falla si varios paquetes de contenido omitidos comparten el mismo nombre de archivo o si el nombre de archivo cambia durante la incrustación.
