---
title: Añadir una canalización de producción
description: Aprenda a utilizar Cloud Manager para crear y configurar canalizaciones de producción para implementar su código.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
TQID: https://experienceleague.adobe.com/WH6W8bZNCWo0BAGLwnMOPpB3bk5P6Fd7c5b-dRT5Vc0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: badb64b816e83ca08a39b2b39eda13335f6a3c1d
workflow-type: tm+mt
source-wordcount: 1665
ht-degree: 73%

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

   ![Agregar una canalización de producción](/help/assets/configure-pipelines/add-prod7.png)

1. El cuadro de diálogo **Agregar canalización de producción** se abre a la pestaña **Configuración**, en la que se deben definir varias opciones para la canalización. Estas opciones se agrupan en secciones contraíbles y se describen en los pasos siguientes.

   1. Proporcione un nombre descriptivo para la canalización en el campo **Nombre de la canalización**.

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

1. Haga clic en **Continuar** para avanzar a la pestaña **Código Source**, donde seleccionará el tipo de código que se va a implementar y configurará el repositorio de origen.

   1. En **Seleccionar código para implementar**, elija el tipo de implementación:

      * **[Código de pila completa](#full-stack-code)**: código para la aplicación AEM completa.
      * **[Configuración de nivel web](#web-tier-config)**: propiedades de Dispatcher para almacenar, procesar y entregar páginas web al cliente.

      Consulte [Canalizaciones de CI/CD](/help/overview/ci-cd-pipelines.md#code-sources) para obtener más información sobre estos tipos de implementación. Los pasos restantes para completar la configuración de la canalización dependen del tipo seleccionado. Siga los vínculos anteriores para ir a la sección correspondiente de este documento.

1. Haga clic en **Continuar** para avanzar a la pestaña **Prueba de ensayo**, donde puede configurar las pruebas de rendimiento de AEM Sites y AEM Assets, en función de los productos para los que disponga de licencia. {#stage-testing}

   >[!TIP]
   >
   >Consulte el documento [Prueba de calidad del código](/help/using/code-quality-testing.md#performance-testing) para obtener más información sobre las opciones disponibles en la pestaña **Prueba de ensayo**.

   1. En la sección **Entrega de contenido de sitios/Peso de carga distribuido**, configure las pruebas de rendimiento del sitio en función de la ponderación de las solicitudes de página entre tres conjuntos de páginas. Puede habilitar o deshabilitar los conjuntos de páginas según sea necesario.

      * **Páginas en directo populares**
      * **Otras páginas en directo**
      * **Nuevas páginas**

      ![Peso de carga de los sitios](/help/assets/configure-pipelines/add-prod8.png)

   1. En la sección **Distribución de pruebas de rendimiento de activos**, puede definir la distribución de prueba de imágenes y PDF, así como sus propios activos de prueba.

      * **Imágenes**: ajuste el regulador para ajustar la división de prueba entre imágenes y PDF.
      * **PDF**: ajuste el regulador para ajustar la división de prueba entre imágenes y PDF.

      * Defina sus propios activos personalizados cargándolos.

         1. **FORMATO**: elija si el activo personalizado es un PDF de una imagen.
         1. **NOMBRE DEL ARCHIVO**: utilice el botón del explorador de archivos para seleccionar una imagen del equipo local.
         1. **Agregar archivo de prueba**: haga clic en para cargar el activo seleccionado.

      ![Distribución de pruebas de activos](/help/assets/configure-pipelines/add-prod6.png)

1. Haga clic en **Guardar** para completar la adición de la canalización de producción.

### Código de pila completa {#full-stack-code}

Una canalización de código de pila completa implementa compilaciones de código de back-end y front-end junto con la configuración HTTPD/Dispatcher.

>[!NOTE]
>
>Si ya existe una canalización de producción de pila completa, esta selección está deshabilitada.

**Para configurar una canalización de producción de código de pila completa:**

1. En la ficha **Código Source**, defina las siguientes opciones.

   * **Repositorio**: Define desde qué repositorio de Git la canalización debe recuperar el código.

   >[!TIP]
   >
   >Consulte el documento [Configuración del programa](/help/getting-started/program-setup.md) para aprender a añadir y administrar repositorios en Cloud Manager.

   * **Rama de Git**: define desde qué rama la canalización debe recuperar el código.
   * **Ignorar configuración de nivel web**: cuando se selecciona, la canalización no implementa la configuración del nivel web. Si ya existe una canalización de configuración de nivel web para el mismo entorno, esta casilla de verificación se selecciona automáticamente y se desactiva porque esa canalización administra la configuración de nivel web en su lugar. Cuando no existe ninguna canalización de configuración de nivel web, puede seleccionar o desactivar esta opción para controlar si la canalización de pila completa implementa la configuración de Dispatcher.

   ![Origen del código de pila completa](/help/assets/configure-pipelines/add-prod-fullstack-source.png)

1. Haga clic en **Continuar** para avanzar a la pestaña **Prueba de ensayo**. Consulte [Prueba de ensayo](#stage-testing) para obtener más información.

### Configuración de nivel web {#web-tier-config}

Una canalización de configuración de nivel web solo implementa la configuración de HTTPD/Dispatcher. Consulte [Canalizaciones de CI/CD](/help/overview/ci-cd-pipelines.md#deployment-types) para obtener más información sobre este tipo de canalización.

>[!NOTE]
>
>Si ya existe una canalización de producción de configuración de nivel web, esta selección está deshabilitada.

Si crea una canalización de configuración de nivel web para un entorno con una canalización de pila completa existente, se ignorará la configuración de nivel web en la canalización de pila completa. Este cambio solo afecta a la configuración del nivel web en ese entorno.

**Para configurar una canalización de producción de configuración de nivel web:**

1. En la ficha **Código Source**, defina las siguientes opciones.

   * **Repositorio**: en la lista desplegable, seleccione el repositorio Git que contiene la configuración del nivel web.
   * **Rama de Git**: seleccione la rama en el repositorio elegido que Cloud Manager usa para la implementación.
   * **Ubicación del código**: escriba la ruta de acceso en el repositorio seleccionado que contiene la configuración del nivel web que se va a implementar. La ubicación predeterminada es la raíz del repositorio (`/`).

   >[!NOTE]
   >
   >Si Ubicación del código no señala a la ubicación del código de Dispatcher, se podría extraer el código de aplicación adicional en el paquete del artefacto e implementarlo en Dispatcher, lo que ocasionaría que Apache falle al reiniciar y que la canalización falle. Asegúrese de establecer la ruta correcta a los archivos de Dispatcher en el repositorio.

   ![Origen de configuración de nivel web](/help/assets/configure-pipelines/add-prod-webtier-source.png)

1. Haga clic en **Continuar** para avanzar a la pestaña **Prueba de ensayo**. Consulte [Prueba de ensayo](#stage-testing) para obtener más información.

## Pasos siguientes {#the-next-steps}

Después de configurar la canalización, puede implementar el código. Consulte la [Implementación de código](/help/using/code-deployment.md) para obtener más información.

## Tutorial de vídeo {#video-tutorial-one}

Este vídeo ofrece información general sobre el proceso de creación de canalizaciones, que se detalla en este documento.

>[!VIDEO](https://video.tv.adobe.com/v/327603?captions=spa)
