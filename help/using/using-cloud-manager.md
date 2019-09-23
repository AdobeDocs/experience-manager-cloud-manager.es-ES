---
title: Uso de Cloud Manager
seo-title: Uso de Adobe AEM Cloud Manager
description: Se explica la interfaz de usuario de AEM Cloud Manager
seo-description: Se explica la interfaz de usuario de Adobe AEM Cloud Manager
page-status-flag: nunca activado
uuid: cef44d35-75ed-44bb-9636-2de2bca5e458
contentOwner: jsyal
discoiquuid: c37566d5-0d1b-4c44-abd7-b271ea443c1a
translation-type: tm+mt
source-git-commit: 4c1c6786db9b8972f9315bd2f12fc1752881492f

---


# Uso de Cloud Manager{#using-cloud-manager}

En esta sección se explica la interfaz de usuario [!UICONTROL Cloud Manager] y el flujo de trabajo desde la configuración del programa hasta la implementación de código, seguida de comprobaciones de calidad.

## Requisitos previos {#prerequisites}

Antes de entrar en los detalles del uso de [!UICONTROL Cloud Manager], se recomienda seguir las siguientes secciones:

* [Conceptos antes de utilizar [!UICONTROL Cloud Manager]](understanding-concepts.md)
* [Configuración general de [!UICONTROL Cloud Manager]](setting-configurations-for-cloud-manager.md)

## Getting Started with [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Una vez que haya configurado las configuraciones generales para [!UICONTROL Cloud Manager], estará listo para usar el [!UICONTROL Cloud Manager].

1. Inicie sesión en Adobe [!UICONTROL Experience Cloud] y verá la lista de soluciones.

   ![](assets/screen_shot_2018-04-22at92951am.png)

1. Seleccione el programa y haga clic en el icono superior izquierdo para abrir [!UICONTROL Cloud Manager].

   ![](assets/screen_shot_2018-04-22at93346am.png)

## Configuración del programa {#setting-up-program}

Después de embarcar, el dueño de la empresa tendrá que hacer alguna configuración inicial del programa. Esto implica configurar la descripción del programa y definir los KPI que se utilizarán para las pruebas de rendimiento. Opcionalmente, se puede cargar una miniatura.

Los KPI definidos sirven de referencia para las pruebas de rendimiento que se pasan cada vez que se ejecuta la canalización.

>[!NOTE]
>
>Los KPI definidos se miden en pruebas ejecutadas en el entorno de **etapa** . Normalmente, estos KPI se reducen para adaptarse a las capacidades del entorno de etapa.
>
>Por ejemplo, un usuario que espere un promedio de 1000 vistas de página por minuto en su entorno de producción y que tenga cuatro `dispatcher/publish` servidores en producción debería escalarlo a 250 vistas de página por minuto (suponiendo que su entorno de etapa consiste en un solo par `dispatcher/publish` de servidores).
>
>Además, muchos usuarios tendrán una CDN (Akamai, CloudFront) delante de su entorno de producción. Dado que [!UICONTROL Cloud Manager] las pruebas con el entorno de etapa se realizan directamente, el KPI debe reflejar únicamente el tráfico que se espera que pase a través de la CDN, es decir, la caché no se encuentra. Normalmente, este será un subconjunto relativamente pequeño del tráfico total de producción.

### Uso [!UICONTROL Cloud Manager] para definir KPI {#using-cloud-manager-to-define-kpis}

Siga los pasos a continuación para configurar el programa y definir KPI:

1. Haga clic en Programa **de** instalación para iniciar el proceso de configuración en [!UICONTROL Cloud Manager].
1. Aparece la pantalla **Editar información** del programa.

   Cargue una miniatura en el programa. También puede agregar una descripción relevante al programa y hacer clic en **Siguiente**.

1. Aparece la pantalla **Configurar usuarios** .

   Puede configurar las funciones de equipo y los usuarios. Haga clic en **Siguiente**. 

1. Aparece la pantalla **Configurar KPI** generales de negocios.

   Puede definir los dos KPI (expectativas para cada implementación):

   1. ¿Cuál es el tiempo de respuesta del porcentaje 95 que usted puede aceptar?

      1. Valor recomendado: 3 segundos
   1. ¿Cuántas vistas de página por minuto bajo la carga máxima?

      1. Valor recomendado: 200 pv/m


1. Haga clic en **Enviar** para completar el asistente de configuración.

   Verá la pantalla de inicio para [!UICONTROL Cloud Manager] cambiar a **Implementar**.

## Entornos disponibles {#available-environments}

En Entornos **** disponibles de la [!UICONTROL Cloud Manager] lista se muestran todos los entornos AEM administrados.

