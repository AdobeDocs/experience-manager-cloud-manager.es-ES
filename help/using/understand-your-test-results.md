---
title: Comprender los resultados de la prueba
description: Descubra cómo funcionan las pruebas de calidad del código de las canalizaciones y cómo pueden mejorar la calidad de las implementaciones.
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4
feature: CI-CD Pipeline, Test Results
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: bfcb0fb5b9cf8317eb75e3b7b46455b14cd9d7b7
workflow-type: tm+mt
source-wordcount: '2896'
ht-degree: 3%

---

# Comprender los resultados de la prueba {#understand-your-test-results}

Descubra cómo funcionan las pruebas de calidad del código de las canalizaciones y cómo pueden mejorar la calidad de las implementaciones.

## Introducción {#introduction}

Durante la ejecución de la canalización, se capturan varias métricas que se comparan con los indicadores de rendimiento clave (KPI) definidos por el propietario del negocio o con los estándares establecidos por Adobe Managed Services.

Estos se informan utilizando un sistema de clasificación de tres niveles como se define en la siguiente sección

>[!NOTE]
>
>Para obtener más información sobre las pruebas admitidas por Cloud Manager para AEM as a Cloud Service, consulte la [AEM documentación as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/test-results/overview-test-results.html).


## Clasificaciones en tres niveles  {#three-tier-gates-while-running-a-pipeline}

Hay tres puertas en la canalización:

* Calidad de código
* Pruebas de rendimiento
* Pruebas de seguridad

Para cada una de estas puertas, hay una estructura de tres niveles para los problemas identificados por la puerta.

