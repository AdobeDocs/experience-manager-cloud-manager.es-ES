---
title: Configurar la canalización de CD/CI
seo-title: Configure your CI/CD Pipeline
description: Siga esta página para configurar las opciones de canalización desde Cloud Manager.
seo-description: Before you start to deploy your code, you must configure your pipeline settings from the AEM Cloud Manager.
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
feature: CI-CD Pipeline
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 2be8f290b58fff2991f876c37dd1b499bc6c5352
workflow-type: tm+mt
source-wordcount: '1834'
ht-degree: 1%

---

# Configurar la canalización de CD/CI {#configure-your-ci-cd-pipeline}

>[!NOTE]
>Para obtener información sobre cómo configurar la canalización de CI/CD para Cloud Manager en AEM as a Cloud Service, consulte [here](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager).

La siguiente página explica cómo configurar la variable **Canalización**. Para obtener más información conceptual sobre el funcionamiento de la canalización, consulte la [Descripción general de la canalización de CI/CD](ci-cd-pipeline.md).


## Explicación del flujo {#understanding-the-flow}

Puede configurar la canalización desde el mosaico **Configuración de canalización** en la interfaz de usuario de [!UICONTROL Cloud Manager].

El administrador de implementación es responsable de configurar la canalización. Al hacerlo, seleccione primero una rama de la **Repositorio de Git**. La configuración de canalización consta de:

* definición del déclencheur que iniciará la canalización.
* definición de los parámetros que controlan la implementación de producción.
* configuración de los parámetros de prueba de rendimiento.

## Tutorial de vídeo {#video-tutorial-one}

### Configuración de canalización en Cloud Manager {#config-pipeline-video}

La configuración de la canalización de producción CI/CD define el déclencheur que iniciará la canalización, parámetros que controlan la implementación de producción y parámetros de prueba de rendimiento.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## Configuración de la canalización {#setting-up-the-pipeline}

>[!CAUTION]
>
>La canalización no se puede configurar hasta que el repositorio de Git tenga al menos una rama y [Configuración del programa](setting-up-program.md) ha finalizado.