Cada uno de los entornos enumerados tendrá un estado asociado.

## Configuración de tubería {#configuring-pipeline}

### Configuración de canalización {#setting-up-pipeline}

>[!CAUTION]
>
>La canalización no se puede configurar hasta que el repositorio de git tenga al menos una rama.

Antes de comenzar a implementar el código, debe configurar la configuración de la canalización desde el [!UICONTROL Cloud Manager].

Para obtener más información sobre la configuración de canalización, consulte la sección Información general **de** canalización en ** [Explicación de los conceptos antes de utilizar [!UICONTROL Cloud Manager]](understanding-concepts.md)**.

>[!NOTE]
>
>Puede cambiar la configuración de la canalización después de la configuración inicial.

### Configuración de tubería desde la [!UICONTROL Cloud Manager]{#configuring-pipeline-settings-from-the-cloud-manager}

Siga los pasos que se describen a continuación desde el [!UICONTROL Cloud Manager] para configurar el comportamiento y las preferencias de la canalización:

1. Acceda a la ficha **Ramificación** para configurar la ramificación de la aplicación.

   Seleccione la rama de git que desee configurar.

   >[!NOTE]
   >
   >Las ramas que se encuentran en el repositorio de Git están vinculadas a su programa.

   ![](assets/screen_shot_2018-05-06at73604pm.png)

1. Acceda a la ficha **Entornos** para seleccionar las opciones **Fase** y **Producción** .

   Puede definir el activador que iniciará la canalización:

   * **Manual** : alguien tiene que hacer clic manualmente en la interfaz de usuario para iniciar la canalización.
   Ahora define los parámetros que controlan la implementación de producción. Las tres opciones disponibles son las siguientes:

   * **Usar aprobación** de lanzamiento: una implementación debe ser aprobada manualmente por un propietario de empresa, un jefe de proyecto o un administrador de implementación a través de la [!UICONTROL Cloud Manager] interfaz de usuario.
   * **Usar la supervisión** de CSE: un CSE se compromete a iniciar realmente la implementación.
   ![](assets/screen_shot_2018-05-06at73715pm.png)

1. Acceda a la ficha **Pruebas** para definir los criterios de prueba del programa.

   Ahora puede configurar los parámetros de prueba de rendimiento.

   ![](assets/screen_shot_2018-05-06at73750pm.png)

## Implementación de código {#deploying-code}

Una vez configurada la canalización (repositorio, entorno y entorno de prueba), estará listo para implementar el código.

### Implementación de código desde [!UICONTROL Cloud Manager]{#deploying-code-from-cloud-manager}

Siga los pasos a continuación para implementar el código en el entorno de producción:

1. Haga clic en **Implementar** desde el [!UICONTROL Cloud Manager] para iniciar el proceso de implementación.
1. Aparece la pantalla Implementación **de** etapa.

   Haga clic en **Generar** para iniciar el proceso.

1. El proceso completo de compilación tiene en cuenta varios parámetros para comprobar e implementar el código.

   Los siguientes parámetros marcados son los siguientes:

   **Implementación de etapa**

   * Repositorio
   * Prueba de unidad
   * Análisis de código
   * Implementado en entorno de etapa
   **Pruebas previas a la producción**

   * Pruebas de seguridad
   * Prueba de rendimiento
   >[!NOTE]
   >
   >Además, puede ver registros o revisar los resultados de los criterios de prueba mencionados anteriormente.

## Resultados de las comprobaciones de calidad {#results-from-quality-checks}

Hay tres puertas en el oleoducto: Calidad del código, Pruebas de rendimiento y Pruebas de seguridad.

Para cada una de estas puertas, existe una estructura de tres niveles para los problemas identificados por la puerta.

* **Crítico** : Estos son problemas identificados por la puerta que causan un fallo inmediato en la tubería.
* **Importante** : Son problemas identificados por la puerta que hacen que la tubería entre en estado de pausa. Un administrador de implementación, un jefe de proyecto o un propietario de empresa pueden anular los problemas, en cuyo caso la canalización continúa, o pueden aceptar los problemas, en cuyo caso la canalización se detiene con un error.
* **Información** : Son problemas identificados por la puerta que se proporcionan exclusivamente con fines informativos y que no tienen impacto en la ejecución de la tubería.

### Análisis de código {#code-scanning}

![](assets/screen_shot_2018-04-22at101443am.png)

### Prueba de rendimiento {#performance-testing}

*La prueba* de rendimiento en [!UICONTROL Cloud Manager] se implementa mediante una prueba durante 30 minutos.

