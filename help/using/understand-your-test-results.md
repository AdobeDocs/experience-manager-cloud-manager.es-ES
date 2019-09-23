---
title: Comprender los resultados de la prueba
seo-title: Comprender los resultados de la prueba
description: nulo
seo-description: Siga esta página para obtener información sobre tres puertas de nivel mientras ejecuta una canalización, análisis de código, rendimiento y pruebas de seguridad que validan el programa en Cloud Manager.
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4
translation-type: tm+mt
source-git-commit: 26014cfabfee6226033ba2fc1167d8f5509e17c6

---


# Comprender los resultados de la prueba {#understand-your-test-results}

Durante el proceso de **canalización** , se capturan varias métricas y se comparan con los Indicadores de rendimiento clave (KPI) definidos por el propietario del negocio o con los estándares establecidos por Adobe Managed Services.

Estos informes se registran utilizando el sistema de enlace de tres niveles definido en esta sección.

## Puerta de tres niveles mientras se ejecuta una canalización {#three-tier-gates-while-running-a-pipeline}

Hay tres puertas en el oleoducto:

* Calidad del código
* Prueba de rendimiento
* Pruebas de seguridad

Para cada una de estas puertas, existe una estructura de tres niveles para los problemas identificados por la puerta.

* **Crítico** : Estos son problemas identificados por la puerta que causan un fallo inmediato en la tubería.
* **Importante** : Son problemas identificados por la puerta que hacen que la tubería entre en estado de pausa. Un administrador de implementación, un jefe de proyecto o un propietario de empresa pueden anular los problemas, en cuyo caso la canalización continúa, o pueden aceptar los problemas, en cuyo caso la canalización se detiene con un error.
* **Información** : Son problemas identificados por la puerta que se proporcionan exclusivamente con fines informativos y que no tienen impacto en la ejecución de la tubería.

>[!NOTE]
>
>En una canalización de sólo calidad de código, no se pueden anular los errores importantes en la puerta de comprobación de calidad de código, ya que el paso Prueba de calidad de código es el último paso de la canalización.

## Prueba de calidad del código {#code-quality-testing}

Como parte de la canalización, se analiza el código fuente para asegurarse de que las implementaciones cumplen determinados criterios de calidad. Actualmente, esto se implementa mediante una combinación de SonarQube y un examen a nivel de paquete de contenido con OakPAL. Existen más de 100 reglas que combinan reglas genéricas de Java y reglas específicas de AEM. La siguiente tabla resume la clasificación para los criterios de prueba:

| Nombre | Definición | Categoría | Umbral de error |
|--- |--- |--- |--- |
| Clasificación de seguridad | A = 0 Vulnerabilidad <br/>B = al menos 1 vulnerabilidad<br/> menor C = al menos 1 vulnerabilidad grave <br/>D = al menos 1 vulnerabilidad crítica <br/>E = al menos 1 vulnerabilidad de bloqueador |  Crítico | &lt; B |
| Clasificación de confiabilidad | A = 0 Error <br/>B = al menos 1 Error menor <br/>C = al menos 1 Error mayor <br/>D = al menos 1 Error crítico E = al menos 1 Error de bloqueo | Importante | &lt; C |
| Clasificación de mantenimiento | El costo de corrección sobresaliente de los olores de código es: <br/><ul><li>&lt;=5% del tiempo que ya ha pasado a la aplicación, la clasificación es A </li><li>entre el 6 y el 10 % la calificación es B </li><li>entre el 11 y el 20 % la calificación es una C </li><li>entre el 21 y el 50 % la calificación es una D</li><li>cualquier cosa superior al 50% es una E</li></ul> | Importante | &lt; A |
| Cobertura | Combinación de cobertura de la línea de prueba unitaria y cobertura de condición mediante esta fórmula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)` <br/>donde: CT = condiciones que se han evaluado en 'true' al menos una vez mientras se ejecutan las pruebas unitarias <br/>CF = condiciones que se han evaluado en 'false' al menos una vez mientras se ejecutan las pruebas unitarias <br/>LC = líneas cubiertas = líneas_to_cover - líneasdescubiertas <br/><br/> B = número total de condiciones <br/>EL = número total de líneas ejecutables (lines_to_cover) | Importante | &lt; 50% |
| Pruebas unitarias omitidas | Número de pruebas unitarias omitidas. | Información | &gt; 1 |
| Problemas abiertos | Tipos de problemas generales: Vulnerabilidades, errores y huecos de código | Información | &gt; 1 |
| Líneas duplicadas | Número de líneas involucradas en bloques duplicados. <br/>Para que un bloque de código se considere como duplicado: <br/><ul><li>**Proyectos que no son de Java:**</li><li>Debe haber al menos 100 tokens sucesivos y duplicados.</li><li>Estos tokens deben propagarse al menos en: </li><li>30 líneas de código para COBOL </li><li>20 líneas de código para ABAP </li><li>10 líneas de código para otros idiomas</li><li>**Proyectos de Java:**</li><li> Debe haber al menos 10 declaraciones sucesivas y duplicadas, independientemente del número de tokens y líneas.</li></ul> <br/>Las diferencias en sangría y en literales de cadena se omiten al detectar duplicaciones. | Información | &gt; 1% |


>[!NOTE]
>
>Consulte Definiciones [de métricas](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) para obtener definiciones más detalladas.

Puede descargar la lista de reglas aquí [code-quality-rules.xlsx](/help/using/assets/CodeQuality-Rules-new.xlsx)

>[!NOTE]
>
>Para obtener más información sobre las reglas de calidad de código personalizadas ejecutadas por [!UICONTROL Cloud Manager], consulte Reglas [de calidad de código](custom-code-quality-rules.md)personalizado.

### Tratar con falsos positivos {#dealing-with-false-positives}

El proceso de análisis de calidad no es perfecto y a veces identifica incorrectamente problemas que no son realmente problemáticos. Esto se denomina "falso positivo".

En estos casos, el código fuente se puede anotar con la anotación estándar de Java `@SuppressWarnings` que especifica el ID de la regla como el atributo de anotación. Por ejemplo, un problema común es que la regla SonarQube para detectar contraseñas codificadas puede ser agresiva sobre cómo se identifica una contraseña codificada.

Para ver un ejemplo específico, este código sería bastante común en un proyecto de AEM que tiene código para conectarse a algún servicio externo:

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube generará una vulnerabilidad de bloqueador. Después de revisar el código, se identifica que no se trata de una vulnerabilidad y se puede anotar con la identificación de regla adecuada.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Sin embargo, por otro lado, si el código era en realidad esto:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

A continuación, la solución correcta es quitar la contraseña codificada.

>[!NOTE]
>
>Si bien es recomendable que la anotación sea lo más específica posible, es decir, que solo haga una anotación de la sentencia o bloque específico que causa el problema, es posible realizar anotaciones a nivel de clase. `@SuppressWarnings`

## Pruebas de seguridad {#security-testing}

[!UICONTROL Cloud Manager] ejecuta las comprobaciones ***de estado de seguridad de*** AEM existentes en el escenario después de la implementación e informa del estado a través de la interfaz de usuario. Los resultados se agregan de todas las instancias de AEM en el entorno.

Si alguna de las **instancias** indica un error en una comprobación de estado determinada, todo el **entorno** falla en esa comprobación de estado. Al igual que con las pruebas de calidad y rendimiento del código, estas comprobaciones de estado se organizan en categorías y se notifican mediante el sistema de enlace de tres niveles. La única distinción es que no hay umbral en el caso de las pruebas de seguridad. Todos los controles de salud son simplemente aprobados o no.

En la tabla siguiente se muestran las comprobaciones actuales:

| **Nombre** | **Implementación de comprobación de estado** | **Categoría** |
|---|---|---|
| Deserialización cortafuegos Adjuntar preparación de API está en un estado aceptable | Disposición de la API de anexo de cortafuegos de deserialización |  Crítico |
| El cortafuegos de deserialización funciona | Cortafuegos de deserialización funcional |  Crítico |
| Se cargó el cortafuegos de deserialización | Cortafuegos de deserialización cargado |  Crítico |
| La implementación de AuthorizableNodeName no muestra el ID autorizado en el nombre o la ruta de nodo. | Generación del nombre de nodo con autorización |  Crítico |
| Se han cambiado las contraseñas predeterminadas | Cuentas de inicio de sesión predet. |  Crítico |
| El servlet GET predeterminado de Sling está protegido contra ataques DOS. | Sling Get Servlet |  Crítico |
| Dispatcher filtra correctamente las solicitudes | Configuración de CQ Dispatcher |  Crítico |
| Sling Java Script Handler está configurado correctamente | Sling Java Script Handler |  Crítico |
| Sling JSP Script Handler está configurado correctamente | Sling JSP Script Handler |  Crítico |
| SSL está configurado correctamente | Configuración SSL |  Crítico |
| No se encontraron directivas de perfil de usuario obviamente inseguras | Acceso predet. del perfil de usuario |  Crítico |
| El filtro de referente de Sling está configurado para evitar ataques de CSRF | Filtro de referente de Sling | Importante |
| Adobe Granite HTML Library Manager está configurado correctamente | Configuración del administrador de bibliotecas HTML de CQ | Importante |
| El paquete de compatibilidad con CRXDE está deshabilitado | Compatibilidad con CRXDE | Importante |
| El paquete y servlet Sling DavEx están desactivados | Comprobación de estado de DavEx | Importante |
| El contenido de muestra no está instalado | Paquetes de contenido de ejemplo | Importante |
| El filtro de solicitud WCM y el filtro de depuración WCM están desactivados | Configuración de filtros WCM | Importante |
| El paquete y servlet Sling WebDAV están correctamente configurados | Comprobación de estado de WebDAV | Importante |
| El servidor web está configurado para evitar el rastreo de clics | Configuración de servidor web | Importante |
| La replicación no utiliza el usuario 'admin' | Replicación y usuarios de transporte | Información |

## Prueba de rendimiento {#performance-testing}

*La prueba* de rendimiento en [!UICONTROL Cloud Manager] se implementa mediante una prueba de 30 minutos.

Durante la configuración del canal, el administrador de implementación puede decidir cuánto tráfico dirigir a cada bloque.

Puede obtener más información sobre los controles de bucket en [Configurar la canalización](configuring-pipeline.md)CI/CD.

>[!NOTE]
>
>Para configurar el programa y definir los KPI, consulte [Configuración del programa](setting-up-program.md).

La siguiente tabla resume la matriz de prueba de rendimiento utilizando el sistema de enlace de tres niveles:

| **Métrica** | **Categoría** | **Umbral de error** |
|---|---|---|
| Tasa de errores de solicitud de página % |  Crítico | &gt;= 2% |
| Tasa de utilización de CPU |  Crítico | &gt;= 80% |
| Tiempo de espera de E/S de disco |  Crítico | &gt;= 50% |
| Tiempo de respuesta del 95 % | Importante | &gt;= KPI a nivel de programa |
| Tiempo máximo de respuesta | Importante | &gt;= 18 segundos |
| Vistas de página por minuto | Importante | &lt; KPI a nivel de programa |
| Uso del ancho de banda del disco | Importante | &gt;= 90% |
| Uso del ancho de banda de la red | Importante | &gt;= 90% |
| Solicitudes por minuto | Información | &lt; 6000 |

### Gráficos de resultados de la prueba de rendimiento {#performance-testing-results-graphs}

Se han añadido nuevos gráficos y opciones de descarga al cuadro de diálogo Resultados de la prueba de rendimiento.

Al abrir el cuadro de diálogo Prueba de rendimiento, los paneles de métricas se pueden expandir para mostrar un gráfico, proporcionar un vínculo a una descarga o ambos.

Para [!UICONTROL Cloud Manager] la versión 2018.7.0, esta funcionalidad está disponible para las siguientes métricas:

* **Uso de CPU**
   * Un gráfico de la utilización de CPU durante el período de prueba.

* **Tiempo de espera de E/S de disco**
   * Un gráfico del tiempo de espera de E/S de disco durante el período de prueba.

* **Tasa de errores de página**
   * Un gráfico de los errores de página por minuto durante el período de prueba.
   * Un archivo CSV enumera las páginas que han producido un error durante la prueba.

* **Uso del ancho de banda del disco**
   * Gráfico de la utilización del ancho de banda del disco durante el período de prueba.

* **Uso del ancho de banda de la red**
   * Gráfico de la utilización del ancho de banda de la red durante el período de prueba.

* **Tiempo máximo de respuesta**
   * Un gráfico del tiempo de respuesta máximo por minuto durante el período de prueba.

* **Tiempo de respuesta del porcentaje 95**
   * Gráfico del tiempo de respuesta del percentil 95 por minuto durante el período de prueba.
   * Un archivo CSV enumera las páginas cuyo tiempo de respuesta en porcentaje 95 ha excedido el KPI definido.

Las siguientes imágenes muestran los gráficos de prueba de rendimiento:

![](assets/understand_test-results-screen1.png)

![](assets/screen_shot_2018-09-05at83933pm.png)

