---
title: Adición de una canalización que no es de producción
description: Aprenda a utilizar Cloud Manager para crear y configurar canalizaciones que no son de producción e implementar su código.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 1209faf71edbd74cd87acfe24ec438b98ddd4a3a
workflow-type: ht
source-wordcount: '688'
ht-degree: 100%

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

Una vez que haya configurado el programa y tenga al menos un entorno utilizando la interfaz de usuario de Cloud Manager, estará listo para agregar una canalización que no sea de producción siguiendo estos pasos.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) y seleccione la organización y el programa adecuados.

1. Acceda a la tarjeta Canalizaciones desde la pantalla de inicio de Cloud Manager. Haga clic en **+Agregar** y seleccione **Añadir canalización que no es de producción**.

   ![Agregar canalización que no sea de producción](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. En la pestaña **Configuración** del cuadro de diálogo **Agregar canalización que no sea de producción**, seleccione el tipo de canalización que desea crear, ya sea una **Código de calidad de la canalización** o una **Canalización de implementación**.

   ![Elección del tipo de canalización](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. Proporcione una descripción para la canalización en el campo **Nombre de la canalización que no es de producción**.

1. Si decide añadir una **Canalización de implementación**, seleccione el entorno de implementación de destinatario en la lista desplegable **Entornos de implementación aptos**.

1. Proporcione el repositorio donde la canalización debe obtener el código.

   * **Repositorio**: Define desde qué repositorio de Git la canalización debe recuperar el código.
   * **Rama de Git**: Define desde qué rama de la canalización seleccionada debe recuperar el código.

1. Defina las opciones de implementación.

   1. En **Activador de implementación**, defina qué evento activa la canalización.

      * **Manual**: Le permite iniciar manualmente la canalización.
      * **Cambios en Git**: Inicia la canalización cuando se añaden confirmaciones a la rama de Git configurada. Con esta opción, aún puede iniciar la canalización manualmente, según sea necesario.

   1. Para canalizaciones de implementación, en **Comportamiento de los errores de las métricas importantes**, defina el comportamiento de la canalización cuando se encuentre un error importante en cualquiera de las puertas de acceso de calidad.

      * **Preguntar cada vez**: La configuración predeterminada y requiere intervención manual en caso de que se produzca algún error importante.
      * **Fallo inmediatamente**: La canalización se cancela siempre que se produzca un fallo importante. Se trata, básicamente, de emular a un usuario que rechaza errores manualmente.
      * **Continuar inmediatamente**: La canalización se ejecuta automáticamente cada vez que se produzca un error importante. Se trata, básicamente, de emular a un usuario que aprueba manualmente cada fallo.

   1. **Configuración de Dispatcher**: La función **Administrador de implementación** puede configurar un conjunto de rutas de contenido que se invalidarán o vaciarán de la caché de AEM Dispatcher cuando se ejecute una canalización. Estas acciones de caché se ejecutan como parte del paso de canalización de implementación, justo después de implementar cualquier paquete de contenido. Esta configuración utiliza el comportamiento estándar de AEM Dispatcher. Para configurarlo, haga lo siguiente:

      1. En **RUTA**, proporcione una ruta de contenido.
      1. En **TIPO**, seleccione la acción que se realizará en esa ruta.

         * **Vaciado**: realice una eliminación de caché.
         * **Invalidar**: efectúe una invalidación de caché, similar a cuando el contenido se activa desde una instancia de creación a una instancia de publicación.

      1. Haga clic en **Agregar ruta** para añadir la ruta especificada. Puede agregar hasta 100 rutas por entorno.

1. Haga clic en **Guardar**.

## Pasos siguientes {#the-next-steps}

Después de configurar la canalización, puede implementar el código. Consulte la [Implementación de código](/help/using/code-deployment.md) para obtener más información.

## Tutorial de vídeo {#video-tutorial}

Este vídeo ofrece información general sobre el proceso de creación de canalizaciones, que se detalla en este documento.

>[!VIDEO](https://video.tv.adobe.com/v/327617?captions=spa)
