---
title: Configuración de canalizaciones de producción
description: Aprenda a utilizar Cloud Manager para crear y configurar canalizaciones de producción para implementar su código.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 99325c28c379103db2ba4c19bb6d206849c6e126
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 0%

---


# Configuración de canalizaciones de producción {#configuring-production-pipelines}

Aprenda a utilizar Cloud Manager para crear y configurar canalizaciones de producción para implementar su código. si desea primero una descripción general más conceptual del funcionamiento de las canalizaciones en Cloud Manager, consulte el documento [Canalizaciones CI/CD.](/help/overview/ci-cd-pipelines.md)

## Información general {#overview}

Al usar la variable **Configuración de canalización** mosaico en [!UICONTROL Cloud Manager] puede crear dos tipos diferentes de canalizaciones.

* **Canalizaciones de producción** - Una canalización de producción es una canalización diseñada específicamente y formada por una serie de pasos organizados para tomar el código fuente de su repositorio de Git hasta la producción.
* **Canalizaciones que no son de producción** : una canalización que no es de producción sirve principalmente para ejecutar análisis de calidad del código o para implementar código fuente en un entorno de desarrollo.

Este documento se centra en las canalizaciones de producción. Para obtener más información sobre cómo configurar canalizaciones que no sean de producción, consulte el documento [Configuración de canalizaciones que no sean de producción.](/help/using/non-production-pipelines.md)

La variable **Administrador de implementación** es responsable de configurar la canalización. La configuración de canalización consta de:

1. Definición del déclencheur que iniciará la canalización.
1. Definición de los parámetros que controlan la implementación de producción.
1. Configuración de los parámetros de prueba de rendimiento.

>[!NOTE]
>
>No se puede configurar una canalización hasta que su repositorio de Git asociado tenga al menos una rama y [configuración del programa](/help/getting-started/program-setup.md) ha finalizado.

## Tutorial de vídeo {#video-tutorial-one}

Este vídeo ofrece información general sobre el proceso de creación de canalizaciones, que se detalla en este documento.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## Adición de una nueva canalización de producción {#adding-production-pipeline}

Una vez que haya utilizado la variable [!UICONTROL Cloud Manager] Para configurar el programa y tener al menos un entorno, está listo para agregar una canalización de producción.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y el programa adecuados.

1. Vaya a la **Canalizaciones** de la **Información general del programa** página y haga clic en **+Añadir** y seleccione **Agregar canalización de producción**.

   ![Añadir una canalización de producción](/help/assets/configure-pipelines/add-prod1.png)

