---
title: Uso de Cloud Manager
seo-title: Uso de Adobe AEM Cloud Manager
description: Se explica la interfaz de usuario de AEM Cloud Manager
seo-description: Interfaz de usuario de Adobe AEM Cloud Manager
page-status-flag: no activado nunca
uuid: cef 44 d 35-75 ed -44 bb -9636-2 de 2 bca 5 e 458
contentOwner: jsyal
discoiquuid: c 37566 d 5-0 d 1 b -4 c 44-abd 7-b 271 ea 443 c 1 a
translation-type: tm+mt
source-git-commit: 4c1c6786db9b8972f9315bd2f12fc1752881492f

---


# Using Cloud Manager{#using-cloud-manager}

This section explains the User Interface (UI) for [!UICONTROL Cloud Manager] and explains the workflow from setting up the program to code deployment followed by quality checks.

## Requisitos previos {#prerequisites}

Before you get into the details of using the [!UICONTROL Cloud Manager], it is recommended to go though the following sections:

* [Explicación de los conceptos antes de utilizar [! UICONTROL Cloud Manager]](understanding-concepts.md)
* [Configuración de configuraciones generales para [! UICONTROL Cloud Manager]](setting-configurations-for-cloud-manager.md)

## Getting Started with [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Once you have setup the general configurations for [!UICONTROL Cloud Manager], you are ready to use the [!UICONTROL Cloud Manager].

1. Log in to the Adobe [!UICONTROL Experience Cloud] and you will see the list of solutions.

   ![](assets/screen_shot_2018-04-22at92951am.png)

1. Select the program and click on the top left icon to open [!UICONTROL Cloud Manager].

   ![](assets/screen_shot_2018-04-22at93346am.png)

## Setting Up Program {#setting-up-program}

Tras la integración, el propietario del negocio deberá realizar alguna configuración inicial del programa. Esto implica configurar la descripción del programa y definir los KPI que se utilizarán para la prueba de rendimiento. Opcionalmente, se puede cargar una miniatura.

Los KPI definidos sirven como referencia para la prueba de rendimiento que se pasa cada vez que se ejecuta la canalización.

>[!NOTE]
>
>The KPIs defined are measured on tests run on the **stage** environment. Normalmente, estos KPI se reducen para adaptarse a las capacidades del entorno de etapa.
>
>For example, a user expecting an average of 1000 page views per minute in their production environment and having four `dispatcher/publish` servers in production should scale this to 250 page views per minute (assuming their stage environment consists of only a single `dispatcher/publish` server pair).
>
>Además, muchos usuarios tendrán un CDN (Akamai, cloudfront) delante del entorno de producción. Since [!UICONTROL Cloud Manager] tests against the stage environment directly, the KPI should reflect only the traffic expected to pass through the CDN, that is, the cache misses. Generalmente, éste será un subconjunto relativamente pequeño del tráfico total de producción.

### Using [!UICONTROL Cloud Manager] to define KPIs {#using-cloud-manager-to-define-kpis}

Siga los pasos a continuación para configurar el programa y definir KPI:

1. Click **Setup Program** to start the setup process in [!UICONTROL Cloud Manager].
1. The **Edit Program Information** screen displays.

   Cargue una miniatura en el programa. You can also add a relevant description to your program and click **Next**.

1. The **Configure Users** screen displays.

   Puede configurar las funciones y los usuarios de su equipo. Haga clic en **Siguiente**. 

1. The **Configure General Business KPIs** screen displays.

   Puede definir los dos KPI (expectativas para cada implementación):

   1. ¿Cuál es el tiempo de respuesta de percentil 95 que es aceptable para usted?

      1. Valor recomendado - 3 segundos
   1. ¿Cuántas vistas de página por minuto bajo la carga máxima?

      1. Valor recomendado - 200 pv/m


1. Click **Submit** to complete the setup wizard.

   You will see the home screen for [!UICONTROL Cloud Manager] change to **Deploy**.

## Available Environments {#available-environments}

The **Available Environments** in the [!UICONTROL Cloud Manager] lists all the managed AEM environments.

Cada uno de los entornos enumerados tendrá un estado asociado.

## Configuring Pipeline {#configuring-pipeline}

### Setting up Pipeline {#setting-up-pipeline}

