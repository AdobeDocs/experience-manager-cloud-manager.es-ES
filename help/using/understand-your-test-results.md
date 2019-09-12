---
title: Comprender los resultados de la prueba
seo-title: Comprender los resultados de la prueba
description: nulo
seo-description: Siga esta página para obtener más información sobre tres puertas de nivel al ejecutar un canal, una digitalización de código, un rendimiento y pruebas de seguridad que validan su programa en Cloud Manager.
uuid: 93 caa 01 f -0 df 2-4 a 6 f -81 dc -23 dfee 24 dc 93
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299 ed 8-4 b 7 a -4 b 1 c-bd 56-1 bfc 7 e 7318 d 4
translation-type: tm+mt
source-git-commit: 26014cfabfee6226033ba2fc1167d8f5509e17c6

---


# Comprender los resultados de la prueba {#understand-your-test-results}

Durante el proceso **de Pipeline** , se capturan varias métricas y se comparan con los indicadores de rendimiento clave (KPI) definidos por el propietario del negocio, o con estándares establecidos por Adobe Managed Services.

Se registran usando el sistema de gating de tres niveles como se define en esta sección.

## Puertas de tres niveles al ejecutar un canal {#three-tier-gates-while-running-a-pipeline}

Hay tres puertas en el canal:

* Calidad del código
* Prueba de rendimiento
* Prueba de seguridad

Para cada una de estas puertas, existe una estructura de tres niveles para los problemas identificados por la puerta.

* **Crítico** : Son problemas identificados por la puerta que provocan un fallo inmediato en la canalización.
* **Importante** : Son problemas identificados por la puerta que hacen que el canal introduzca un estado pausado. Un administrador de implementación, un administrador de proyectos o un propietario comercial pueden anular los problemas, en cuyo caso el canalizador continúa o puede aceptar los problemas, en cuyo caso la canalización se detiene con un error.
* **Información** : Son problemas identificados por la computación que se proporcionan exclusivamente con fines informativos y no tienen impacto en la ejecución del canal.

>[!NOTE]
>
>En el canal Solo calidad de código, no se pueden anular los errores importantes en la portada de Comprobación de calidad del código, ya que el paso de comprobación de calidad de código es el último paso en la canalización.

## Prueba de calidad del código {#code-quality-testing}

Como parte del canal, se escanea el código fuente para garantizar que las implementaciones cumplan determinados criterios de calidad. Actualmente, esto se implementa mediante una combinación de sonarchbe y de un examen de nivel de paquete de contenido usando oakpal. Existen más de 100 reglas que combinan reglas genéricas Java y reglas específicas de AEM. En la tabla siguiente se resume la clasificación para los criterios de prueba:

