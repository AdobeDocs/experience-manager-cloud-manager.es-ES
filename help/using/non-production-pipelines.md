---
title: Adición de una canalización que no es de producción
description: Aprenda a utilizar Cloud Manager para crear y configurar canalizaciones que no son de producción e implementar su código.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 57de7b00b382e4fb65ad3e03948960022ec02de1
workflow-type: tm+mt
source-wordcount: '1992'
ht-degree: 27%

---

# Adición de una canalización que no es de producción {#configuring-non-production-pipelines}

Aprenda a utilizar Cloud Manager para crear y configurar canalizaciones que no son de producción e implementar su código. Si desea conocer primero una descripción general más conceptual del funcionamiento de las canalizaciones en Cloud Manager, consulte el documento [Canalizaciones de CI/CD](/help/overview/ci-cd-pipelines.md).

## Información general {#overview}

Con el mosaico **Canalizaciones** en [!UICONTROL Cloud Manager], el **Administrador de implementación** puede crear dos tipos diferentes de canalizaciones.

* **Canalizaciones de producción**: una canalización de producción está estructurada y formada específicamente por una serie de pasos organizados para llevar el código fuente hasta la producción.
* **Canalizaciones que no son de producción**: una canalización que no es de producción sirve principalmente para ejecutar un análisis de calidad del código o para implementar código fuente en un entorno de desarrollo.

Este documento se centra en las canalizaciones que no son de producción. Para obtener más información sobre cómo configurar canalizaciones de producción, consulte el documento [Configuración de canalizaciones de producción](/help/using/production-pipelines.md).

Existen dos tipos de canalizaciones que no son de producción:

* **Canalizaciones de calidad del código**: ejecutan análisis de calidad del código de una rama de Git y ejecutan los pasos de compilación y calidad del código.
* **Canalizaciones de implementación**: además de ejecutar los pasos de compilación y calidad del código como las canalizaciones de calidad del código, estas lo implementan en un entorno que no es de producción.

>[!NOTE]
>
>No se puede configurar una canalización hasta que su repositorio de Git asociado tenga al menos una rama y la [configuración del programa](/help/getting-started/program-setup.md) haya finalizado. Consulte el documento [Repositorios de Cloud Manager](/help/managing-code/managing-repositories.md) para aprender a añadir y administrar repositorios en Cloud Manager.

## Adición de una nueva canalización que no es de producción {#add-non-production-pipeline}

Después de configurar un programa y tener al menos un entorno usando la interfaz de usuario de Cloud Manager, puede agregar canalizaciones que no sean de producción para probar la calidad del código antes de implementarlas en entornos de producción.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) y seleccione la organización y el programa adecuados.