Durante la configuración del canal, el administrador de implementación puede decidir cuánto tráfico dirigir a cada bloque. Pueden elegir entre uno y los tres bloques. La distribución del tráfico se basa en el número de bloques seleccionados, es decir, si se seleccionan los tres, el 33 % del total de vistas de página se coloca en cada bloque; si se seleccionan dos, el 50 % va a cada conjunto; si se selecciona uno, el 100 % del tráfico se dirige a ese conjunto.

Por ejemplo: supongamos que hay una división del 50 %/50 % entre el conjunto Páginas en vivo populares y Páginas nuevas (en este ejemplo, no se utiliza Otras páginas en vivo) y que el conjunto Páginas nuevas contiene 3000 páginas. El KPI de vistas de página por minuto se establece en 200. Durante el período de prueba de 30 minutos:

* Cada una de las 25 páginas del conjunto de páginas en vivo populares se visitará 240 veces: `((200 &#42; 0.5) / 25) &#42; 30 = 120`
* Cada una de las 3000 páginas del conjunto Nuevas páginas se visita una vez: `((200 &#42; 0.5) / 3000) &#42; 30 = 1`

![](assets/image2018-3-14_16-23-56.png)

### Métricas de prueba de rendimiento {#performance-test-metrics}

Durante el período de prueba, se capturan varias métricas y se comparan con los KPI definidos por el propietario del negocio o con los estándares establecidos por AMS.

Estos se notifican utilizando el sistema de enlace de tres niveles de la siguiente manera:

### Puerta de tres niveles mientras se ejecuta una canalización {#three-tier-gates-while-running-a-pipeline}

Hay tres puertas en la canalización: Calidad del código, Pruebas de rendimiento y Pruebas de seguridad.

Para cada una de estas puertas, existe una estructura de tres niveles para los problemas identificados por la puerta:

* **Crítico**: Estos son problemas identificados por la puerta que causan un fallo inmediato de la tubería.
* **Importante**: Estos son problemas identificados por la puerta que hacen que la tubería entre en estado de pausa. Un administrador de implementación, un jefe de proyecto o un propietario de empresa pueden anular los problemas, en cuyo caso la canalización continúa, o pueden aceptar los problemas, en cuyo caso la canalización se detiene con un error.
* **Información**: Estos son problemas identificados por la puerta que se proporcionan exclusivamente con fines informativos y no tienen impacto en la ejecución de la tubería.

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

### Pruebas de seguridad {#security-testing}

[!UICONTROL Cloud Manager] ejecuta las comprobaciones *de estado de seguridad de* AEM existentes en el escenario después de la implementación e informa de su estado a través de la interfaz de usuario. Los resultados se agregan de todas las instancias de AEM en el entorno.

Si alguna de las instancias informa de un error en una determinada comprobación de estado, todo el entorno falla en esa comprobación de estado. Al igual que con las pruebas de calidad y rendimiento del código, estas comprobaciones de estado se organizan en categorías y se notifican mediante el sistema de enlace de tres niveles. La única distinción es que no hay umbral en el caso de las pruebas de seguridad. Todos los controles de salud son simplemente aprobados o no.

Las comprobaciones actuales son:

| **Comprobación de estado** | **Categoría** |
|---|---|
| Disposición de la API de anexo de cortafuegos de deserialización |  Crítico |
| Cortafuegos de deserialización funcional |  Crítico |
| Cortafuegos de deserialización cargado |  Crítico |
| Generación del nombre de nodo con autorización |  Crítico |
| Cuentas de inicio de sesión predet. |  Crítico |
| Sling Get Servlet |  Crítico |
| Configuración de CQ Dispatcher |  Crítico |
| Configuración del administrador de bibliotecas HTML de CQ |  Crítico |
| Sling Java Script Handler |  Crítico |
| Sling Jsp Script Handler |  Crítico |
| Filtro de referente de Sling |  Crítico |
| Configuración SSL |  Crítico |
| Acceso predet. del perfil de usuario |  Crítico |
| Compatibilidad con CRXDE | Importante |
| Comprobación de estado de DavEx | Importante |
| Paquetes de contenido de ejemplo | Importante |
| Configuración de filtros WCM | Importante |
| Comprobación de estado de WebDAV | Importante |
| Configuración de servidor web | Importante |
| Replicación y usuarios de transporte | Información |

### Implementación de comprobación de calidad por SonarQube {#quality-check-implementation-by-sonarqube}

Como parte de la canalización, como se ilustra más arriba, se escanea el código. Actualmente, SonarQube lo implementa. Tenemos 93 reglas que son una combinación de reglas genéricas de Java y reglas específicas de AEM (incluidas algunas del conjunto de reglas existente de Cognifide). Puede encontrar una lista de estas reglas aquí: [code-quality-rules.xlsx](/help/using/assets/code-quality-rules.xlsx)