| Nombre | Definición | Categoría | Umbral de error |
|--- |--- |--- |--- |
| Clasificación de seguridad | A = 0 Vulnerabilidad <br/>B = al menos 1 Vulnerabilidad menor<br/> C = por lo menos 1 Vulnerabilidad mayor <br/>D = al menos 1 Vulnerabilidad crítica <br/>E = al menos 1 Vulnerabilidad de bloqueo | Crítico | &lt; B |
| Clasificación de fiabilidad | A = 0 Bug <br/>B = al menos 1 Error menor <br/>C = al menos 1 error grave <br/>D = al menos 1 error grave E = al menos 1 error de bloqueo | Importante | &lt; C |
| Clasificación de capacidad de permanencia | El costo de remediación excepcional del código smells es: <br/><ul><li>&lt; = 5% del tiempo que ya se ha entrado en la aplicación, la clasificación es A. </li><li>entre 6 y 10% la clasificación es una B </li><li>entre 11 y 20% la clasificación es un C </li><li>entre 21 y 50% la clasificación es un D</li><li>todo lo que supere el 50% es un E</li></ul> | Importante | &lt; A |
| Cobertura | Combinación de cobertura de línea de prueba unitaria y cobertura de condición mediante esta fórmula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`<br/>donde: CT = condiciones que se han evaluado a'true'al menos una vez mientras se ejecutan las pruebas <br/>de unidad CF = condiciones que se han evaluado en'false'al menos una vez mientras se ejecutan pruebas <br/>unitarias LC = líneas cubiertas = líneas_ to_ cover - uncover_ lines <br/><br/> B = líneas_ to_ cover - <br/>uncover_ lines de líneas ejecutables (líneas_ a_ portada) | Importante | &lt; 50% |
| Omitir pruebas de unidad | Número de pruebas de unidad omitidas. | Información | &gt; 1 |
| Problemas abiertos | Tipos de problemas generales: vulnerabilidades, errores y huelgas de código | Información | &gt; 1 |
| Líneas duplicadas | Número de líneas involucradas en bloques duplicados. <br/>Para que un bloque de código se considere como duplicado: <br/><ul><li>**Proyectos que no son Java:**</li><li>Debe haber al menos 100 tokens duplicados y duplicados.</li><li>Estos tokens deben propagarse al menos en: </li><li>30 líneas de código para COBOL </li><li>20 líneas de código para ABAP </li><li>10 líneas de código para otros idiomas</li><li>**Proyectos Java:**</li><li> Debe haber al menos 10 afirmaciones sucesivas y duplicadas independientemente del número de tokens y líneas.</li></ul> <br/>Las diferencias en la sangría y en los literales de cadena se ignoran al detectar duplicaciones. | Información | &gt; 1% |


>[!NOTE]
>
>Consulte Definiciones [de métricas](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) para obtener definiciones más detalladas.

Puede descargar la lista de reglas aquí [code-quality-rules.xlsx](/help/using/assets/CodeQuality-Rules-new.xlsx)

>[!NOTE]
>
>Para obtener más información sobre las reglas de calidad de código personalizadas realizadas por [!UICONTROL Cloud Manager], consulte Reglas de calidad de código [personalizado](custom-code-quality-rules.md).

### Uso de falsos positivos {#dealing-with-false-positives}

El proceso de digitalización de calidad no es perfecto y a veces identificará incorrectamente los problemas que no son problemáticos. Esto se denomina "falso positivo".

En estos casos, el código fuente se puede anotar con la anotación estándar Java `@SuppressWarnings` que especifica el ID de regla como atributo de anotación. Por ejemplo, un problema común es que la regla sonarchbe para detectar contraseñas codificadas puede ser agresiva sobre cómo se identifica una contraseña codificada.

Para ver un ejemplo específico, este código sería bastante común en un proyecto de AEM que tiene código para conectarse a algún servicio externo:

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Sonarquía aumenta luego una vulnerabilidad de bloqueador. Después de revisar el código, debe identificar que no es una vulnerabilidad y puede anotarlo con la identificación de regla adecuada.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Sin embargo, si el código era realmente esto:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

A continuación, la solución correcta es eliminar la contraseña codificada.

>[!NOTE]
>
>Aunque es recomendable hacer la `@SuppressWarnings` anotación lo más específica posible, es decir, anotar únicamente la afirmación o bloque que causa el problema, es posible anotar en un nivel de clase.

## Prueba de seguridad {#security-testing}

[!UICONTROL Cloud Manager] ejecuta las comprobaciones de seguridad ***de AEM existentes*** en el escenario después de la implementación e informa sobre el estado a través de la interfaz de usuario. Los resultados se agregan desde todas las instancias de AEM en el entorno.

Si alguna **de las instancias** indica un error en una comprobación de estado determinada, todo **el Entorno** falla en esa comprobación de estado. Al igual que con la Calidad del código y la Prueba de rendimiento, estas comprobaciones de estado se organizan en categorías y se registran usando el sistema de gating de tres niveles. La única diferencia es que no hay umbral en el caso de las pruebas de seguridad. Todas las comprobaciones de estado simplemente pasan o dan error.

La siguiente tabla enumera las comprobaciones actuales:

| **Nombre** | **Implementación de comprobación de estado** | **Categoría** |
|---|---|---|
| Deserialization Firewall Attach API Readiness is in a acceptable state | Disposición de la API de anexo de cortafuegos de deserialización | Crítico |
| El servidor de seguridad de Deserialization funciona | Cortafuegos de deserialización funcional | Crítico |
| Se carga el servidor de seguridad de deserialización | Cortafuegos de deserialización cargado | Crítico |
| La implementación authorizablenodename no expone ID autorizables en el nombre o ruta del nodo. | Generación del nombre de nodo con autorización | Crítico |
| Se han cambiado las contraseñas predeterminadas | Cuentas de inicio de sesión predet. | Crítico |
| El servlet GET predeterminado está protegido frente a los ataques DOS. | Sling Get Servlet | Crítico |
| Dispatcher está filtrando correctamente las solicitudes | Configuración de CQ Dispatcher | Crítico |
| El controlador de secuencias de comandos Sling Java se configura correctamente | Sling Java Script Handler | Crítico |
| El controlador de secuencias de comandos Sling JSP se configura correctamente | Sling JSP Script Handler | Crítico |
| SSL se configura correctamente | Configuración SSL | Crítico |
| Obviamente no se encontraron políticas de perfil de usuario no seguras | Acceso predet. del perfil de usuario | Crítico |
| El filtro de referentes Sling está configurado para evitar ataques CSRF | Filtro de referente de Sling | Importante |
| El Administrador de biblioteca HTML de Granite de Adobe se configura correctamente | Configuración del administrador de bibliotecas HTML de CQ | Importante |
| Se desactiva el paquete de compatibilidad CRXDE | Compatibilidad con CRXDE | Importante |
| El servlet y el paquete Sling davex están desactivados | Comprobación de estado de DavEx | Importante |
| El contenido de muestra no está instalado | Paquetes de contenido de ejemplo | Importante |
| El filtro de solicitud WCM y el filtro de depuración WCM están desactivados | Configuración de filtros WCM | Importante |
| El servlet y el paquete Sling webdav se configuran correctamente | Comprobación de estado de WebDAV | Importante |
| El servidor web está configurado para evitar el rastreo de clics | Configuración de servidor web | Importante |
| Replicación no está usando el usuario'administrador ' | Replicación y usuarios de transporte | Información |

## Prueba de rendimiento {#performance-testing}

*Las pruebas de rendimiento* se [!UICONTROL Cloud Manager] implementan con una prueba de 30 minutos.

Durante la configuración de la canalización, el administrador de implementación puede decidir cuánto tráfico dirigir a cada bloque.

Puede obtener más información sobre los controles de bucket, desde [Configurar su flujo de PC/CD](configuring-pipeline.md).

>[!NOTE]
>
>Para configurar el programa y definir los KPI, consulte [Configuración del programa](setting-up-program.md).

En la tabla siguiente se resume la matriz de prueba de rendimiento utilizando el sistema de gating de tres niveles:

| **Métrica** | **Categoría** | **Umbral de error** |
|---|---|---|
| Tasa de error de solicitud de página % | Crítico | &gt;= 2% |
| Tasa de uso de CPU | Crítico | &gt;= 80% |
| Tiempo de espera de la IO de disco | Crítico | &gt;= 50% |
| 95 tiempo de respuesta del percentil | Importante | &gt; = KPI de nivel de programa |
| Tiempo de respuesta máxima | Importante | &gt; = 18 segundos |
| Vistas de página por minuto | Importante | &lt; KPI de nivel de programa |
| Uso de ancho de banda de disco | Importante | &gt;= 90% |
| Uso de ancho de banda de la red | Importante | &gt;= 90% |
| Solicitudes por minuto | Información | &lt; 6000 |

### Gráficos de resultados de prueba de rendimiento {#performance-testing-results-graphs}

Se han agregado nuevos gráficos y opciones de descarga al cuadro de diálogo Resultados de la prueba de rendimiento.

Cuando abra el cuadro de diálogo Prueba de rendimiento, los paneles de métricas se pueden expandir para mostrar un gráfico, proporcionar un vínculo a una descarga o ambos.

En [!UICONTROL Cloud Manager] la versión 2018.7.0, esta funcionalidad está disponible para las siguientes métricas:

* **Uso de CPU**
   * Gráfico de uso de CPU durante el periodo de prueba.

* **Tiempo de espera de disco I/O**
   * Gráfico del tiempo de espera de disco I/O durante el periodo de prueba.

* **Tasa de error de página**
   * Gráfico de errores de página por minuto durante el periodo de prueba.
   * Un archivo CSV que enumera las páginas que produjeron un error durante la prueba.

* **Uso de ancho de banda de disco**
   * Gráfico de Uso de ancho de banda de disco durante el periodo de prueba.

* **Uso de ancho de banda de la red**
   * Gráfico de uso de ancho de banda de la red durante el período de prueba.

* **Tiempo de respuesta máxima**
   * Gráfico de tiempo de respuesta máximo por minuto durante el periodo de prueba.

* **95 º tiempo de respuesta del percentil**
   * Gráfico de tiempo de respuesta de percentil 95 por minuto durante el periodo de prueba.
   * Un archivo CSV que enumera páginas cuyo 95 º intervalo de respuesta de percentil ha excedido el KPI definido.

Las siguientes imágenes muestran los gráficos de prueba de rendimiento:

![](assets/understand_test-results-screen1.png)

![](assets/screen_shot_2018-09-05at83933pm.png)