1. Acceda a la tarjeta Canalizaciones desde la pantalla de inicio de Cloud Manager. Haga clic en **+Agregar** y seleccione **Añadir canalización que no es de producción**.

   ![Agregar canalización que no sea de producción](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. En la ficha **Configuración** del cuadro de diálogo **Agregar canalización que no sea de producción**, seleccione el tipo de canalización que desea crear, ya sea una de las siguientes:

   * **Canalización de calidad de código**: crea una canalización que genera el código, ejecuta pruebas unitarias y evalúa la calidad del código sin implementarlo en un entorno.
   * **Canalización de implementación**: crea una canalización que genera el código, ejecuta pruebas unitarias, evalúa la calidad del código y se implementa en un entorno.

   ![Elección del tipo de canalización](/help/using/assets/add-non-production-pipeline-cm-ams.png)

>[!BEGINTABS]

>[!TAB Canalización de calidad de código: ficha Configuración]

| Sección | Opción | Descripción |
| --- | --- | --- |
| **Configuración de canalización** | **Nombre de canalización que no es de producción** | Proporcione una descripción para la canalización en el campo **Nombre de la canalización que no es de producción**. |
|  | **Pruebas** | Solo visible al editar una canalización que no es de producción.<br>La interfaz de usuario muestra las categorías de prueba que ejecuta la canalización como parte de la validación de calidad del código.<ul><li>**Prueba de código estático**: analiza el código para detectar problemas de calidad y corrección.<li>**Prueba de carga/rendimiento**: evalúa el comportamiento relacionado con el rendimiento como parte de las pruebas de canalización.<li>**Prueba de seguridad**: comprueba el código y el resultado de la canalización en busca de problemas relacionados con la seguridad. |
| **Opciones de implementación** | **Déclencheur de implementación** | <ul><li>**Manual**: Le permite iniciar manualmente la canalización.<li>**Cambios en Git**: Inicia la canalización cuando se añaden confirmaciones a la rama de Git configurada. Con esta opción, aún puede iniciar la canalización manualmente, según sea necesario. |
|  | **Comportamiento de errores de métricas importantes** | <ul><li>**Preguntar cada vez**: esta es la configuración predeterminada y requiere intervención manual en caso de que se produzca algún error importante.<li>**Error inmediato**: si se selecciona, la canalización se cancela cada vez que se produce un error importante. Básicamente, emula a un usuario rechazando manualmente cada error.<li>**Continuar inmediatamente**: si se selecciona, la canalización se ejecuta automáticamente cada vez que se produce un error importante. Básicamente, emula al usuario que aprueba manualmente cada error.</li></ul> |
|  | **Aprobar después de la implementación de la fase** | Solo visible al editar una canalización que no sea de producción.<br>Seleccione esta opción para requerir aprobación después de la implementación en el entorno de ensayo antes de que la canalización pueda continuar. Si no se selecciona esta opción, la canalización continúa según el comportamiento configurado. |

>[!TAB Canalización de implementación: ficha Configuración]

| Sección | Opción | Descripción |
| --- | --- | --- |
| **Configuración de canalización** | **Nombre de canalización que no es de producción** | Proporcione una descripción para la canalización en el campo **Nombre de la canalización que no es de producción**. |
|   | **Entorno de implementación elegible** | Si la canalización es una canalización de implementación, debe seleccionar qué entornos donde Cloud Manager implementa el código. |
|   | **Pruebas** | Solo visible al editar una canalización que no es de producción.<br>La interfaz de usuario muestra las categorías de prueba que ejecuta la canalización como parte de la validación de calidad del código.<ul><li>**Prueba de código estático**: analiza el código para detectar problemas de calidad y corrección.<li>**Prueba de carga/rendimiento**: evalúa el comportamiento relacionado con el rendimiento como parte de las pruebas de canalización.<li>**Prueba de seguridad**: comprueba el código y el resultado de la canalización en busca de problemas relacionados con la seguridad.</li></ul> |
| **Opciones de implementación** | **Déclencheur de implementación** | <ul><li>**Manual**: Le permite iniciar manualmente la canalización.<li>**Cambios en Git**: Inicia la canalización cuando se añaden confirmaciones a la rama de Git configurada. Con esta opción, aún puede iniciar la canalización manualmente, según sea necesario. |
|   | **Comportamiento de errores de métricas importantes** | <ul><li>**Preguntar cada vez**: la configuración predeterminada y pide al usuario que decida cómo continuar cuando falle una métrica importante.<li>**Error inmediato**: la canalización se cancela cada vez que falla una métrica importante. Se trata, básicamente, de emular a un usuario que rechaza errores manualmente.<li>**Continuar inmediatamente**: la canalización se ejecuta automáticamente cada vez que falla una métrica importante. Se trata, básicamente, de emular a un usuario que aprueba manualmente cada fallo.</li></ul> |
|  | **Aprobar después de la implementación de la fase** | Solo visible al editar una canalización que no sea de producción.<br>Seleccione esta opción para requerir aprobación después de la implementación en el entorno de ensayo antes de que la canalización pueda continuar. Si no se selecciona esta opción, la canalización continúa según el comportamiento configurado. |
|  | **Omitir cambios del equilibrador de carga** | Seleccione esta opción para evitar que la canalización realice cambios en el equilibrador de carga durante el despliegue. |
|  | **Configuración de Dispatcher** | El rol **Administrador de implementación** puede configurar un conjunto de rutas de contenido que se invalidan o se vacían de la caché de AEM Dispatcher cuando se ejecuta una canalización. Estas acciones de caché se ejecutan como parte del paso de canalización de implementación, justo después de implementar cualquier paquete de contenido. Esta configuración utiliza el comportamiento estándar de AEM Dispatcher. Para configurar `Dispatcher`, haga lo siguiente:<ul><li>En **RUTA**, proporcione una ruta de contenido que quiera que la canalización vacíe o invalide.<li>En **TIPO**, seleccione la acción que se realizará en esa ruta.<ul><li>**Vaciar**: realice una eliminación de caché en la ruta de acceso especificada.</li><li>**Invalidar**: efectúe una invalidación de caché, similar a cuando el contenido se activa desde una instancia de creación a una instancia de publicación.</li><li>Haga clic en **Agregar ruta** para añadir la ruta especificada. Puede agregar hasta 100 rutas por entorno.</li></ul> |
| **Canalización** | **Auditoría de experiencias** casilla de verificación | Seleccione esta opción para incluir un paso Auditoría de experiencias en la canalización. Cuando se habilita, la canalización incluye el paso Auditoría de experiencias después de la pestaña Código de Source. |

>[!ENDTABS]

1. En la esquina inferior derecha del cuadro de diálogo **Agregar canalización que no sea de producción**, haga clic en **Continuar**.
1. Seleccione el tipo de código que la canalización está configurada para generar e implementar.

>[!BEGINTABS]

>[!TAB Pestaña Código Source - Código de pila completa]

Implementa la aplicación AEM completa, incluido el código de la aplicación y, de forma predeterminada, la configuración del nivel web.

| Sección | Opción | Descripción |
| --- | --- | --- |
| **Código Source** | **Repositorio** | En la lista desplegable, elija el repositorio de Git que la canalización utiliza como origen. Cloud Manager genera código a partir del repositorio que elija aquí. |
|   | **Rama Git** | En la lista desplegable, elija desde qué rama del repositorio seleccionado debe crearse la canalización. El valor predeterminado es `main`. La canalización utiliza la rama elegida como origen para la compilación y la implementación. Si es necesario, haga clic en **Actualizar** para actualizar la lista de ramas disponibles para el repositorio seleccionado. Utilice esta opción si una rama creada recientemente no aparece en la lista. |
|   | **Estrategia de compilación** | <ul><li>**Compilación completa**: genera todos los módulos del repositorio cada vez<li>BETA **Smart Build**: genera solo módulos que han cambiado desde la última confirmación.<br>Obtenga más información acerca de [cómo usar Smart Build en una canalización que no es de producción](#about-smart-build).</li></ol>**Importante**: La compilación inteligente solo está disponible para canalizaciones de calidad de código y canalizaciones de implementación de código de pila completa de desarrolladores. |
|   | **Ignorar configuración de nivel web** | Seleccione esta opción para omitir la implementación de la configuración del nivel web en una canalización de código de pila completa. Deje la opción sin seleccionar para implementar la configuración del nivel web junto con el código de la canalización. |
| **Canalización** | **Auditoría de experiencias** casilla de verificación | Seleccione esta opción para incluir un paso Auditoría de experiencias en la canalización. Cuando se habilita, la canalización incluye el paso Auditoría de experiencias después de la pestaña Código de Source. |

>[!TAB Código Source - Configuración de nivel web]

Implementa únicamente la configuración del nivel web, como las propiedades de Dispatcher utilizadas para almacenar, procesar y enviar páginas web al cliente. Al seleccionar **Configuración de nivel web**, Cloud Manager crea una canalización dedicada a la implementación de la configuración del nivel web.

Si ya existe una canalización de pila completa, Cloud Manager muestra un aviso de que la creación de una canalización de configuración de capa web hace que la canalización de pila completa existente ignore la configuración de la capa web. Después de crear la canalización de configuración de nivel web, Cloud Manager administra las implementaciones de configuración de nivel web a través de esa canalización en lugar de la canalización de pila completa.

| Sección | Opción | Descripción |
| --- | --- | --- |
| **Código Source** | **Repositorio** | En la lista desplegable, seleccione el repositorio Git que contiene la configuración del nivel web. |
|   | **Rama Git** | Seleccione la rama del repositorio elegido que Cloud Manager utiliza para la implementación. Si es necesario, haga clic en **Actualizar** para actualizar la lista de ramas disponibles para el repositorio seleccionado. Utilice esta opción si una rama creada recientemente no aparece en la lista. |
|   | **Ubicación del código** | Introduzca la ruta en el repositorio seleccionado que contiene la configuración del nivel web que se va a desplegar. La ubicación predeterminada es la raíz del repositorio (`/`). |

>[!ENDTABS]

1. Haga clic en **Guardar**.

## Acerca del uso de Smart Build en una canalización que no es de producción{#about-smart-build}

**Smart Build** en Cloud Manager es una estrategia de compilación optimizada para canalizaciones que no son de producción. La versión inteligente reduce los tiempos de compilación al almacenar en caché los módulos y reconstruir solo los módulos que han cambiado desde la última ejecución correcta. Los módulos no modificados se reutilizan desde la caché, mientras que solo se reconstruyen los módulos modificados y sus dependencias, lo que mejora la eficacia de los flujos de trabajo de desarrollo iterativos.

Actualmente, Smart Build solo está disponible para lo siguiente:

* Código de calidad de las canalizaciones.
* Desarrollo de canalizaciones de implementación de pila completa.

>[!NOTE]
>
>La primera ejecución después de habilitar Smart Build se comporta como una compilación completa porque la caché está vacía.

Se recomienda Smart Build cuando se dispone de lo siguiente:
* Está desarrollando y comprometiendo activamente cambios incrementales frecuentes.
* El proyecto contiene varios módulos Maven.
* Las compilaciones completas están tardando un tiempo considerable.

Smart Build no siempre es ideal cuando se tiene lo siguiente:
* Su compilación se basa en gran medida en complementos que realizan operaciones fuera del gráfico de dependencias de Maven.
* Se requiere una validación de regeneración completa en cada ejecución.

### Comprender el rendimiento de compilación{#smart-build-performance}

La mejora del rendimiento obtenida mediante el uso de Smart Build depende de varios factores, entre los que se incluyen los siguientes:

* Número de módulos del proyecto.
* La frecuencia y el ámbito del código cambian.
* La distribución de dependencias entre módulos.

Por lo general, los proyectos con muchos módulos independientes son los que experimentan la mayor mejora.

### Exclusión de caché por módulo{#smart-build-cache-optout}

Smart Build proporciona un control detallado que le permite deshabilitar el almacenamiento en caché para módulos específicos. Esta capacidad es útil cuando se utilizan ciertos módulos:

* Use complementos, como `exec-maven-plugin` o `maven-antrun-plugin`.
* Realizar operaciones de archivo no rastreadas por dependencias de Maven.
* Produzca resultados incoherentes cuando se almacene en caché.

### Deshabilitar el almacenamiento en caché de un módulo{#smart-build-disable-caching}

Puede agregar la siguiente propiedad al `pom.xml` del módulo afectado:

```xml
<properties>
  <maven.build.cache.enabled>false</maven.build.cache.enabled>
</properties>
```

Esta sintaxis fuerza al módulo a reconstruir en cada ejecución de canalización, mientras que otros módulos siguen beneficiándose del almacenamiento en caché.

### Limitaciones y consideraciones al utilizar Smart Build{#smart-build-limitations}

Tenga en cuenta lo siguiente al utilizar Smart Build:

* La generación inteligente se basa en el análisis de dependencias de Maven.
* Los cambios fuera del gráfico de dependencias no pueden almacenar en déclencheur las regeneraciones.
* Es posible que algunos complementos no sean totalmente compatibles con el almacenamiento en caché.
* Puede volver a **Compilación completa** en cualquier momento editando la canalización que no sea de producción.

Si encuentra un comportamiento de compilación inesperado, considere la posibilidad de deshabilitar el almacenamiento en caché para módulos específicos o cambiar temporalmente su estrategia de compilación a **Compilación completa**.

### Solución de problemas de Smart Build{#smart-build-troubleshoot}

| Problema | Soluciones sugeridas |
| --- | --- |
| Los resultados de la compilación son incoherentes | · Deshabilite el almacenamiento en caché para los módulos afectados.<br>· Compruebe el comportamiento de los complementos (especialmente los complementos `exec`/`antrun`). |
| Sin mejora de rendimiento | · Asegúrese de que se han producido varias ejecuciones (calentamiento de caché).<br>· Compruebe si la mayoría de los módulos cambian con frecuencia. |
| Artefactos inesperados o cambios que faltan | · Revise si los cambios están fuera del seguimiento de dependencias de Maven.<br>· Use **Compilación completa** para la verificación. |

Consulte [Agregar una canalización que no sea de producción](#add-non-production-pipeline) para habilitar Smart Build.



<!-- 
1. If you chose to add a **Deployment Pipeline**, select the target deployment environment from the **Eligible Deployment Environments** dropdown.

1. Provide the repository where the pipeline should retrieve the code.

   * **Repository** - Defines from which Git repo that the pipeline should retrieve the code.
   * **Git Branch** - Defines from which branch in Git that the selected pipeline should retrieve the code.

1. Define your deployment options.

   1. Under **Deployment Trigger**, define what event activates the pipeline.

      * **Manual** - Lets you manually start the pipeline.
      * **On Git Changes** - Starts the pipeline when commits are added to the configured Git branch. With this option, you can still start the pipeline manually, as required.

   1. For deployment pipelines, under **Important Metric Failures Behavior**, define the behavior of the pipeline when an important failure is encountered in any of the quality gates.

       * **Ask every time** - The default setting and requires manual intervention on any important failure.
       * **Fail Immediately** - The pipeline is canceled whenever an important failure occurs. It is essentially emulating a user manually rejecting each failure.
       * **Continue Immediately** - The pipeline proceeds automatically whenever an important failure occurs. It is essentially emulating a user manually approving each failure.

   1. **Dispatcher Configuration** - The **Deployment Manager** role can configure a set of content paths that are either invalidated or flushed from the AEM Dispatcher cache when a pipeline is run. These cache actions are performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior. To configure:

      1. Under **PATH** provide a content path.
      1. Under **TYPE**, select the action to be taken on that path.

         * **Flush** - Perform a cache deletion.
         * **Invalidate** - Perform a cache invalidation, similar to when content is activated from an authoring instance to a publishing instance.
         
      1. Click **Add Path** to add your specified path. You can add up to 100 paths per environment.

1. Click **Save**.
-->

## Pasos siguientes {#the-next-steps}

Después de configurar la canalización, puede implementar el código. Consulte la [Implementación de código](/help/using/code-deployment.md) para obtener más información.

## Tutorial de vídeo {#video-tutorial}

Este vídeo ofrece información general sobre el proceso de creación de canalizaciones, que se detalla en este documento.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