Antes de comenzar a implementar el código, debe configurar la configuración de la canalización desde la [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Puede cambiar la configuración de la canalización después de la configuración inicial.

### Adición de una nueva canalización de producción desde la tarjeta de canalización {#adding-production-pipeline}

Una vez que haya configurado el programa y tenga al menos un entorno usando [!UICONTROL Cloud Manager] La interfaz de usuario de está lista para añadir una canalización de producción.

Siga estos pasos para configurar el comportamiento y las preferencias de la canalización de producción:

1. Vaya a la **Canalizaciones** de la **Información general del programa** página.

1. Haga clic en **+Añadir** y seleccione **Agregar canalización de producción**.

   ![](/help/using/assets/configure-pipelines/add-prod1.png)

1. **Agregar canalización de producción** se abre.

   1. Introduzca la variable **Nombre de canalización**. Puede elegir el **Repositorio** y **Rama de Git**.

      ![](/help/using/assets/configure-pipelines/add-prod2.png)

   1. Puede configurar **Déclencheur de implementación** y **Comportamiento de errores de métricas importantes** from **Opciones de implementación**.

      ![](/help/using/assets/configure-pipelines/add-prod3.png)


      Puede asignar las siguientes déclencheur de implementación para iniciar la canalización:

      * **Manual** : al usar la interfaz de usuario, se inicia manualmente la canalización.
      * **Cambios en Git** - inicia la canalización CI/CD cada vez que se añaden confirmaciones a la rama git configurada. Incluso si selecciona esta opción, siempre puede iniciar la canalización manualmente.

      Durante la configuración o edición de la canalización, el administrador de implementación tiene la opción de definir el comportamiento de la canalización cuando se encuentra un error importante en cualquiera de las puertas de calidad.

      Esto resulta útil para los clientes que desean procesos más automatizados. Las opciones disponibles son:

      * **Pregunte cada vez** - Esta es la configuración predeterminada y requiere una intervención manual en cualquier error importante.
      * **Fallo Inmediatamente** - Si se selecciona, la canalización se cancelará siempre que se produzca un error importante. Básicamente, esto emula a un usuario rechazando manualmente cada error.
      * **Continuar inmediatamente** - Si está seleccionada, la canalización se realizará automáticamente cada vez que se produzca un error importante. Básicamente, esto está emulando a un usuario que aprueba manualmente cada error.
   1. Seleccione el **Opciones de implementación**.

      ![](/help/using/assets/configure-pipelines/add-prod4.png)

      * **Aprobar después de la implementación de la fase** funciona de forma similar a la aprobación antes de la implementación de producción, pero se produce inmediatamente después del paso de implementación de la fase, es decir, antes de que se realice la prueba, en comparación con la aprobación antes de la implementación de producción, que se realiza después de completar todas las pruebas.

      * **Omitir cambios del equilibrador de carga** omite los cambios.
   1. Seleccione el **Configuración de Dispatcher** para Stage. Introduzca la ruta, seleccione la acción de **Tipo** y haga clic en **Agregar ruta**. Puede especificar hasta 100 rutas por entorno.

      ![](/help/using/assets/configure-pipelines/dispatcher-stage.png)

   1. Seleccione el **Opciones de implementación** para producción. Ahora define los parámetros que controlan la implementación de producción.

      ![](/help/using/assets/configure-pipelines/prod-deploymentoptions.png)

      Las tres opciones disponibles son las siguientes:

      * **Usar la aprobación de lanzamiento** : Una implementación debe ser aprobada manualmente por el propietario de una empresa, el administrador de proyectos o el administrador de implementaciones a través de la variable [!UICONTROL Cloud Manager] IU.

      * **Programado** : esta opción permite al usuario activar la implementación de producción programada.

         >[!NOTE]
         >If **Programado** está seleccionada, puede programar la implementación de producción en la canalización **after** la implementación de la fase (y **Usar aprobación de GoLive**, si se ha activado) para esperar a que se establezca una programación. El usuario también puede elegir ejecutar la implementación de producción inmediatamente.
         >
         >Consulte [Implementar el código](deploying-code.md), para configurar la programación de implementación o ejecutar la producción inmediatamente.

         * **Usar la supervisión de CSE** - Un CSE se compromete a iniciar realmente la implementación. Durante la configuración o edición de la canalización cuando la supervisión de CSE está habilitada, el administrador de implementación tiene la opción de seleccionar:

            * **Cualquier CSE**: hace referencia a cualquier CSE disponible
            * **Mi CSE**: hace referencia a un CSE específico asignado al cliente o a su copia de seguridad, si el CSE está fuera de la oficina
   1. Configure el **Configuraciones de Dispatcher** para producción. Introduzca la ruta, seleccione la acción de **Tipo** y haga clic en **Agregar ruta**. Puede especificar hasta 100 rutas por entorno.

      ![](/help/using/assets/configure-pipelines/dispatcher-prod.png)

      Como administrador de implementación, tiene la oportunidad de configurar un conjunto de rutas de contenido que serán **invalidado** o **vaciado** desde la caché de AEM Dispatcher para instancias de publicación, mientras se configura o edita la canalización.

      Puede configurar un conjunto independiente de rutas para la implementación de fase y producción. Si se configura, estas acciones de caché se realizarán como parte del paso de canalización de implementación, justo después de implementar cualquier paquete de contenido. Estas configuraciones utilizan AEM comportamiento estándar de Dispatcher: invalidate realiza una invalidación de caché, similar a cuando el contenido se activa de autor a publicación; flush realiza una eliminación de caché.

      En general, es preferible el uso de la acción de invalidación, pero puede haber casos en los que sea necesario vaciar, especialmente cuando se utilizan AEM bibliotecas de cliente de HTML.

      >[!NOTE]
      >
      >Consulte [Información general de Dispatcher](dispatcher-configurations.md) obtenga más información sobre el almacenamiento en caché de Dispatcher.





1. Haga clic en **Continuar** una vez seleccionadas todas las opciones.

1. Seleccione las opciones de la lista **Prueba de prueba** paso a paso. Puede configurar *AEM Sites* y *AEM Assets* Pruebas de rendimiento, en función de los productos con licencia. Consulte [Pruebas de rendimiento](understand-your-test-results.md#performance-testing) para obtener más información.

   1. Seleccione las opciones de **Entrega de contenido de sitios/Peso de carga distribuido**. Consulte [AEM Sites en pruebas de rendimiento](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-sites) para obtener más información.

      ![](/help/using/assets/configure-pipelines/add-prod5.png)

   1. Seleccione las opciones de **Distribución de pruebas de rendimiento de recursos**. Consulte [AEM Assets en pruebas de rendimiento](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-assets) para obtener más información.

      ![](/help/using/assets/configure-pipelines/add-prod6.png)

1. Haga clic en **Guardar** para completar la adición de la canalización de producción.

### Edición de una canalización de producción {#editing-prod-pipeline}

Puede editar las configuraciones de canalización desde el **Información general del programa** página.

Siga los pasos a continuación para editar la canalización configurada:

1. Vaya a **Canalizaciones** de la **Información general del programa** página.

1. Haga clic en **...** de la variable **Canalizaciones** y haga clic en **Editar**, como se muestra en la figura siguiente.

   ![](/help/using/assets/configure-pipelines/edit-prod1.png)

1. La variable **Editar canalización de producción** se abre.

   1. La variable **Configuración** le permite actualizar el **Nombre de canalización**, **Repositorio**, **Rama de Git**, **Déclencheur de implementación**, **Comportamiento de error de métricas importantes**, **Opciones de implementación** y **Configuraciones de Dispatcher**.

      >[!NOTE]
      >Consulte [Adición y administración de repositorios](/help/using/cloud-manager-repositories.md) para aprender a añadir y administrar repositorios en Cloud Manager.


   1. La variable **Prueba de prueba** proporciona una opción para volver a seleccionar las opciones **Entrega de contenido de sitios/Peso de carga distribuido** y **Distribución de pruebas de rendimiento de recursos**.

1. Haga clic en **Actualizar** una vez que haya terminado de editar la canalización.

### Acciones adicionales de canalización de producción {#additional-prod-actions}

#### Ejecución de una canalización de producción {#run-prod}

Puede ejecutar la canalización de producción desde la tarjeta Canalizaciones:

1. Vaya a **Canalizaciones** de la **Información general del programa** página.

1. Haga clic en **...** de la variable **Canalizaciones** y haga clic en **Ejecutar**, como se muestra en la figura siguiente.

   ![](/help/using/assets/configure-pipelines/prod-run.png)

#### Eliminación de una canalización de producción {#delete-prod}

Puede eliminar la canalización de producción de la tarjeta Canalizaciones:

1. Vaya a **Canalizaciones** de la **Información general del programa** página.

1. Haga clic en **...** de la variable **Canalizaciones** y haga clic en **Eliminar**, como se muestra en la figura siguiente.

   ![](/help/using/assets/configure-pipelines/prod-delete.png)

   >[!NOTE]
   >Un usuario con la función de administrador de implementación ahora puede eliminar la canalización de producción con un método de autoservicio a través del **Eliminar** de la tarjeta Canalización.

## Canalizaciones de calidad de código y no producción

Además de la canalización principal que se implementa en las fases de producción y producción, los clientes pueden configurar canalizaciones adicionales, denominadas **Canalizaciones que no son de producción**. Estas canalizaciones siempre ejecutan los pasos de compilación y calidad del código. Opcionalmente, también pueden implementarse en el entorno de Adobe Managed Services.

## Tutorial de vídeo {#video-tutorial-two}

### Canalizaciones de calidad de código y no producción de Cloud Manager {#non-prod-video}

Las canalizaciones no productivas de CI/CD se dividen en dos categorías, las canalizaciones de calidad del código y las canalizaciones de implementación. La calidad del código canaliza todo el código de una rama de Git para crearlo y evaluarlo en relación con el análisis de calidad del código de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

### Adición de una canalización que no sea de producción {#add-non-production-pipeline}

En la pantalla de inicio, estas canalizaciones se enumeran en una tarjeta nueva:

1. Acceda a la **Canalizaciones** de la pantalla de inicio de Cloud Manager. Haga clic en **+Añadir** y seleccione **Agregar canalización que no sea de producción**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. **Agregar canalización que no sea de producción**  se abre. Seleccione el tipo de canalización que desea crear, ya sea **Canalización de calidad de código** o **Canalización de implementación**.

   Además, también puede configurar **Déclencheur de implementación** y **Comportamiento de errores de métricas importantes** from **Opciones de implementación**. Haga clic en **Continuar**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add2.png)


1. La canalización que no es de producción recién creada ahora se muestra en la **Canalizaciones** tarjeta.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add4.png)


   La canalización se muestra en la tarjeta de la pantalla principal con tres acciones, como se muestra a continuación:

   * **Agregar** : permite añadir una nueva canalización.
   * **Acceder a información de repositorios** : permite al usuario obtener la información necesaria para acceder al repositorio Git de Cloud Manager.
   * **Más información** : navega para comprender el recurso de documentación de canalización CI/CD.

