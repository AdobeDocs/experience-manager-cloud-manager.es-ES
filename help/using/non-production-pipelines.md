---
title: Configuración de canalizaciones que no son de producción
description: Aprenda a utilizar Cloud Manager para crear y configurar canalizaciones que no son de producción e implementar su código.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 567a16a032bf80451b5e8ba4e3d842cb617a615f
workflow-type: ht
source-wordcount: '600'
ht-degree: 100%

---

# Configuración de canalizaciones que no son de producción {#configuring-non-production-pipelines}

Aprenda a utilizar Cloud Manager para crear y configurar canalizaciones que no son de producción e implementar su código. Si desea conocer primero una descripción general más conceptual del funcionamiento de las canalizaciones en Cloud Manager, consulte el documento [Canalizaciones de CI/CD.](/help/overview/ci-cd-pipelines.md)

## Información general {#overview}

Con el mosaico **Canalizaciones** en [!UICONTROL Cloud Manager], el **Administrador de implementación** puede crear dos tipos diferentes de canalizaciones.

* **Canalizaciones de producción**: una canalización de producción está estructurada y formada específicamente por una serie de pasos organizados para llevar el código fuente hasta la producción.
* **Canalizaciones que no son de producción**: una canalización que no es de producción sirve principalmente para ejecutar un análisis de calidad del código o para implementar código fuente en un entorno de desarrollo.

Este documento se centra en las canalizaciones que no son de producción. Para obtener más información sobre cómo configurar canalizaciones de producción, consulte el documento [Configuración de canalizaciones de producción.](/help/using/production-pipelines.md)

Existen dos tipos de canalizaciones que no son de producción:

* **Canalizaciones de calidad de código**: ejecutan análisis de calidad del código en el código de una rama de Git y ejecutan los pasos de compilación y calidad del código.
* **Canalizaciones de implementación**: además de ejecutar los pasos de compilación y calidad del código como las canalizaciones de calidad del código, estas lo implementan en un entorno que no es de producción.

>[!NOTE]
>
>No se puede configurar una canalización hasta que su repositorio de Git asociado tenga al menos una rama y la [configuración del programa](/help/getting-started/program-setup.md) haya finalizado. Consulte el documento [Repositorios de Cloud Manager](/help/managing-code/repositories.md) para aprender a añadir y administrar repositorios en Cloud Manager.

## Tutorial de vídeo {#video-tutorial}

Este vídeo ofrece información general sobre el proceso de creación de canalizaciones, que se detalla en este documento.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

## Adición de una canalización que no es de producción {#add-non-production-pipeline}

Una vez que haya configurado el programa y tenga al menos un entorno utilizando la IU de Cloud Manager, estará listo para agregar una canalización que no es de producción siguiendo estos pasos.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) y seleccione la organización y el programa adecuados.

1. Acceda a la tarjeta Canalizaciones desde la pantalla de inicio de Cloud Manager. Haga clic en **Agregar** y seleccione **Agregar canalización que no sea de producción**.

   ![Agregar canalización que no sea de producción](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. En la pestaña **Configuración** del cuadro de diálogo **Agregar canalización que no sea de producción**, seleccione el tipo de canalización que desea crear, ya sea una **Código de calidad de la canalización** o una **Canalización de implementación**.

   ![Elección del tipo de canalización](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. Proporcione una descripción para la canalización en el campo **Nombre de la canalización que no es de producción**.

1. Si decide añadir una **Canalización de implementación**, seleccione el entorno de implementación de destinatario en la lista desplegable **Entornos de implementación aptos**.

1. Proporcione el repositorio donde la canalización debe obtener el código.

   * **Repositorio**: esta opción define desde qué repositorio de Git debe obtener el código la canalización.
   * **Rama Git**: esta opción define desde qué rama de la canalización seleccionada debe recuperar el código.

1. Defina las opciones de implementación.

   1. En **Activador de implementación**, defina qué evento activa la canalización.

      * **Manual**: utilice esta opción para iniciar manualmente la canalización.
      * **Cambios en Git**: esta opción inicia la canalización cada vez que se añaden confirmaciones a la rama de Git configurada. Con esta opción, sigue pudiendo iniciar la canalización de forma manual según sea necesario.
   1. Para canalizaciones de implementación, en **Comportamiento de los errores de las métricas importantes**, defina el comportamiento de la canalización cuando se encuentre un error importante en cualquiera de las puertas de acceso de calidad.

      * **Preguntar cada vez**: esta es la configuración predeterminada y requiere intervención manual en caso de que se produzca algún error importante.
      * **Produjo un error inmediatamente**: si se selecciona, la canalización se cancelará siempre que se produzca un fallo importante. Básicamente, esto emula a un usuario rechazando manualmente cada error.
      * **Continuar inmediatamente**: si se selecciona, la canalización se realizará automáticamente cada vez que se produzca un error importante. Básicamente, esto emula al usuario que aprueba manualmente cada error.


1. Haga clic en **Guardar** para guardar la canalización.

## Pasos siguientes {#the-next-steps}

Una vez configurada la canalización, debe implementar el código. Consulte el documento [Implementación de código](/help/using/code-deployment.md) para obtener más información.