>[!CAUTION]
>
>La canalización no se puede configurar hasta que el repositorio de git tenga al menos una rama.

Before you start to deploy your code, you must configure your pipeline settings from the [!UICONTROL Cloud Manager].

To learn more about pipeline configuration, see **Pipeline Overview** section in ** [Understanding Concepts before Using [!UICONTROL Cloud Manager]](understanding-concepts.md)**.

>[!NOTE]
>
>Puede cambiar la configuración del canal después de la configuración inicial.

### Configuring Pipeline Settings from the [!UICONTROL Cloud Manager] {#configuring-pipeline-settings-from-the-cloud-manager}

Follow the steps below from the [!UICONTROL Cloud Manager] to configure the bahavior and preferences for your pipeline:

1. Access the **Branch** tab to set up the application branch.

   Seleccione la ramificación de git que desee configurar.

   >[!NOTE]
   >
   >Las ramas que se encuentran en el repositorio de Git están vinculadas al programa.

   ![](assets/screen_shot_2018-05-06at73604pm.png)

1. Access the **Environments** tab to select **Stage** and **Production** options.

   Puede definir el activador que iniciará la canalización:

   * **Manual** : alguien tiene que hacer clic manualmente en la interfaz de usuario para iniciar la canalización.
   Ahora define los parámetros que controlan la implementación de producción. Las tres opciones disponibles son las siguientes:

   * **Usar aprobación en lanzamiento**: un propietario de negocio, un administrador de proyectos o un gestor de implementación deben aprobar una implementación manualmente a través de [!UICONTROL Cloud Manager] la interfaz de usuario.
   * **Usar CSE Monitoring** - A CSE is engaged to really start the deployment.
   ![](assets/screen_shot_2018-05-06at73715pm.png)

1. Access the **Testing** tab to define your testing criteria for your program.

   Ahora puede configurar los parámetros de prueba de rendimiento.

   ![](assets/screen_shot_2018-05-06at73750pm.png)

## Deploying Code {#deploying-code}

Una vez configurado el canal (repositorio, entorno y entorno de prueba), podrá implementar su código.

### Deploying Code from [!UICONTROL Cloud Manager] {#deploying-code-from-cloud-manager}

Siga los pasos a continuación para implementar el código en el entorno de producción:

1. Click **Deploy** from the [!UICONTROL Cloud Manager] to start the deployment process.
1. The **Stage Deployment** screen displays.

   Click **Build** to start the process.

1. El proceso de generación completo tiene en cuenta varios parámetros para comprobar e implementar el código.

   Los siguientes parámetros que están marcados son los siguientes:

   **Implementación del escenario**

   * Repositorio
   * Prueba de unidad
   * Digitalización de código
   * Implementado en el entorno de escenario
   **Pruebas previas a la producción**

   * Prueba de seguridad
   * Prueba de rendimiento
   >[!NOTE]
   >
   >Además, puede ver registros o revisar los resultados para los criterios de prueba mencionados anteriormente.

## Results from Quality Checks {#results-from-quality-checks}

Hay tres puertas en el canal: Calidad del código, Prueba de rendimiento y Prueba de seguridad.

Para cada una de estas puertas, existe una estructura de tres niveles para los problemas identificados por la puerta.

* **Crítico** : Son problemas identificados por la puerta que provocan un fallo inmediato en la canalización.
* **Importante** : Son problemas identificados por la puerta que hacen que el canal introduzca un estado pausado. Un administrador de implementación, un administrador de proyectos o un propietario comercial pueden anular los problemas, en cuyo caso el canalizador continúa o puede aceptar los problemas, en cuyo caso la canalización se detiene con un error.
* **Información** : Son problemas identificados por la computación que se proporcionan exclusivamente con fines informativos y no tienen impacto en la ejecución del canal.

### Code Scanning {#code-scanning}

![](assets/screen_shot_2018-04-22at101443am.png)

### Performance Testing {#performance-testing}

*Las pruebas de rendimiento* se [!UICONTROL Cloud Manager] implementan mediante una prueba durante 30 minutos.

Durante la configuración de la canalización, el administrador de implementación puede decidir cuánto tráfico dirigir a cada bloque. Pueden elegir entre uno y tres bloques. La distribución del tráfico se basa en el número de bloques seleccionados, es decir, si se seleccionan los tres, el 33% del total de vistas de página se sitúa en cada bloque; si se seleccionan dos, el 50% va a cada conjunto; Si se selecciona uno, el 100% del tráfico va a dicho conjunto.

