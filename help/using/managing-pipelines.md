---
title: Administrar canalizaciones
description: Obtenga información sobre cómo administrar las canalizaciones existentes, como editarlas, ejecutarlas y eliminarlas.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 8e2c57d2594691e7fb18d8a538caa9b54a26b6bb
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 41%

---


# Administrar canalizaciones {#managing-pipelines}

Obtenga información sobre cómo administrar las canalizaciones existentes, como editarlas, ejecutarlas y eliminarlas.

## Tarjeta de canalización {#pipeline-card}

La tarjeta **Canalizaciones** de la página **Información general del programa** en Cloud Manager le ofrece una descripción general de todas sus canalizaciones y de su estado actual.

![Tarjeta de canalización en Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

Al hacer clic en el botón de los tres puntos situado junto a cada canalización, puede realizar las siguientes acciones:

* [Ejecute la canalización](#running-pipelines).
* [Editar la canalización](#editing-pipelines).
* [Eliminar la canalización](#deleting-pipelines).
* [Ver detalles](#view-details).

En la parte inferior de la lista de canalizaciones, tiene las siguientes opciones generales.

* **Agregar** - Para [agregar una nueva canalización de producción](/help/using/production-pipelines.md) o [agregar una nueva canalización que no sea de producción](/help/using/non-production-pipelines.md).
* **Mostrar todo**: lleva al usuario a la pantalla **Canalizaciones** para ver todas las canalizaciones en una tabla más detallada.
* **Acceder a la info del repositorio**: muestra la información necesaria para acceder al repositorio Git de Cloud Manager.
* **Más información**: Navega hasta los recursos de documentación de canalización de CI/CD.

## Ventana Canalizaciones {#pipelines}

La ventana **Canalizaciones** muestra una lista completa de todas las canalizaciones para el programa seleccionado. Esta lista es útil porque presenta información más completa que la disponible en la [tarjeta de canalizaciones](#pipeline-card).

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. En la página **Resumen del programa**, haga clic en la ficha **Canalizaciones** para cambiar a la ventana **Canalizaciones**.

1. Aquí puede ver una lista de todas las canalizaciones para el programa y comenzar y detener la ejecución de la canalización como lo haría en la **Tarjeta de canalizaciones**.

Al hacer clic en el icono `i`, se muestran detalles sobre la última o la ejecución actual de la canalización.

![Detalles de ejecución de canalización](/help/assets/configure-pipelines/pipeline-status.png)

Al hacer clic en **Ver detalles**, accederá a [los detalles de la ejecución de la canalización](#view-details).

## Ventana de actividad {#activity}

La ventana **Actividades** muestra una lista completa de todas las ejecuciones de canalizaciones para el programa seleccionado.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. En la página **Información general del programa**, haga clic en la ficha **Actividad** para cambiar a la ventana **Actividad**.

1. Aquí puede ver una lista de todas las ejecuciones de canalización del programa, incluidas las ejecuciones actuales e históricas.

Al hacer clic en el icono `i`, se muestran detalles sobre la ejecución de la canalización seleccionada.

![Detalles de ejecución de canalización](/help/assets/configure-pipelines/pipeline-activity.png)

Haga clic en **Ver detalles** para revisar [los detalles de la ejecución de la canalización](#view-details).

## Ejecutar canalizaciones {#running-pipelines}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.
1. Vaya a la tarjeta **Canalizaciones** de la página **Información general del programa**.
1. Haga clic en el botón de los tres puntos situado junto a la canalización que ejecuta y, a continuación, en el menú, seleccione **Ejecutar**.

   La columna Estado indica cuándo comienza la ejecución de la canalización.

   Para ver los detalles de la ejecución, vuelva a hacer clic en el botón de los tres puntos y seleccione **[Ver detalles](#view-details)**.

   Según el tipo de canalización, puede cancelar la ejecución si hace clic de nuevo en el botón de los tres puntos y selecciona **Cancelar**.

## Editar canalizaciones {#editing-pipelines}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Vaya a la tarjeta **Canalizaciones** de la página **Resumen del programa** y haga clic en el botón de puntos suspensivos situado junto a la canalización que desee editar. A continuación, en el menú, seleccione **Editar**.

1. Aparecerá el cuadro de diálogo **Editar canalización de producción** o **Editar canalización que no sea de producción**. Puede editar los mismos detalles introducidos durante la creación de la canalización.

   Consulte [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) y [Configuración de canalizaciones que no son de producción](/help/using/non-production-pipelines.md) para obtener detalles sobre los campos y las opciones de configuración disponibles para las canalizaciones.

1. Haga clic en **Actualizar** cuando haya terminado.

>[!NOTE]
>
>No se puede editar una canalización en ejecución.

## Eliminar canalizaciones {#deleting-pipelines}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Vaya a la tarjeta **Canalizaciones** de la página **Resumen del programa** y haga clic en el botón de puntos suspensivos situado junto a la canalización que ejecuta. A continuación, en el menú, seleccione **Eliminar**.

>[!NOTE]
>
>No se puede eliminar una canalización en ejecución.

## Ver detalles {#view-details}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Vaya a la tarjeta **Canalizaciones** de la página **Resumen del programa** y haga clic en el botón de puntos suspensivos situado junto a la canalización que ejecuta. A continuación, en el menú, seleccione **Ver detalles**.

1. Se le redirigirá a la página de detalles de la canalización en ejecución.

![Detalles de canalización](/help/assets/configure-pipelines/pipeline-running-details.png)

Desde aquí puede ver el estado de los distintos pasos de la canalización y recuperar los registros de generación con fines diagnósticos. Consulte el documento [Implementación de código](/help/using/code-deployment.md) para obtener más información.

Todos los pasos de la ejecución de una canalización se muestran con los que aún no se han iniciado en gris. Los pasos finalizados muestran su duración.

Cuando se completa un paso de una canalización, se presenta un resumen.

![Resumen del paso](/help/assets/configure-pipelines/pipeline-step.png)

Haga clic en el vínculo **Ver detalles** para mostrar la sección **Duración**. Esta sección incluye la duración promedio de la canalización en función de la tendencia histórica para ese programa.

![Duración](/help/assets/configure-pipelines/duration.png)

Si la canalización contenía un paso de **escaneo de código** que generó problemas, puede hacer clic en el botón **Descargar detalles** para ver una lista de [pruebas de calidad de código](/help/using/code-quality-testing.md) que no se superaron.

![Problemas de calidad del código](assets/managing-pipelines-code-quality-issues.png)

La columna de **Ubicación de archivos del proyecto** está disponible en el archivo CSV para indicar la ubicación del código infractor. Esta columna es la ruta relativa al proyecto, mientras que la columna **Ubicación del archivo** es generada por Maven.

![Detalles del problema de análisis de código del proyecto](assets/managing-pipelines-code-quality-details.png)


>[!NOTE]
>
>Solo puede ver los detalles de una canalización que se esté ejecutando o que se haya ejecutado al menos una vez.
