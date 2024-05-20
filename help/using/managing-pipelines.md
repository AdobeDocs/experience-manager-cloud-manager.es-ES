---
title: Administración de canalizaciones
description: Obtenga información sobre cómo administrar las canalizaciones existentes, como editarlas, ejecutarlas y eliminarlas.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: ab527beb706ab73a14cc933a3414873dee6b7a9e
workflow-type: ht
source-wordcount: '800'
ht-degree: 100%

---


# Administración de canalizaciones {#managing-pipelines}

Obtenga información sobre cómo administrar las canalizaciones existentes, como editarlas, ejecutarlas y eliminarlas.

## Tarjeta de canalización {#pipeline-card}

La tarjeta **Canalizaciones** de la página **Información general del programa** en Cloud Manager le ofrece una descripción general de todas sus canalizaciones y de su estado actual.

![Tarjeta de canalización en Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

Al hacer clic en el botón de los tres puntos situado junto a cada canalización, puede realizar las siguientes acciones.

* [Ejecutar la canalización](#running-pipelines)
* [Editar la canalización](#editing-pipelines)
* [Eliminar la canalización](#deleting-pipelines)
* [Ver detalles](#view-details)

En la parte inferior de la lista de canalizaciones, tiene opciones generales.

* **Agregar**: para [añadir una nueva canalización de producción](/help/using/production-pipelines.md) o [añadir una nueva canalización que no sea de producción](/help/using/non-production-pipelines.md)
* **Mostrar todos**: lleva al usuario a la pantalla **Canalizaciones** para ver todas las canalizaciones en una tabla más detallada
* **Acceder a la info del repositorio**: muestra la información necesaria para acceder al repositorio de Git de Cloud Manager
* **Más información**: Navega hasta los recursos de documentación de canalización de CI/CD.

## Ventana de canalizaciones {#pipelines}

La ventana **Canalizaciones** muestra una lista completa de todas las canalizaciones para el programa seleccionado. Esto resulta útil, ya que presenta información más completa que la disponible en la [Tarjeta de canalización.](#pipeline-card)

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. En la página **Resumen del programa**, pulse o haga clic en **Canalizaciones** para cambiar a la ventana **Canalizaciones**.

1. Aquí puede ver una lista de todas las canalizaciones para el programa, así como iniciar y detener la ejecución de la canalización como lo haría en la **Tarjeta de canalizaciones**.

Al pulsar o hacer clic en el icono `i` se muestran detalles sobre la última o la actual ejecución de la canalización.

![Detalles de ejecución de canalización](/help/assets/configure-pipelines/pipeline-status.png)

Pulsar o hacer clic en **Ver detalles** le llevará a los [detalles de la ejecución de la canalización.](#view-details)

## Ventana de actividad {#activity}

La ventana **Actividades** muestra una lista completa de todas las ejecuciones de canalizaciones para el programa seleccionado.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. En la página **Resumen del programa**, pulse o haga clic en **Actividad** para cambiar a la ventana **Actividad**.

1. Aquí puede ver una lista de todas las ejecuciones de canalización del programa, incluidas las ejecuciones actuales e históricas.

Al pulsar o hacer clic en el icono `i` se muestran los detalles sobre la última o la actual ejecución de la canalización seleccionada.

![Detalles de ejecución de canalización](/help/assets/configure-pipelines/pipeline-activity.png)

Pulsar o hacer clic en **Ver detalles** le llevará a los [detalles de la ejecución de la canalización.](#view-details)

## Ejecutar canalizaciones {#running-pipelines}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Navegue hasta la tarjeta **Canalizaciones** de la página **Información general del programa** y haga clic en el botón de los tres puntos situado junto a la canalización que ejecute, seleccione **Ejecutar** del menú.

1. La ejecución de la canalización comienza y se indica con la columna **Estado**.

Para ver los detalles de la ejecución, vuelva a hacer clic en el botón de los tres puntos y seleccione **[Ver detalles.](#view-details)**

Según el tipo de canalización, puede cancelar la ejecución si hace clic de nuevo en el botón de los tres puntos y selecciona **Cancelar**.

## Editar canalizaciones {#editing-pipelines}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Navegue hasta la tarjeta **Canalizaciones** de la página **Información general del programa**, haga clic en el botón de los tres puntos situado junto a la canalización que desee editar y, a continuación, seleccione **Editar** del menú.

1. El cuadro de diálogo **Editar canalización de producción** o **Editar canalización que no sea de producción** se mostrará y le permitirá editar los mismos detalles introducidos al crear la canalización.

   * Consulte las siguientes páginas para obtener más información sobre todos los campos y las opciones de configuración disponibles para las canalizaciones.
      * [Configurar canalizaciones de producción](/help/using/production-pipelines.md)
      * [Configurar canalizaciones que no sean de producción](/help/using/non-production-pipelines.md)

1. Haga clic en **Actualizar** cuando haya terminado de editar la canalización.

>[!NOTE]
>
>No se puede editar una canalización en ejecución.

## Eliminar canalizaciones {#deleting-pipelines}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Navegue hasta la tarjeta **Canalizaciones** de la página **Información general del programa** y haga clic en el botón de los tres puntos situado junto a la canalización que ejecute, seleccione **Eliminar** del menú.

>[!NOTE]
>
>No se puede eliminar una canalización en ejecución.

## Ver detalles {#view-details}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Navegue hasta la tarjeta **Canalizaciones** de la página **Información general del programa** y haga clic en el botón de los tres puntos situado junto a la canalización que ejecute, seleccione **Ver detalles** del menú.

1. Se le redirigirá a la página de detalles de la canalización en ejecución.

![Detalles de canalización](/help/assets/configure-pipelines/pipeline-running-details.png)

Desde esta, puede ver el estado de los distintos pasos de la canalización y recuperar los registros de compilación para fines diagnósticos. Consulte el documento [Implementación de código](/help/using/code-deployment.md) para obtener más información.

Todos los pasos de la ejecución de una canalización se muestran con los que aún no se han iniciado en gris. Los pasos finalizados muestran su duración.

Una vez completado el paso de una canalización, se presenta un resumen.

![Resumen del paso](/help/assets/configure-pipelines/pipeline-step.png)

Haga clic o pulse en el vínculo **Ver detalles** para mostrar la sección **Duración**. Esto incluye la duración promedio de la canalización en función de la tendencia histórica para ese programa.

![Duración](/help/assets/configure-pipelines/duration.png)

>[!NOTE]
>
>Solo puede ver los detalles de una canalización que se esté ejecutando o que se haya ejecutado al menos una vez.