1. La variable **Agregar canalización de producción** se abre **Configuración** en la que se deben definir varias opciones para la canalización. Estas opciones se agrupan en secciones contraíbles y se describen en los pasos siguientes.

   1. Proporcione un nombre descriptivo para la canalización en la **Nombre de canalización** campo .

   1. En el **Código fuente** , define dónde recupera la canalización el código que procesará.

      * **Repositorio** - Esta opción define desde qué repositorio de Git la canalización debe recuperar el código.
      >[!TIP]
      >
      >Consulte el documento [Configuración del programa](/help/getting-started/program-setup.md) para aprender a añadir y administrar repositorios en Cloud Manager.

      * **Rama de Git** - Esta opción define desde qué rama de la canalización seleccionada debe recuperar el código.
      * **Ubicación del código** - Esta opción define la ruta en la rama de la repo seleccionada desde la que la canalización debe recuperar el código.

      ![Definir repositorios para la canalización](/help/assets/configure-pipelines/add-prod2.png)

   1. En el **Entornos** , define los déclencheur de una implementación y cómo debe implementarse por entorno.

      1. En el **STAGE** , puede definir cómo se despliega la canalización en el entorno de ensayo.

         * **Déclencheur de implementación** : Tiene las siguientes opciones para definir los déclencheur de implementación para iniciar la canalización.

            * **Manual** - Utilice esta opción para iniciar manualmente la canalización mediante la interfaz de usuario de Cloud Manager.
            * **Cambios en Git** - Esta opción inicia la canalización CI/CD cada vez que se añaden confirmaciones a la rama git configurada. Con esta opción, aún puede iniciar la canalización manualmente según sea necesario.
         * **Comportamiento de errores de métricas importantes** - Durante la configuración o edición de la canalización, el administrador de implementación tiene la opción de definir el comportamiento de la canalización cuando se encuentra un error importante en cualquiera de las puertas de calidad. Las opciones disponibles son:

            * **Pregunte cada vez** - Esta es la configuración predeterminada y requiere intervención manual en caso de que se produzca algún error importante.
            * **Fallo Inmediatamente** - Si se selecciona, la canalización se cancelará siempre que se produzca un fallo importante. Básicamente, esto emula a un usuario rechazando manualmente cada error.
            * **Continuar inmediatamente** - Si se selecciona, la canalización se realizará automáticamente cada vez que se produzca un error importante. Básicamente, esto está emulando a un usuario que aprueba manualmente cada error.

         ![Déclencheur de implementación](/help/assets/configure-pipelines/add-prod3.png)

         * **Opciones de implementación** : puede acelerar ciertas tareas de implementación.

            * **Aprobar después de la implementación de la fase** : Esta aprobación se produce después de la implementación en el entorno de ensayo antes de realizar ninguna prueba. De lo contrario, la aprobación se produce antes de la implementación de producción, que se realiza después de completar todas las pruebas.

            * **Omitir cambios del equilibrador de carga** - No se realizan cambios en el equilibrador de carga.

         ![Opciones de implementación de ensayo](/help/assets/configure-pipelines/add-prod4.png)

         * **Configuración de Dispatcher** - El **Administrador de implementación** puede configurar un conjunto de rutas de contenido que se invalidarán o vaciarán de la caché de Dispatcher AEM cuando se ejecute una canalización. Estas acciones de caché se realizarán como parte del paso de canalización de implementación, justo después de implementar cualquier paquete de contenido. Estos ajustes utilizan el comportamiento estándar AEM Dispatcher. Para configurar:

            1. En **RUTA** proporcione una ruta de contenido.
            1. En **TYPE**, seleccione la acción que se realizará en esa ruta.
            * **Vaciado** : realice una invalidación de caché, similar a cuando el contenido se activa desde una instancia de creación a una instancia de publicación.
            * **Invalidar** : realiza una eliminación de caché.
            1. Haga clic en **Agregar ruta** para agregar la ruta especificada. Puede agregar hasta 100 rutas por entorno.

         ![Configuración de Dispatcher](/help/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >En general, es preferible el uso de la acción de invalidación, pero puede haber casos en los que sea necesario vaciar, especialmente cuando se utilizan AEM bibliotecas de cliente de HTML.

      1. En el **PRODUCCIÓN** , puede definir cómo se despliega la canalización en el entorno de producción.

         * **Opciones de implementación** : Puede definir los parámetros que controlan la implementación de producción.

            * **Usar la aprobación de lanzamiento** : un usuario debe aprobar manualmente una implementación con la variable **Propietario empresarial**, **Administrador de proyectos** o **Administrador de implementación** a través de la función [!UICONTROL Cloud Manager] IU.
            * **Programado** : Esta opción detiene la canalización antes de la implementación de producción para permitir que se programe. Si se selecciona esta opción, la canalización se detendrá después de la implementación en el entorno de ensayo y se pedirá al usuario que realice la acción.
               * **Ahora** : esta opción se implementa en producción inmediatamente, completando efectivamente la canalización.
               * **Fecha** : Esta opción permite al usuario programar un momento en el que se debe completar la implementación.
               * **Detener ejecución** : Esta opción anula la implementación en producción.

            >[!TIP]
            >
            >Consulte el documento [Implementación de código,](/help/using/code-deployment.md) para obtener información sobre cómo configurar la programación de implementación o ejecutar la canalización inmediatamente.

            * **Usar la supervisión de CSE** : Si se selecciona esta opción, se contrata a un CSE para que inicie realmente la implementación. Al crear o editar una canalización cuando esta opción está habilitada, la variable **Administrador de implementación** tiene las siguientes opciones.

               * **Cualquier CSE** : Esta opción permite que cualquier CSE disponible inicie la implementación.
               * **Mi CSE** : Esta opción solo permite que el CSE específico asignado al cliente inicie la implementación. Esto también se aplica a la copia de seguridad designada del CSE si el CSE asignado no está disponible.

            ![Opciones de implementación de producción](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Configuración de Dispatcher** : Defina la configuración de Dispatcher para su entorno de producción. Las opciones son las mismas que para el entorno de ensayo.











1. Haga clic en **Continuar** para avanzar al **Prueba de prueba** , donde puede configurar las pruebas de rendimiento de AEM Sites y AEM Assets, en función de los productos con licencia.

   >[!TIP]
   >
   >Consulte el documento [Prueba de calidad de código](/help/using/code-quality-testing.md#performance-testing) para obtener más información sobre las opciones disponibles en la **Prueba de prueba** pestaña .

   1. En el **Entrega de contenido de sitios/Peso de carga distribuido** , define cómo se configuran las pruebas de rendimiento de los sitios en función de la ponderación de las solicitudes de página entre los tres conjuntos de páginas, que se pueden habilitar o deshabilitar.

      * **Páginas Live populares**
      * **Otras páginas Live**
      * **Nuevas páginas**

      ![Peso de carga de los sitios](/help/assets/configure-pipelines/add-prod5.png)

   1. En el **Distribución de pruebas de rendimiento de recursos** , puede definir la distribución de prueba de imágenes y PDF, así como sus propios recursos de prueba.

      * **Imágenes** - Ajuste el control deslizante para ajustar la división de prueba entre imágenes y PDF.
      * **PDF** - Ajuste el control deslizante para ajustar la división de prueba entre imágenes y PDF.

      * Cargue sus propios recursos personalizados.

         1. **FORMATO** : elija si el recurso personalizado es un PDF de una imagen.
         1. **NOMBRE DE ARCHIVO** - Utilice el botón del navegador de archivos para seleccionar una imagen del equipo local.
         1. **Agregar archivo de prueba** - Haga clic en para cargar el recurso seleccionado.

      ![Distribución de pruebas de activos](/help/assets/configure-pipelines/add-prod6.png)



1. Haga clic en **Guardar** para completar la adición de la canalización de producción.

## Pasos siguientes {#the-next-steps}

Una vez configurada la canalización, debe implementar el código. Consulte el documento [Implementación de código](/help/using/code-deployment.md) para obtener más información.
