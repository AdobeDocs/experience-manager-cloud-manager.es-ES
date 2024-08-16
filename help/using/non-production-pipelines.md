---
title: Configurar canalizaciones que no sean de producción
description: Aprenda a utilizar Cloud Manager para crear y configurar canalizaciones que no son de producción e implementar su código.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: ba08da1b25a1f9ba8bc954b2fbd27b60d4ddf1a0
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 55%

---

# Configuración de canalizaciones que no sean de producción {#configuring-non-production-pipelines}

Aprenda a utilizar Cloud Manager para crear y configurar canalizaciones que no son de producción e implementar su código. Si desea conocer primero una descripción general más conceptual del funcionamiento de las canalizaciones en Cloud Manager, consulte [Canalizaciones de CI/CD](/help/overview/ci-cd-pipelines.md).

## Información general {#overview}

Con el mosaico **Canalizaciones** en [!UICONTROL Cloud Manager], el **Administrador de implementación** puede crear dos tipos diferentes de canalizaciones.

* **Canalizaciones de producción**: una canalización de producción está estructurada y formada específicamente por una serie de pasos organizados para llevar el código fuente hasta la producción.
* **Canalizaciones que no son de producción**: una canalización que no es de producción sirve principalmente para ejecutar un análisis de calidad del código o para implementar código fuente en un entorno de desarrollo.

Este documento se centra en las canalizaciones que no son de producción. Para obtener más información sobre cómo configurar canalizaciones de producción, consulte el documento [Configuración de canalizaciones de producción](/help/using/production-pipelines.md).

Existen dos tipos de canalizaciones que no son de producción:

* **Canalizaciones de calidad de código**: ejecutan análisis de calidad del código en el código de una rama Git y ejecutan los pasos de compilación y calidad del código.
* **Canalizaciones de implementación**: además de realizar los pasos de compilación y calidad del código como las canalizaciones de calidad del código, estas también implementan el código en un entorno que no es de producción.

>[!NOTE]
>
>No se puede configurar una canalización hasta que su repositorio de Git asociado tenga al menos una rama y se haya completado la configuración del [programa](/help/getting-started/program-setup.md). Consulte [Repositorios de Cloud Manager](/help/managing-code/managing-repositories.md) para obtener información sobre cómo agregar y administrar repositorios en Cloud Manager.

## Agregar una canalización que no sea de producción {#add-non-production-pipeline}

Una vez que haya configurado el programa y tenga al menos un entorno utilizando la interfaz de usuario de Cloud Manager, estará listo para agregar una canalización que no sea de producción siguiendo estos pasos.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) y seleccione la organización y el programa adecuados.

1. Acceda a la tarjeta Canalizaciones desde la pantalla de inicio de Cloud Manager. Haga clic en **Agregar** y luego seleccione **Agregar canalización que no sea de producción**.

   ![Agregar canalización que no sea de producción](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. En la pestaña **Configuración** del cuadro de diálogo **Agregar canalización que no sea de producción**, seleccione el tipo de canalización que desea crear, ya sea una **Código de calidad de la canalización** o una **Canalización de implementación**.

   ![Elección del tipo de canalización](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. Proporcione una descripción para la canalización en el campo **Nombre de la canalización que no es de producción**.

1. Si decide añadir una **Canalización de implementación**, seleccione el entorno de implementación de destinatario en la lista desplegable **Entornos de implementación aptos**.

1. Proporcione el repositorio donde la canalización debe obtener el código.

   * **Repositorio**: define desde qué repositorio de Git la canalización debe recuperar el código.
   * **Rama de Git**: define desde qué rama de Git la canalización seleccionada debe recuperar el código.

1. Defina las opciones de implementación.

   1. En **Activador de implementación**, defina qué evento activa la canalización.

      * **Manual**: le permite iniciar manualmente la canalización.
      * **Cambios en Git**: inicia la canalización cuando se agregan confirmaciones a la rama Git configurada. Con esta opción, aún puede iniciar la canalización manualmente, según sea necesario.

   1. Para canalizaciones de implementación, en **Comportamiento de los errores de las métricas importantes**, defina el comportamiento de la canalización cuando se encuentre un error importante en cualquiera de las puertas de acceso de calidad.

      * **Preguntar cada vez**: la configuración predeterminada y requiere intervención manual en caso de que se produzca algún error importante.
      * **Error inmediato**: la canalización se cancela cada vez que se produce un error importante. Se trata, básicamente, de emular a un usuario que rechaza errores manualmente.
      * **Continuar inmediatamente**: la canalización se ejecuta automáticamente cada vez que se produce un error importante. Se trata, básicamente, de emular a un usuario que aprueba manualmente cada fallo.

   1. **Configuración de Dispatcher AEM** - El rol **Administrador de implementación** puede configurar un conjunto de rutas de contenido que se invalidan o se vacían de la caché de Dispatcher de la cuando se ejecuta una canalización. Estas acciones de caché se realizan como parte del paso de canalización de implementación, justo después de implementar cualquier paquete de contenido. Esta configuración utiliza el comportamiento estándar de AEM Dispatcher. Para configurarlo, haga lo siguiente:

      1. En **RUTA**, proporcione una ruta de contenido.
      1. En **TIPO**, seleccione la acción que se realizará en esa ruta.

         * **Vaciado**: realice una eliminación de caché.
         * **Invalidar**: efectúe una invalidación de caché, similar a cuando el contenido se activa desde una instancia de creación a una instancia de publicación.

      1. Haga clic en **Agregar ruta** para añadir la ruta especificada. Puede agregar hasta 100 rutas por entorno.

1. Haga clic en **Guardar**.

## Los siguientes pasos {#the-next-steps}

Después de configurar la canalización, puede implementar el código. Consulte [Implementación de código](/help/using/code-deployment.md) para obtener más información.

## Tutorial de vídeo {#video-tutorial}

Este vídeo ofrece información general sobre el proceso de creación de canalizaciones, que se detalla en este documento.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
