---
title: Administración de canalizaciones
description: Obtenga información sobre cómo administrar las canalizaciones existentes, incluido editarlas, ejecutarlas y eliminarlas.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 99325c28c379103db2ba4c19bb6d206849c6e126
workflow-type: ht
source-wordcount: '517'
ht-degree: 100%

---


# Administración de canalizaciones {#managing-pipelines}

Obtenga información sobre cómo administrar las canalizaciones existentes, incluido editarlas, ejecutarlas y eliminarlas.

## Tarjeta de canalización {#pipeline-card}

La tarjeta **Canalizaciones** en la página **Resumen del programa** en Cloud Manager le ofrece una descripción general de todas sus canalizaciones y de su estado actual.

![Tarjeta de canalizaciones en Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

Al hacer clic en el botón de puntos suspensivos situado junto a cada canalización, puede llevar a cabo las siguientes acciones.

* [Ejecutar la canalización](#running-pipelines)
* [Editar la canalización](#editing-pipelines)
* [Eliminar la canalización](#deleting-pipelines)
* [Ver detalles](#view-details)

En la parte inferior de la lista de canalizaciones, tiene opciones generales.

* **Agregar**: para [añadir una nueva canalización de producción](/help/using/production-pipelines.md) o [añadir una nueva canalización que no sea de producción](/help/using/non-production-pipelines.md)
* **Mostrar todos**: lleva al usuario a la pantalla **Canalizaciones** para ver todas las canalizaciones en una tabla más detallada
* **Acceder a la info del repositorio**: muestra la información necesaria para acceder al repositorio de Git de Cloud Manager
* **Más información**: navega a los recursos de documentación de canalización de CI/CD.

## Ejecución de canalizaciones {#running-pipelines}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y el programa adecuados.

1. Vaya a la tarjeta **Canalizaciones** de la página **Resumen del programa** y haga clic en el botón de puntos suspensivos situado junto a la canalización que ejecuta. Seleccione **Ejecutar** en el menú.

1. La ejecución de la canalización comienza y se indica con la columna **Estado**.

Para ver los detalles de la ejecución, vuelva a hacer clic en el botón de puntos suspensivos y seleccione **[Ver detalles.](#view-details)**

Según el tipo de canalización, puede cancelar la ejecución haciendo clic de nuevo en el botón de puntos suspensivos y seleccionando **Cancelar**.

## Edición de canalizaciones {#editing-pipelines}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y el programa adecuados.

1. Vaya a la tarjeta **Canalizaciones** de la página **Resumen del programa** y haga clic en el botón de puntos suspensivos situado junto a la canalización que quiere editar. Seleccione **Editar** en el menú.

1. Se muestra el cuadro de diálogo **Editar canalización de producción** o **Editar canalización que no es de producción**, que le permite editar los mismos detalles introducidos al crear la canalización.

   * Consulte las siguientes páginas para obtener más información sobre todos los campos y las opciones de configuración disponibles para las canalizaciones.
      * [Configuración de canalizaciones de producción](/help/using/production-pipelines.md)
      * [Configuración de canalizaciones que no son de producción](/help/using/non-production-pipelines.md)

1. Haga clic en **Actualización del estado** una vez que haya terminado de editar la canalización.

>[!NOTE]
>
>No se puede editar una canalización en ejecución.

## Eliminación de canalizaciones {#deleting-pipelines}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y el programa adecuados.

1. Vaya a la tarjeta **Canalizaciones** de la página **Resumen del programa** y haga clic en el botón de puntos suspensivos situado junto a la canalización que ejecuta. Seleccione **Eliminar** en el menú.

>[!NOTE]
>
>No se puede eliminar una canalización en ejecución.

## Ver detalles {#view-details}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y el programa adecuados.

1. Vaya a la tarjeta **Canalizaciones** de la página **Resumen del programa** y haga clic en el botón de puntos suspensivos situado junto a la canalización que ejecuta. Seleccione **Ver detalles** en el menú.

1. Se le redirige a la página de detalles de la canalización en ejecución.

![Detalles de canalización](/help/assets/configure-pipelines/pipeline-running-details.png)

Desde esta, puede ver el estado de los distintos pasos de la canalización y recuperar los registros de compilación para fines diagnósticos. Consulte el documento [Implementación de código](/help/using/code-deployment.md) para obtener más información.

>[!NOTE]
>
>Solo puede ver los detalles de una canalización que se está ejecutando o que se ha ejecutado al menos una vez.
