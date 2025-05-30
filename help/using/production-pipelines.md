---
title: Añadir una canalización de producción
description: Aprenda a utilizar Cloud Manager para crear y configurar canalizaciones de producción para implementar su código.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 1209faf71edbd74cd87acfe24ec438b98ddd4a3a
workflow-type: ht
source-wordcount: '1249'
ht-degree: 100%

---


# Añadir una canalización de producción {#configuring-production-pipelines}

Aprenda a utilizar Cloud Manager para crear y configurar canalizaciones de producción para implementar su código. Si desea conocer primero una descripción general más conceptual del funcionamiento de las canalizaciones en Cloud Manager, consulte el documento [Canalizaciones de CI/CD](/help/overview/ci-cd-pipelines.md).

## Información general {#overview}

Al usar el mosaico **Configuración de canalización** en [!UICONTROL Cloud Manager], puede crear dos tipos diferentes de canalizaciones.

* **Canalizaciones de producción**: Una canalización de producción está estructurada y formada específicamente por una serie de pasos organizados para tomar el código fuente de su repositorio de Git y llevarlo a la producción.
* **Canalizaciones que no son de producción**: una canalización que no es de producción sirve principalmente para ejecutar el análisis de calidad del código o para implementar el código fuente en un entorno de desarrollo.

Este documento se centra en las canalizaciones de producción. Para obtener más información sobre cómo configurar canalizaciones que no son de producción, consulte el documento [Configuración de canalizaciones que no son de producción](/help/using/non-production-pipelines.md).

La función **Administrador de implementación** es responsable de configurar la canalización. La configuración de canalización consta de lo siguiente:

1. Definición del activador que iniciará la canalización.
1. Definición de los parámetros que controlan la implementación de producción.
1. Configuración de los parámetros de prueba de rendimiento.

>[!NOTE]
>
>No se puede configurar una canalización hasta que su repositorio de Git asociado tenga al menos una rama y la [configuración del programa](/help/getting-started/program-setup.md) haya finalizado.

## Adición de una nueva canalización de producción {#adding-production-pipeline}

Una vez que haya utilizado la IU de [!UICONTROL Cloud Manager] para configurar el programa y tener al menos un entorno, ya puede añadir una canalización de producción.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Vaya a la tarjeta **Canalizaciones** de la página **Información general del programa**.

1. Haga clic en **+Agregar** y seleccione **Añadir canalización que no es de producción**.

   ![Agregar una canalización de producción](/help/assets/configure-pipelines/add-prod1.png)