Por ejemplo: supongamos que hay un 50%/50% dividido entre las Páginas interactivas populares y las Páginas nuevas (en este ejemplo no se utiliza Otras páginas Live) y el conjunto Nuevas páginas contiene 3000 páginas. Las vistas de página por minuto KPI se establecen en 200. Durante el período de prueba de 30 minutos:

* Each of the 25 pages in the Popular Live Pages set will be hit 240 times - `((200 &#42; 0.5) / 25) &#42; 30 = 120`
* Each of the 3000 pages in the New Pages set will be hit once - `((200 &#42; 0.5) / 3000) &#42; 30 = 1`

![](assets/image2018-3-14_16-23-56.png)

### Performance Test Metrics {#performance-test-metrics}

Durante el período de prueba, se capturan varias métricas y se comparan con los KPI definidos por el propietario del negocio o con los estándares establecidos por AMS.

Se registran usando el sistema de gating de tres niveles como se indica a continuación:

### Three-Tier Gates while Running a Pipeline {#three-tier-gates-while-running-a-pipeline}

Hay tres puertas en la canalización como Calidad del código, Prueba de rendimiento y Prueba de seguridad.

Para cada una de estas puertas, existe una estructura de tres niveles para los problemas identificados por el portal:

* **Crítico**: Se trata de problemas identificados por la puerta de enlace que producen un fallo inmediato en la canalización.
* **Importante**: Se trata de problemas identificados por la puerta que provocan que el canal introduzca un estado pausado. Un administrador de implementación, un administrador de proyectos o un propietario comercial pueden anular los problemas, en cuyo caso el canalizador continúa o puede aceptar los problemas, en cuyo caso la canalización se detiene con un error.
* **Información**: Se trata de problemas identificados por la compuerta que se proporcionan exclusivamente con fines informativos y que no tienen impacto en la ejecución del canal.

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

### Security Testing {#security-testing}

[!UICONTROL Cloud Manager] ejecuta las comprobaciones de seguridad *de AEM existentes* en el escenario después de la implementación e informa su estado a través de la interfaz de usuario. Los resultados se agregan desde todas las instancias de AEM en el entorno.

Si alguna de las instancias indica un error en una comprobación de estado determinada, todo el entorno falla en la comprobación de estado. Al igual que con la Calidad del código y la Prueba de rendimiento, estas comprobaciones de estado se organizan en categorías y se registran usando el sistema de gating de tres niveles. La única diferencia es que no hay umbral en el caso de las pruebas de seguridad. Todas las comprobaciones de estado simplemente pasan o dan error.

Las comprobaciones actuales son:

| **Comprobación de estado** | **Categoría** |
|---|---|
| Disposición de la API de anexo de cortafuegos de deserialización | Crítico |
| Cortafuegos de deserialización funcional | Crítico |
| Cortafuegos de deserialización cargado | Crítico |
| Generación del nombre de nodo con autorización | Crítico |
| Cuentas de inicio de sesión predet. | Crítico |
| Sling Get Servlet | Crítico |
| Configuración de CQ Dispatcher | Crítico |
| Configuración del administrador de bibliotecas HTML de CQ | Crítico |
| Sling Java Script Handler | Crítico |
| Sling Jsp Script Handler | Crítico |
| Filtro de referente de Sling | Crítico |
| Configuración SSL | Crítico |
| Acceso predet. del perfil de usuario | Crítico |
| Compatibilidad con CRXDE | Importante |
| Comprobación de estado de DavEx | Importante |
| Paquetes de contenido de ejemplo | Importante |
| Configuración de filtros WCM | Importante |
| Comprobación de estado de WebDAV | Importante |
| Configuración de servidor web | Importante |
| Replicación y usuarios de transporte | Información |

### Quality Check Implementation by SonarQube {#quality-check-implementation-by-sonarqube}

Como parte del canal, como se muestra arriba, se escanea el código. Actualmente, sonarquía se implementa. Tenemos 93 reglas que son una combinación de reglas genéricas Java y reglas específicas de AEM (incluidos algunos del conjunto de reglas existente de Cognifide). A list of these rules can be found here: [code-quality-rules.xlsx](/help/using/assets/code-quality-rules.xlsx)

