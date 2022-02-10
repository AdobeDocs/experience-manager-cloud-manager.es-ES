---
title: Configuración de canalizaciones que no sean de producción
description: Aprenda a utilizar Cloud Manager para crear y configurar canalizaciones que no sean de producción con el fin de implementar su código.
source-git-commit: 205113735cc743e11e140b1161413002844f5b79
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---


# Configuración de canalizaciones que no sean de producción {#configuring-non-production-pipelines}

Aprenda a utilizar Cloud Manager para crear y configurar canalizaciones que no sean de producción con el fin de implementar su código. si desea primero una descripción general más conceptual del funcionamiento de las canalizaciones en Cloud Manager, consulte la [Documentación general de la canalización CI/CD.](ci-cd-pipeline.md)

>[!NOTE]
>
>Para obtener información sobre cómo configurar canalizaciones de CI/CD para Cloud Manager en AEM as a Cloud Service, consulte [la documentación de AEMaaCS.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html#using-cloud-manager)

## Información general {#understanding-the-flow}

La variable **Administrador de implementación** es responsable de configurar la canalización mediante la función **Canalizaciones** en el [!UICONTROL Cloud Manager] IU.

Puede crear dos tipos diferentes de canalizaciones.

* **Canalizaciones de producción** - Una canalización de producción es una canalización diseñada específicamente y formada por una serie de pasos organizados para llevar el código fuente hasta la producción.
* **Canalizaciones que no son de producción** : una canalización que no es de producción sirve principalmente para ejecutar análisis de calidad del código o para implementar código fuente en un entorno de desarrollo.

Este documento se centra en las canalizaciones que no son de producción. Para obtener más información sobre cómo configurar canalizaciones que no sean de producción, consulte el documento [Configuración de canalizaciones que no sean de producción.](configuring-non-production-pipelines.md)

Existen dos tipos de canalizaciones que no son de producción:

* **Canalizaciones de calidad de código** : ejecutan análisis de calidad del código en el código de una rama de Git y ejecutan los pasos de compilación y calidad del código.
* **Canalizaciones de implementación** - Además de ejecutar los pasos de compilación y calidad del código como las canalizaciones de calidad del código, estas canalizaciones implementan el código en un entorno que no es de producción.

>[!NOTE]
>
>No se puede configurar una canalización hasta que su repositorio de Git asociado tenga al menos una rama y [configuración del programa](setting-up-program.md) ha finalizado. Consulte [Adición y administración de repositorios](cloud-manager-repositories.md) para aprender a añadir y administrar repositorios en Cloud Manager.

## Tutorial de vídeo {#video-tutorial-two}

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

## Adición de una canalización que no sea de producción {#add-non-production-pipeline}

Una vez que haya configurado el programa y tenga al menos un entorno utilizando la interfaz de usuario de Cloud Manager, estará listo para agregar una canalización que no sea de producción siguiendo estos pasos.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) y seleccione la organización y el programa adecuados.

1. Acceda a la tarjeta Canalizaciones desde la pantalla de inicio de Cloud Manager. Haga clic en **Agregar** y seleccione **Agregar canalización que no sea de producción**.

   ![Añadir canalización que no sea de producción](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. En el **Configuración** de la pestaña **Agregar canalización que no sea de producción** , seleccione el tipo de canalización que desea crear, ya sea una **Canalización de calidad de código** o **Canalización de implementación**.


   ![Elegir tipo de canalización](/help/using/assets/configure-pipelines/add-non-production-pipeline.png)

1. Proporcione una descripción para la canalización en el **Nombre de canalización que no es de producción** campo .

1. Si decide agregar una **Canalización de implementación**, seleccione el entorno de implementación de destino en el **Entornos de implementación aptos** lista desplegable.

1. Proporcione el repositorio donde la canalización debe recuperar el código.

   * **Repositorio** - Esta opción define desde qué repositorio de Git la canalización debe recuperar el código.
   * **Rama de Git** : esta opción define desde qué rama de la canalización seleccionada debe recuperar el código.

1. Defina las opciones de implementación.

   1. En **Déclencheur de implementación**, defina qué evento activa la canalización.

      * **Manual** - Utilice esta opción para iniciar manualmente la canalización.
      * **Cambios en Git** - Esta opción inicia la canalización cada vez que se añaden confirmaciones a la rama git configurada. Con esta opción, aún puede iniciar la canalización manualmente según sea necesario.
   1. En **Comportamiento de errores de métricas importantes**, defina el comportamiento de la canalización cuando se encuentre un error importante en cualquiera de las puertas de calidad.

      * **Pregunte cada vez** - Esta es la configuración predeterminada y requiere intervención manual en caso de que se produzca algún error importante.
      * **Fallo Inmediatamente** - Si se selecciona, la canalización se cancelará siempre que se produzca un fallo importante. Básicamente, esto emula a un usuario rechazando manualmente cada error.
      * **Continuar inmediatamente** - Si se selecciona, la canalización se realizará automáticamente cada vez que se produzca un error importante. Básicamente, esto está emulando a un usuario que aprueba manualmente cada error.


1. Haga clic en **Guardar** para guardar la canalización.

## Pasos siguientes {#the-next-steps}

Una vez configurada la canalización, debe implementar el código.

Consulte el documento [Implementar el código](deploying-code.md) para obtener más información.