1. El cuadro de diálogo **Agregar canalización de producción** se abre a la pestaña **Configuración**, en la que se deben definir varias opciones para la canalización. Estas opciones se agrupan en secciones contraíbles y se describen en los pasos siguientes.

   1. Proporcione un nombre descriptivo para la canalización en el campo **Nombre de la canalización**.

   1. En la sección **Código fuente** defina dónde la canalización recupera el código que procesará.

      * **Repositorio**: Define desde qué repositorio de Git la canalización debe recuperar el código.

      >[!TIP]
      >
      >Consulte el documento [Configuración del programa](/help/getting-started/program-setup.md) para aprender a añadir y administrar repositorios en Cloud Manager.

      * **Rama de Git**: Define desde qué rama de la canalización seleccionada debe recuperar el código.
      * **Ubicación del código**: Esta opción define la ruta en la rama del repositorio seleccionado desde la que la canalización debe recuperar el código.

      ![Definir repositorios para la canalización](/help/assets/configure-pipelines/add-prod2.png)

   1. En la sección **Entornos** puede definir qué activa una implementación y cómo debe desplegarse por entorno.

      1. En la sección **FASE** puede definir cómo se despliega la canalización en el entorno de ensayo.

         * **Activador de implementación**: tiene las siguientes opciones para definir los activadores de implementación para iniciar la canalización.

            * **Manual**: Inicie la canalización manualmente mediante la interfaz de usuario de Cloud Manager.
            * **Cambios en Git**: esta opción inicia la canalización CI/CD cada vez que se añaden confirmaciones a la rama de Git configurada. Con esta opción, sigue pudiendo iniciar la canalización de forma manual según sea necesario.

         * **Comportamiento de los errores de las métricas importantes**: durante la configuración o edición de la canalización, el administrador de implementación tiene la opción de definir el comportamiento de la canalización cuando se encuentra un error importante en cualquiera de las puertas de calidad. Las opciones disponibles son las siguientes:

            * **Preguntar cada vez**: La configuración predeterminada y requiere intervención manual en caso de que se produzca algún error importante.
            * **Fallo inmediatamente**: La canalización se cancela siempre que se produzca un fallo importante. Se trata de emular a un usuario que rechaza errores manualmente.
            * **Continuar inmediatamente**: La canalización se ejecuta automáticamente cada vez que se produzca un error importante. Se trata de emular a un usuario que aprueba manualmente cada fallo.

         ![Activador de implementación](/help/assets/configure-pipelines/add-prod3.png)

         * **Opciones de implementación**: puede acelerar ciertas tareas de implementación.

            * **Aprobar después de la implementación de la fase**: esta aprobación se produce después de la implementación en el entorno de ensayo antes de realizar cualquier prueba. De lo contrario, la aprobación se produce antes de la implementación de producción, que se realiza después de completar todas las pruebas.

            * **Omitir los cambios del equilibrador de carga**: no se realizan cambios en el equilibrador de carga.

         ![Opciones de implementación de ensayo](/help/assets/configure-pipelines/add-prod4.png)

         * **Configuración de Dispatcher**: La función **Administrador de implementación** puede configurar un conjunto de rutas de contenido que se invalidarán o vaciarán de la caché de AEM Dispatcher cuando se ejecute una canalización. Estas acciones de caché se ejecutan como parte del paso de canalización de implementación, justo después de implementar cualquier paquete de contenido. Esta configuración utiliza el comportamiento estándar de AEM Dispatcher. Para configurarlo, haga lo siguiente:

            1. En **RUTA**, proporcione una ruta de contenido.
            1. En **TIPO**, seleccione la acción que se realizará en esa ruta.

               * **Vaciado**: realice una eliminación de caché.
               * **Invalidar**: efectúe una invalidación de caché, similar a cuando el contenido se activa desde una instancia de creación a una instancia de publicación.

            1. Haga clic en **Agregar ruta** para añadir la ruta especificada. Puede agregar hasta 100 rutas por entorno.

         ![Configuración de Dispatcher](/help/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >En general, es preferible el uso de la acción de invalidación, pero puede haber casos en los que sea necesario vaciar, sobre todo cuando se usan bibliotecas de cliente HTML de AEM.

      1. En la sección **PRODUCCIÓN**, puede definir cómo se despliega la canalización en el entorno de producción.

         * **Opciones de implementación**: puede definir los parámetros que controlan la implementación de producción.

            * **Usar la aprobación de GoLive**: un usuario con la función de **Propietario del negocio**, **Administrador de proyectos** o **Administrador de implementación** a través de la interfaz de usuario de [!UICONTROL Cloud Manager] debe aprobar manualmente una implementación.
            * **Programado**: Detiene la canalización antes de la implementación de producción para permitir que se programe. Si se selecciona esta opción, la canalización se detendrá después de la implementación en el entorno de ensayo y se preguntará al usuario qué acción debe hacerse.
               * **`Now`**: Implementa en producción de inmediato y completa efectivamente la canalización.
               * **Fecha**: Permite al usuario programar en qué momento se debe completar la implementación.
               * **Detener ejecución**: Anula la implementación en producción.

           >[!TIP]
           >
           >Consulte el documento [Implementación de código](/help/using/code-deployment.md) para obtener información sobre cómo configurar la programación de implementación o ejecutar la canalización inmediatamente.

            * **Usar la supervisión de CSE**: si se selecciona esta opción, se involucra un ingeniero de éxito del cliente (CSE) para que inicie la propia implementación. Al crear o editar una canalización cuando esta opción está habilitada, la función **Administrador de implementación** tiene las siguientes opciones.

               * **Cualquier CSE**: Esta opción permite que cualquier CSE disponible inicie la implementación.
               * **Mi CSE**: Esta opción solo permite que el CSE específico asignado al cliente inicie la implementación. Esta opción también se aplica al CSE sustituto, si el asignado no está disponible.

           ![Opciones de implementación de producción](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Configuración de Dispatcher**: Defina la configuración de Dispatcher para su entorno de producción. Las opciones son las mismas que para el entorno de ensayo.

1. Haga clic en **Continuar** para avanzar a la pestaña **Prueba de ensayo**, donde puede configurar las pruebas de rendimiento de AEM Sites y AEM Assets, en función de los productos para los que disponga de licencia.

   >[!TIP]
   >
   >Consulte el documento [Prueba de calidad del código](/help/using/code-quality-testing.md#performance-testing) para obtener más información sobre las opciones disponibles en la pestaña **Prueba de ensayo**.

   1. En la sección **Entrega de contenido de sitios/Peso de carga distribuido**, configure las pruebas de rendimiento del sitio en función de la ponderación de las solicitudes de página entre tres conjuntos de páginas. Puede habilitar o deshabilitar los conjuntos de páginas según sea necesario.

      * **Páginas en directo populares**
      * **Otras páginas en directo**
      * **Nuevas páginas**

      ![Peso de carga de los sitios](/help/assets/configure-pipelines/add-prod5.png)

   1. En la sección **Distribución de pruebas de rendimiento de activos**, puede definir la distribución de prueba de imágenes y PDF, así como sus propios activos de prueba.

      * **Imágenes**: ajuste el regulador para ajustar la división de prueba entre imágenes y PDF.
      * **PDF**: ajuste el regulador para ajustar la división de prueba entre imágenes y PDF.

      * Defina sus propios activos personalizados cargándolos.

         1. **FORMATO**: elija si el activo personalizado es un PDF de una imagen.
         1. **NOMBRE DEL ARCHIVO**: utilice el botón del explorador de archivos para seleccionar una imagen del equipo local.
         1. **Agregar archivo de prueba**: haga clic en para cargar el activo seleccionado.

      ![Distribución de pruebas de activos](/help/assets/configure-pipelines/add-prod6.png)

1. Haga clic en **Guardar** para completar la adición de la canalización de producción.

## Pasos siguientes {#the-next-steps}

Después de configurar la canalización, puede implementar el código. Consulte la [Implementación de código](/help/using/code-deployment.md) para obtener más información.

## Tutorial de vídeo {#video-tutorial-one}

Este vídeo ofrece información general sobre el proceso de creación de canalizaciones, que se detalla en este documento.

>[!VIDEO](https://video.tv.adobe.com/v/327603?captions=spa)