A partir de estas reglas, se calcula una variedad de métricas, algunas de las cuales se utilizan como puertas de calidad antes de permitir una implementación en el entorno de etapa.

Estos son los umbrales actuales:

| Nombre | Definición | Categoría | Umbral de error |
|--- |--- |--- |--- |
| Clasificación de seguridad | A = 0 Vulnerability <br/>B = at least 1 Minor Vulnerability<br/> C = at least 1 Major Vulnerability <br/>D = at least 1 Critical Vulnerability <br/>E = at least 1 Blocker Vulnerability | Crítico | &lt; B |
| Clasificación de fiabilidad | A = 0 Bug <br/>B = at least 1 Minor Bug <br/>C = at least 1 Major Bug <br/>D = at least 1 Critical Bug E = at least 1 Blocker Bug | Importante | &lt; C |
| Clasificación de capacidad de permanencia | Outstanding remediation cost for code smells is: <br/><ul><li>&lt; = 5% del tiempo que ya se ha entrado en la aplicación, la clasificación es A. </li><li>entre 6 y 10% la clasificación es una B </li><li>entre 11 y 20% la clasificación es un C </li><li>entre 21 y 50% la clasificación es un D</li><li>todo lo que supere el 50% es un E</li></ul> | Importante | &lt; A |
| Cobertura | A mix of line coverage and condition coverage using this formula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <br/>where: CT = conditions that have been evaluated to &#39;true&#39; at least once <br/>CF = conditions that have been evaluated to &#39;false&#39; at least once <br/>LC = covered lines = lines_to_cover - uncovered_lines <br/><br/> B = total number of conditions <br/>EL = total number of executable lines (lines_to_cover) | Importante | &lt; 50% |
| Omitir pruebas de unidad | Número de pruebas de unidad omitidas. | Información | &gt; 1 |
| Problemas abiertos | Tipos de problemas generales: vulnerabilidades, errores y huelgas de código | Información | &gt; 1 |
| Líneas duplicadas | Número de líneas involucradas en bloques duplicados. <br/>Para que un bloque de código se considere como duplicado: <ul><li> **Proyectos que no son Java:**</li><li>Debe haber al menos 100 tokens duplicados y duplicados.</li><li>Estos tokens deben propagarse al menos en: </li><li>30 líneas de código para COBOL </li><li>20 líneas de código para ABAP </li><li>10 líneas de código para otros idiomas</li></ul><ul><li>**Proyectos Java:**</li><li> Debe haber al menos 10 afirmaciones sucesivas y duplicadas independientemente del número de tokens y líneas.</li></ul>Las diferencias en la sangría y en los literales de cadena se ignoran al detectar duplicaciones. | Información | &gt; 1% |

### False Positives {#false-positives}

El proceso de digitalización de calidad no es perfecto y a veces identificará incorrectamente los problemas que no son problemáticos. This is called a *false positive* (although *false negative* would probably be more semantically correct). In these cases, the source code can be annotated with the standard Java `@SuppressWarnings` annotation specifying the rule ID as the annotation attribute. Por ejemplo, un problema común es que la regla sonarchbe para detectar contraseñas codificadas es muy liberal sobre lo que considera una contraseña codificada.

Para ver un ejemplo específico, este código sería bastante común en un proyecto de AEM que tiene código para conectarse a algún servicio externo:

```java
@Property(label = "Service Password")
private static final String SERVICE_PASSWORD = "password";
```

Sonarquía lo elevará como vulnerabilidad del bloqueador. En este caso, el cliente puede identificar que esto no es una vulnerabilidad y anotar esto con la identificación de regla adecuada:

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String SERVICE_PASSWORD = "password";
```

Sin embargo, si el código era realmente esto:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String SERVICE_PASSWORD = "password";
```

A continuación, el cliente debe tomar la advertencia de sontotalbe y eliminar la contraseña codificada. They will still, however, need to add the `@SuppressWarnings` annotation since the SonarQube rule is actually being triggered by the term `password`.

>[!NOTE]
>
>It is a best practice to make the `@SuppressWarnings` annotation as specific as possible, i.e. annotate only the specific statement or block causing the issue, it is possible to annotate at a class level.