### Edición de una canalización que no es de producción {#editing-nonprod-pipeline}

Puede editar las configuraciones de canalización desde el **Tarjeta de canalización** from **Información general del programa** página.

Siga los pasos a continuación para editar la canalización configurada que no sea de producción:

1. Vaya a **Canalizaciones** de la **Información general del programa** página.

1. Seleccione la canalización que no es de producción y haga clic en **...**. Haga clic en **Editar**, como se muestra en la figura siguiente.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit1.png)

1. La variable **Editar canalización de producción** que le permite actualizar el **Nombre de canalización**, **Repositorio**, **Rama de Git**, **Déclencheur de implementación** y **Comportamiento de error de métricas importantes**.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit2.png)

   >[!NOTE]
   >Consulte [Adición y administración de repositorios](/help/using/cloud-manager-repositories.md) para aprender a añadir y administrar repositorios en Cloud Manager.

   Puede asignar las siguientes déclencheur de implementación para iniciar la canalización:

   * **Manual** : al usar la interfaz de usuario, se inicia manualmente la canalización.
   * **Cambios en Git** - inicia la canalización CI/CD cada vez que se añaden confirmaciones a la rama git configurada. Incluso si selecciona esta opción, siempre puede iniciar la canalización manualmente.

   Durante la configuración o edición de la canalización, el administrador de implementación tiene la opción de definir el comportamiento de la canalización cuando se encuentra un error importante en cualquiera de las puertas de calidad. Esto resulta útil para los clientes que desean procesos más automatizados. Las opciones disponibles son:

   * **Pregunte cada vez** - Esta es la configuración predeterminada y requiere una intervención manual en cualquier error importante.
   * **Fallo Inmediatamente** - Si se selecciona, la canalización se cancelará siempre que se produzca un error importante. Básicamente, esto emula a un usuario rechazando manualmente cada error.
   * **Continuar inmediatamente** - Si está seleccionada, la canalización se realizará automáticamente cada vez que se produzca un error importante. Básicamente, esto está emulando a un usuario que aprueba manualmente cada error.


1. Haga clic en **Actualizar** una vez que haya terminado de editar la canalización que no es de producción.

### Acciones adicionales de canalización que no son de producción {#additional-nonprod-actions}

#### Ejecución de una canalización que no sea de producción {#run-nonprod}

Puede ejecutar la canalización de producción desde la tarjeta Canalizaciones:

1. Vaya a **Canalizaciones** de la **Información general del programa** página.

1. Haga clic en **...** de la variable **Canalizaciones** y haga clic en **Ejecutar**, como se muestra en la figura siguiente.

   ![](/help/using/assets/configure-pipelines/nonprod-run1.png)

#### Eliminación de una canalización que no es de producción {#delete-nonprod}

Puede eliminar la canalización de producción de la tarjeta Canalizaciones:

1. Vaya a **Canalizaciones** de la **Información general del programa** página.

1. Haga clic en **...** de la variable **Canalizaciones** y haga clic en **Eliminar**, como se muestra en la figura siguiente.

   ![](/help/using/assets/configure-pipelines/nonprod-delete.png)


## Pasos siguientes {#the-next-steps}

Una vez configurada la canalización, debe implementar el código.

Consulte [Implementar el código](deploying-code.md) para obtener más información.