A partir de estas reglas, se calcula una variedad de métricas, algunas de las cuales se utilizan como una puerta de calidad antes de permitir una implementación en el entorno de ensayo.

Estos son los umbrales actuales:

| Nombre | Definición | Categoría | Umbral de error |
|--- |--- |--- |--- |
| Clasificación de seguridad | A = 0 Vulnerabilidad <br/>B = al menos 1 vulnerabilidad<br/> menor C = al menos 1 vulnerabilidad grave <br/>D = al menos 1 vulnerabilidad crítica <br/>E = al menos 1 vulnerabilidad de bloqueador |  Crítico | &lt; B |
| Clasificación de confiabilidad | A = 0 Error <br/>B = al menos 1 Error menor <br/>C = al menos 1 Error mayor <br/>D = al menos 1 Error crítico E = al menos 1 Error de bloqueo | Importante | &lt; C |
| Clasificación de mantenimiento | El costo de corrección sobresaliente de los olores de código es: <br/><ul><li>&lt;=5% del tiempo que ya ha pasado a la aplicación, la clasificación es A </li><li>entre el 6 y el 10 % la calificación es B </li><li>entre el 11 y el 20 % la calificación es una C </li><li>entre el 21 y el 50 % la calificación es una D</li><li>cualquier cosa superior al 50% es una E</li></ul> | Importante | &lt; A |
| Cobertura | Una combinación de cobertura de línea y cobertura de condición usando esta fórmula: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)` <br/>donde: CT = condiciones que se han evaluado en 'true' al menos una vez <br/>CF = condiciones que se han evaluado en 'false' al menos una vez <br/>LC = líneas cubiertas = líneas_to_cover - líneas_descubiertas <br/><br/> B = número total de condiciones <br/>EL = número total de líneas ejecutables (líneas_to_cover) | Importante | &lt; 50% |
| Pruebas unitarias omitidas | Número de pruebas unitarias omitidas. | Información | &gt; 1 |
| Problemas abiertos | Tipos de problemas generales: Vulnerabilidades, errores y huecos de código | Información | &gt; 1 |
| Líneas duplicadas | Número de líneas involucradas en bloques duplicados. <br/>Para que un bloque de código se considere como duplicado: <ul><li> **Proyectos que no son de Java:**</li><li>Debe haber al menos 100 tokens sucesivos y duplicados.</li><li>Estos tokens deben propagarse al menos en: </li><li>30 líneas de código para COBOL </li><li>20 líneas de código para ABAP </li><li>10 líneas de código para otros idiomas</li></ul><ul><li>**Proyectos de Java:**</li><li> Debe haber al menos 10 declaraciones sucesivas y duplicadas, independientemente del número de tokens y líneas.</li></ul>Las diferencias en sangría y en literales de cadena se omiten al detectar duplicaciones. | Información | &gt; 1% |

### Falsos positivos {#false-positives}

El proceso de análisis de calidad no es perfecto y a veces identifica incorrectamente problemas que no son realmente problemáticos. Esto se denomina *falso positivo* (aunque *falso negativo* probablemente sería más semánticamente correcto). En estos casos, el código fuente se puede anotar con la anotación estándar de Java `@SuppressWarnings` que especifica el ID de la regla como el atributo de anotación. Por ejemplo, un problema común es que la regla SonarQube para detectar contraseñas codificadas es muy liberal sobre lo que considera una contraseña codificada.

Para ver un ejemplo específico, este código sería bastante común en un proyecto de AEM que tiene código para conectarse a algún servicio externo:

```java
@Property(label = "Service Password")
private static final String SERVICE_PASSWORD = "password";
```

SonarQube elevará esto como una vulnerabilidad de bloqueador. En este caso, el cliente puede identificar que no se trata de una vulnerabilidad y anotarla con la identificación de regla adecuada:

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String SERVICE_PASSWORD = "password";
```

Sin embargo, por otro lado, si el código era en realidad esto:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String SERVICE_PASSWORD = "password";
```

Entonces el cliente debe tomar en serio la advertencia de SonarQube y eliminar la contraseña codificada. Sin embargo, aún tendrán que agregar la `@SuppressWarnings` anotación ya que la regla SonarQube está siendo activada por el término `password`.

>[!NOTE]
>
>Se recomienda que la anotación sea lo más específica posible, es decir, que solo tenga en cuenta la afirmación o el bloque específico que causa el problema; es posible realizar anotaciones en un nivel de clase. `@SuppressWarnings`