* **Importante** - Estos son problemas que causan un fallo inmediato de la canalización.
* **Importante** - Estos son problemas que hacen que la canalización introduzca un estado pausado. Un administrador de implementación, un administrador de proyectos o un propietario de empresa pueden anular los problemas, en cuyo caso la canalización continúa, o pueden aceptar los problemas, en cuyo caso la canalización se detiene con un error. La anulación de errores importantes está sujeta a una [tiempo de espera.](deploying-code.md#timeouts)
* **Información** - Se trata de problemas que se proporcionan exclusivamente con fines informativos y que no afectan a la ejecución de la canalización.

>[!NOTE]
>
>En una canalización de solo calidad de código, no se pueden anular los errores importantes en la puerta de calidad de código, ya que el paso de prueba de calidad de código es el último paso de la canalización.

## Prueba de calidad del código {#code-quality-testing}

Este paso evalúa la calidad del código de la aplicación, que es el propósito principal de una canalización de solo calidad de código, y se ejecuta inmediatamente después del paso de compilación en todas las canalizaciones que no sean de producción y producción. Consulte el documento [Configuración de canalizaciones que no sean de producción](configuring-non-production-pipelines.md) para obtener más información.

### Explicación de las pruebas de calidad de código {#understanding-code-quality-testing}

Las pruebas de calidad del código analizan el código fuente para asegurarse de que cumple determinados criterios de calidad. Esto se implementa mediante una combinación de análisis de SonarQube, examen de nivel de paquete de contenido mediante OakPAL y validación de Dispatcher mediante la herramienta de optimización de Dispatcher.

Hay más de 100 reglas que combinan reglas genéricas de Java y reglas específicas de AEM. Algunas de las reglas específicas del AEM se crean en función de las prácticas recomendadas de AEM Engineering y se denominan [Reglas de calidad de código personalizadas.](/help/using/custom-code-quality-rules.md)

>[!NOTE]
>
>Puede descargar la lista completa de reglas [mediante este vínculo.](/help/using/assets/CodeQuality-rules-latest-AMS.xlsx)

Los resultados de las pruebas de calidad del código se entregan como **clasificaciones**. En la tabla siguiente se resumen las clasificaciones de diversos criterios de prueba.

| Nombre | Definición | Categoría | Umbral de error |
|--- |--- |--- |--- |
| Clasificación de seguridad | A = Sin vulnerabilidades<br/>B = Al menos 1 vulnerabilidad menor<br/>C = Al menos 1 vulnerabilidad importante<br/>D = Al menos 1 vulnerabilidad crítica<br/>E = Al menos 1 vulnerabilidad de bloqueo | Importante | &lt; B |
| Clasificación de fiabilidad | A = No hay errores<br/>B = Al menos 1 error menor <br/>C = Al menos 1 error mayor<br/>D = Al menos 1 error crítico<br/>E = Al menos un error de bloqueo | Importante | &lt; C |
| Puntuación de mantenimiento | Definido por el coste de corrección pendiente de los olores de código como un porcentaje del tiempo que ya ha pasado a la aplicación<br/><ul><li>A = &lt;=5%</li><li>B = 6-10 %</li><li>C = 11-20 %</li><li>D = 21-50%</li><li>E = >50%</li></ul> | Importante | &lt; A |
| Cobertura | Definido por una combinación de cobertura de línea de prueba unitaria y cobertura de condición mediante la fórmula: <br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` = Condiciones que se han evaluado como `true` al menos una vez al ejecutar las pruebas unitarias</li><li>`CF` = Condiciones que se han evaluado como `false` al menos una vez al ejecutar las pruebas unitarias</li><li>`LC` = Líneas cubiertas = líneas_to_cover - uncovered_lines</li><li>`B` = número total de condiciones</li><li>`EL` = número total de líneas ejecutables (lines_to_cover)</li></ul> | Importante | &lt; 50% |
| Pruebas unitarias omitidas | Número de pruebas unitarias omitidas | Información | > 1 |
| Problemas abiertos | Tipos de problemas generales: Vulnerabilidades, errores y huecos de código | Información | > 0 |
| Líneas duplicadas | Se define como el número de líneas involucradas en bloques duplicados. Un bloque de código se considera duplicado en las siguientes condiciones.<br>Proyectos que no son de Java:<ul><li>Debe haber al menos 100 tokens sucesivos y duplicados.</li><li>Estos tokens deben propagarse por lo menos: </li><li>30 líneas de código para COBOL </li><li>20 líneas de código para ABAP </li><li>10 líneas de código para otros idiomas</li></ul>Proyectos Java:<ul></li><li> Debe haber al menos 10 instrucciones sucesivas y duplicadas, independientemente del número de tokens y líneas.</li></ul>Las diferencias en la sangría y en los literales de cadena se ignoran al detectar duplicados. | Información | > 1% |
| Compatibilidad del Cloud Service | Número de problemas de compatibilidad con Cloud Service identificados | Información | > 0 |

>[!NOTE]
>
>Consulte [Definiciones de métricas de SonarQube](https://docs.sonarqube.org/latest/user-guide/metric-definitions/) para obtener información más detallada.

>[!NOTE]
>
>Para obtener más información sobre las reglas de calidad de código personalizadas ejecutadas por [!UICONTROL Cloud Manager], consulte el documento [Reglas de calidad de código personalizadas.](custom-code-quality-rules.md)

### Cómo tratar con falsos positivos {#dealing-with-false-positives}

El proceso de digitalización de la calidad no es perfecto y a veces identifica incorrectamente los problemas que no son realmente problemáticos. Esto se conoce como **falso positivo**.

En estos casos, el código fuente se puede anotar con el Java estándar `@SuppressWarnings` anotación que especifica el ID de regla como atributo de anotación. Por ejemplo, un falso positivo común es que la regla SonarQube para detectar contraseñas codificadas puede ser agresiva sobre cómo se identifica una contraseña codificada.

El siguiente código es bastante común en un proyecto AEM, que tiene código para conectarse a algún servicio externo.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube generará una vulnerabilidad de bloqueo. Pero después de revisar el código, reconoce que no se trata de una vulnerabilidad y puede anotar el código con el ID de regla adecuado.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Sin embargo, si el código era realmente así:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

A continuación, la solución correcta es quitar la contraseña codificada.

>[!NOTE]
>
>Aunque es recomendable hacer que la variable `@SuppressWarnings` anotación lo más específica posible, es decir, anotar solo la declaración o el bloque específico que causa el problema; es posible realizar anotaciones a nivel de clase.

## Pruebas de seguridad {#security-testing}

[!UICONTROL Cloud Manager] ejecuta el **Comprobaciones de AEM de seguridad** en el entorno de ensayo después de la implementación e informa del estado a través de la interfaz de usuario. Los resultados se agregan de todas las instancias AEM del entorno.

Estas mismas comprobaciones de estado se pueden ejecutar en cualquier momento a través de la consola web o el panel de operaciones.

Si alguno de los casos indica un error en una comprobación de estado determinada, todo el entorno falla en esa comprobación de estado. Al igual que con las pruebas de calidad y rendimiento del código, estas comprobaciones de estado se organizan en categorías y se comunican utilizando el sistema de enlace de tres niveles. La única distinción es que no hay umbral en el caso de las pruebas de seguridad. Todos los controles de salud se aprueban o no.

La siguiente tabla enumera las comprobaciones de estado.

| Nombre | Implementación de comprobación de estado | Categoría |
|---|---|---|
| Deserialización firewall Adjuntar preparación de API está en un estado aceptable. | [Disposición de la API de anexo de cortafuegos de deserialización](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | Importante |
| El firewall de deserialización funciona. | [Cortafuegos de deserialización funcional](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | Importante |
| Se ha cargado el cortafuegos de deserialización. | [Cortafuegos de deserialización cargado](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | Importante |
| `AuthorizableNodeName` la implementación no expone el ID autorizado en el nombre/ruta del nodo. | [Generación del nombre de nodo con autorización](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#security) | Importante |
| Se han cambiado las contraseñas predeterminadas. | [Cuentas de inicio de sesión predet.](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html#users-and-groups-in-aem) | Importante |
| El servlet de GET predeterminado de Sling está protegido de ataques DOS. | Sling Get Servlet | Importante |
| El controlador de script Java de Sling está configurado correctamente. | Sling Java Script Handler | Importante |
| El controlador de script JSP de Sling está configurado correctamente. | Controlador de script JSP de Sling | Importante |
| SSL está configurado correctamente. | Configuración SSL | Importante |
| Obviamente, no se encuentran políticas de perfil de usuario inseguras. | Acceso predet. del perfil de usuario | Importante |
| El filtro Referente de Sling está configurado para evitar ataques de CSRF. | [Filtro de referente de Sling](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#security) | Importante |
| El Administrador de biblioteca de HTML de Adobe Granite está configurado correctamente. | Configuración del administrador de bibliotecas HTML de CQ | Importante |
| El paquete de soporte CRXDE está deshabilitado. | Compatibilidad con CRXDE | Importante |
| El paquete Sling DavEx y el servlet están desactivados. | Comprobación de estado de DavEx | Importante |
| El contenido de muestra no está instalado. | Paquetes de contenido de ejemplo | Importante |
| Tanto el filtro de solicitud WCM como el filtro de depuración WCM están desactivados. | [Configuración de filtros WCM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html#configuring) | Importante |
| El paquete y el servlet Sling WebDAV están correctamente configurados. | Comprobación de estado de WebDAV | Importante |
| El servidor web está configurado para evitar el secuestro de clics. | Configuración de servidor web | Importante |
| La replicación no utiliza la variable `admin` usuario. | Replicación y usuarios de transporte | Información |

## Pruebas de rendimiento {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager ejecuta pruebas de rendimiento para programas de AEM Sites. La prueba de rendimiento se ejecuta durante aproximadamente 30 minutos girando los usuarios virtuales (contenedores) que simulan que los usuarios reales acceden a páginas en entornos de ensayo para simular tráfico. Estas páginas se encuentran usando un rastreador.

#### Usuarios virtuales {#virtual-users}

El número de usuarios virtuales o contenedores que Cloud Manager genera depende de los KPI (tiempo de respuesta y vistas de página/min) definidos por el usuario con la variable **Propietario empresarial** función durante [crear o editar el programa.](setting-up-program.md) Según los KPI definidos, se enviarán hasta 10 contenedores que simulen usuarios reales. Las páginas seleccionadas para la prueba se dividen y se asignan a cada usuario virtual.

#### Rastreador {#crawler}

Antes del inicio del periodo de prueba de 30 minutos, Cloud Manager rastreará el entorno de ensayo utilizando un conjunto de una o más URL semilla configuradas por el ingeniero de éxito del cliente. A partir de estas direcciones URL, el HTML de cada página se inspecciona y los vínculos se atraviesan de forma predeterminada. Este proceso de rastreo está limitado a un máximo de 5000 páginas. Las solicitudes del rastreador tienen un tiempo de espera fijo de 10 segundos.

#### Conjuntos de páginas para pruebas {#page-sets}

Las páginas se seleccionan mediante tres conjuntos de páginas. Cloud Manager utiliza los registros de acceso de las instancias de AEM en los entornos de producción y ensayo para determinar los siguientes bloques.

* **Páginas Live populares** : esta opción está seleccionada para asegurarse de que se prueben las páginas más populares a las que acceden los clientes activos. Cloud Manager leerá el registro de acceso y determinará las 25 páginas más visitadas por los clientes activos para generar una lista de las principales `Popular Live Pages`. La intersección de estas que también están presentes en el entorno de ensayo se rastrea en el entorno de ensayo.

* **Otras páginas Live** : esta opción está seleccionada para asegurarse de que se prueben las páginas que no están dentro de las 25 páginas activas más populares y que pueden no ser populares, pero que son importantes para probarlas. De forma similar a las páginas en directo más populares, se extraen del registro de acceso y también deben estar presentes en el entorno de ensayo.

* **Nuevas páginas** : esta opción está seleccionada para probar las páginas nuevas que pueden haber sido implementadas únicamente en el entorno de ensayo y que aún no están en producción, pero que deben probarse.

##### Distribución del tráfico entre conjuntos de páginas seleccionados {#distribution-of-traffic}

Puede elegir entre uno y los tres conjuntos del **Pruebas** de su [configuración de canalización.](configuring-production-pipelines.md) La distribución del tráfico se basa en el número de conjuntos seleccionados. Es decir, si se seleccionan las tres, el 33 % del total de vistas de página se destinará a cada conjunto. Si se seleccionan dos, el 50 % va a cada conjunto. Si se selecciona uno, el 100 % del tráfico se destina a ese conjunto.

Consideremos este ejemplo.

* Hay una división 50/50 entre las páginas en directo más populares y los conjuntos de páginas nuevas.
* No se utilizan otras páginas activas.
* El nuevo conjunto de páginas contiene 3000 páginas.
* El KPI de vistas de página por minuto se establece en 200.

Durante el periodo de prueba de 30 minutos:

* Cada una de las 25 páginas del conjunto de páginas en directo más popular se visita 120 veces: `((200 * 0.5) / 25) * 30 = 120`
* Cada una de las 3000 páginas del nuevo conjunto de páginas se visita una vez: `((200 * 0.5) / 3000) * 30 = 1`

#### Pruebas e informes {#testing-reporting}

Cloud Manager ejecuta pruebas de rendimiento para programas de AEM Sites solicitando páginas como usuario no autenticado de forma predeterminada en el servidor de publicación de ensayo durante un periodo de prueba de 30 minutos. Mide las métricas generadas por el usuario virtual (tiempo de respuesta, tasa de error, vistas por minuto, etc.) para cada página, así como varias métricas de nivel de sistema (CPU, memoria, datos de red) para todas las instancias.

En la tabla siguiente se resume la matriz de prueba de rendimiento utilizando el sistema de enlace de tres niveles.

| Métrica | Categoría | Umbral de error |
|---|---|---|
| Tasa de error de solicitud de página | Importante | >= 2% |
| Tasa de uso de CPU | Importante | >= 80 % |
| Tiempo de espera de IO de disco | Importante | >= 50% |
| Tiempo de respuesta del percentil 95 | Importante | >= KPI a nivel de programa |
| Tiempo de respuesta máximo | Importante | >= 18 segundos |
| Vistas de página por minuto | Importante | &lt; KPI de nivel de programa |
| Uso del ancho de banda del disco | Importante | >= 90% |
| Utilización del ancho de banda de red | Importante | >= 90 % |
| Solicitudes por minuto | Información | >= 6000 |

Consulte la sección [Pruebas de rendimiento autenticadas](#authenticated-performance-testing) para obtener más información sobre el uso de la autenticación básica para las pruebas de rendimiento de Sites y Assets.

>[!NOTE]
>
>Las instancias de autor y publicación se supervisan durante el periodo de la prueba. Si no se obtiene ninguna métrica para una instancia, esa métrica se comunica como desconocida y el paso correspondiente falla.

#### Opcional: Pruebas de rendimiento autenticadas {#authenticated-performance-testing}

Si es necesario, los clientes de AMS con sitios autenticados pueden especificar un nombre de usuario y una contraseña que Cloud Manager utilizará para acceder al sitio web durante las pruebas de rendimiento del sitio.

El nombre de usuario y la contraseña se especifican como variables de canalización con los nombres `CM_PERF_TEST_BASIC_USERNAME` y `CM_PERF_TEST_BASIC_PASSWORD`.

El nombre de usuario debe almacenarse en un `string` y la contraseña deben almacenarse en un `secretString` variable. Si se especifican ambos, cada solicitud del rastreador de prueba de rendimiento y los usuarios virtuales de prueba contendrán estas credenciales como autenticación HTTP Basic.

Para establecer estas variables utilizando la CLI de Cloud Manager, ejecute:

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

Consulte el documento [Parche de variables de canalización de usuarios](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Variables/patchPipelineVariables) para aprender a utilizar la API de .

### AEM Assets {#aem-assets}

Cloud Manager ejecuta pruebas de rendimiento para programas de AEM Assets cargando recursos repetidamente durante un periodo de prueba de 30 minutos.

#### Requisito de integración {#onboarding-requirement}

Para las pruebas de rendimiento de Assets, el ingeniero de éxito del cliente creará un `cloudmanager` usuario y contraseña durante la incorporación del autor al entorno de ensayo. Los pasos de la prueba de rendimiento requieren un usuario llamado `cloudmanager` y la contraseña asociada configurada por su CSE. Esto no se debe eliminar de la instancia de autor ni cambiar sus permisos. Si lo hace, es probable que se produzca un error en las pruebas de rendimiento de Assets.

#### Imágenes y recursos para pruebas {#assets-for-testing}

Los clientes pueden cargar sus propios recursos para realizar pruebas. Esto se puede hacer desde el **Configuración de canalización** o **Editar** en el Navegador. Los formatos de imagen comunes, como JPEG, PNG, GIF y BMP, son compatibles con los archivos Photoshop, Illustrator y Postscript.

Si no se carga ninguna imagen, Cloud Manager utilizará una imagen predeterminada y documentos de PDF para realizar pruebas.

#### Distribución de recursos para pruebas {#distribution-of-assets}

La distribución de cuántos recursos de cada tipo se cargan por minuto se establece en la variable **Configuración de canalización** o **Editar** en el Navegador.

Por ejemplo, si se utiliza una división 70/30 y hay 10 activos cargados por minuto, se cargarán 7 imágenes y 3 documentos por minuto.

#### Pruebas e informes {#testing-and-reporting}

Cloud Manager creará una carpeta en la instancia de autor utilizando el nombre de usuario y la contraseña según la configuración del CSE en la variable [Requisitos de integración](#onboaring-requirements) para obtener más información. A continuación, los recursos se cargan en la carpeta mediante una biblioteca de código abierto. Las pruebas ejecutadas por el paso de prueba de Assets se escriben mediante una [biblioteca de código abierto.](https://github.com/adobe/toughday2) Tanto el tiempo de procesamiento de cada recurso como varias métricas a nivel de sistema se miden en la duración de las pruebas de 30 minutos. Esta función puede cargar imágenes y documentos de PDF.

>[!TIP]
>
>Consulte el documento [Configurar canalizaciones de producción](configuring-production-pipelines.md) para obtener más información. Consulte el documento [Configurar el programa](setting-up-program.md) para aprender a configurar el programa y definir los KPI.

### Gráficos de resultados de pruebas de rendimiento {#performance-testing-results-graphs}

Hay varias métricas disponibles en la **Cuadro de diálogo Prueba de rendimiento**

![Lista de métricas](assets/understand_test-results-screen1.png)

Los paneles de métricas se pueden expandir para mostrar un gráfico, proporcionar un vínculo a una descarga o ambos.

![Métricas expandidas como un gráfico](assets/screen_shot_2018-09-05at83933pm.png)

Esta funcionalidad está disponible para las siguientes métricas.

* **Uso de CPU**
   * Un gráfico de la utilización de la CPU durante el período de prueba

* **Tiempo de espera de E/S de disco**
   * Un gráfico del tiempo de espera de E/S de disco durante el periodo de prueba

* **Tasa de error de página**
   * Un gráfico de errores de página por minuto durante el periodo de prueba
   * Un archivo CSV que enumera las páginas que han producido un error durante la prueba

* **Uso del ancho de banda del disco**
   * Un gráfico de la utilización del ancho de banda del disco durante el período de prueba

* **Utilización del ancho de banda de red**
   * Un gráfico de la utilización del ancho de banda de la red durante el período de prueba

* **Tiempo de respuesta máximo**
   * Un gráfico del tiempo de respuesta máximo por minuto durante el periodo de prueba

* **Tiempo de respuesta del percentil 95**
   * Un gráfico del tiempo de respuesta del percentil 95 por minuto durante el periodo de prueba
   * Un archivo CSV que enumera páginas cuyo tiempo de respuesta del percentil 95 ha superado el KPI definido

## Optimización del análisis de paquetes de contenido {#content-package-scanning-optimization}

Como parte del proceso de análisis de calidad, Cloud Manager realiza un análisis de los paquetes de contenido producidos por la compilación de Maven. Cloud Manager ofrece optimizaciones para acelerar este proceso, que son efectivas cuando se observan ciertas restricciones de empaquetado. Lo más significativo es la optimización realizada para proyectos que generan un paquete de contenido único, generalmente denominado paquete &quot;todo&quot;, que contiene otros paquetes de contenido producidos por la compilación, que se marcan como omitidos. Cuando Cloud Manager detecta este escenario, en lugar de desempaquetar el paquete &quot;todo&quot;, los paquetes de contenido individuales se analizan directamente y se ordenan según las dependencias. Por ejemplo, considere la siguiente salida de compilación.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (skipped-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (skipped-content-package)

Si los únicos elementos dentro de `myco-all-1.0.0-SNAPSHOT.zip` son los dos paquetes de contenido omitidos, entonces los dos paquetes incrustados se analizarán en lugar del paquete de contenido &quot;todo&quot;.

Para los proyectos que producen decenas de paquetes incrustados, se ha demostrado que esta optimización ahorra más de 10 minutos por ejecución de canalización.

Se puede producir un caso especial cuando el paquete de contenido &quot;todo&quot; contiene una combinación de paquetes de contenido omitidos y paquetes OSGi. Por ejemplo, si `myco-all-1.0.0-SNAPSHOT.zip` contenía los dos paquetes incrustados mencionados anteriormente, así como uno o más paquetes OSGi, luego se construye un nuevo paquete de contenido mínimo con solo los paquetes OSGi. Este paquete siempre tiene el nombre `cloudmanager-synthetic-jar-package` y los paquetes contenidos se colocan en `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
>
>* Esta optimización no afecta a los paquetes que se implementan en AEM.
>* Debido a que la coincidencia entre los paquetes de contenido incrustado y los paquetes de contenido omitido se basa en los nombres de archivo, esta optimización no se puede realizar si varios paquetes de contenido omitidos tienen exactamente el mismo nombre de archivo o si el nombre de archivo se cambia al incrustar.

