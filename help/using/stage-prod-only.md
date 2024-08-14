---
title: Canalizaciones de solo fase y de producción
description: Descubra cómo puede dividir las implementaciones de fase y producción mediante canalizaciones dedicadas.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 72%

---

# Canalizaciones solo de fase y de producción {#stage-prod-only}

Descubra cómo puede dividir las implementaciones de fase y producción mediante canalizaciones dedicadas.

>[!NOTE]
>
>Esta característica solo está disponible para [el programa que la adoptó por primera vez](/help/release-notes/current.md#early-adoption).

## Información general {#overview}

Los entornos de ensayo y producción están perfectamente asociados. De forma predeterminada, estas implementaciones están vinculadas a una sola canalización. Es una canalización de implementación que se implementa en los entornos de ensayo y producción de ese programa. Aunque este acoplamiento suele ser adecuado, hay ciertos casos de uso en los que existen desventajas:

* Si desea implementar solo en fase, solo puede hacerlo rechazando el paso **Promocionar a producción** de la canalización. Sin embargo, la ejecución se marcará como cancelada.
* Si desea implementar el código más reciente en un entorno de ensayo en producción, debe volver a implementar toda la canalización, incluida la implementación de ensayo, aunque no se haya cambiado ningún código allí.
* Dado que los entornos no se pueden actualizar durante las implementaciones, si desea pausar y realizar pruebas en el entorno de fase durante varios días antes de la promoción a producción, el entorno de producción no se puede actualizar. Esto hace que las tareas no dependientes, como la actualización de las [variables de entorno](/help/getting-started/build-environment.md#environment-variables), sean imposibles.

Las canalizaciones de solo fase y producción ofrecen soluciones para estos casos de uso al proporcionar opciones de implementación dedicadas.

* Las **canalizaciones de implementación de solo fase** se implementan solo en un entorno de fase, quedando la ejecución finalizada una vez realizadas la implementación y las pruebas.
   * Una canalización de solo fase se comporta de forma idéntica a la canalización de producción de pila completa asociada estándar, pero sin los pasos de implementación de producción (aprobación, programación, implementación).
* Las **canalizaciones de implementación de solo producción** se implementan únicamente en un entorno de producción con la opción de seleccionar una ejecución finalizada y validada correctamente en el escenario e implementar sus artefactos en la producción.
   * Las canalizaciones de solo producción reutilizarán los artefactos de las implementaciones de fase, lo que omitirá la fase de generación.

Ni las canalizaciones de solo fase ni las de solo producción se ejecutarán mientras se esté ejecutando una canalización de producción de pila completa y viceversa. Si tanto la canalización de solo fase como la de producción de pila completa tienen configurado el activador **Cambios en Git** y apuntan a la misma rama y repositorio, solo se inicia automáticamente la canalización de solo fase. No se han iniciado las canalizaciones de solo producción **Cambios en Git**, ya que no están directamente vinculadas a un repositorio.

Estas canalizaciones dedicadas ofrecen más flexibilidad, pero debe tener en cuenta los siguientes detalles de funcionamiento y recomendaciones.

>[!NOTE]
>
>Las canalizaciones de solo producción siempre utilizarán los artefactos de la canalización de solo fase, independientemente de lo que se haya podido implementar en el escenario a través de la canalización de producción asociada estándar mientras tanto.
>
>* Esto podría provocar reversiones de código no deseadas.
>* Adobe recomienda dejar de usar la canalización de producción asociada estándar una vez que comience a utilizar las canalizaciones de solo producción y de solo fase.
>* Si todavía decide ejecutar tanto las canalizaciones asociadas estándar como las canalizaciones de solo fase/producción, tenga en cuenta la reutilización de artefactos para evitar reversiones del código.

## Creación de canalizaciones {#pipeline-creation}

Las canalizaciones solo de producción y solo de fase se crean de manera similar a las [canalizaciones de producción](/help/using/production-pipelines.md) y [canalizaciones que no son de producción](/help/using/non-production-pipelines.md) acopladas estándar. Consulte esos documentos para obtener más detalles.

1. En la ventana **Canalizaciones**, haga clic en **Agregar canalización**.

   * Seleccione **Agregar canalización que no sea de producción** para crear una canalización de solo fase.
   * Seleccione **Añadir una canalización de solo producción** para crear una canalización de solo producción.

   ![Creación de una canalización de solo producción/solo fase](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Algunas opciones pueden aparecer atenuadas si ya existen las canalizaciones correspondientes.
>
>* **Agregar canalización solo de producción** no está disponible si todavía no existe una canalización solo de fase.
>* **Agregar canalización de producción** no está disponible si ya existe una canalización acoplada estándar.
>* Solo se permite una canalización de solo producción y una de solo fase por programa.

### Canalizaciones solo de fase {#stage-only}

1. Una vez seleccionada la opción **Agregar canalización que no sea de producción**, se abrirá el cuadro de diálogo **Agregar canalización que no sea de producción**.
1. Para crear una canalización de solo fase, seleccione el entorno de fase en el campo **Entornos de implementación aptos** para la canalización. Complete los campos restantes y haga clic en **Continuar**.

   ![Creación de una canalización de solo fase](/help/assets/configure-pipelines/stage-only.png)

1. En la pestaña **Pruebas de ensayos**, puede definir luego las pruebas que deben realizarse en el entorno de ensayo. Haga clic en **Guardar** para guardar su nueva canalización.

   ![Parámetros de prueba para una canalización de solo fase](/help/assets/configure-pipelines/stage-only-test.png)

### Canalizaciones de solo producción {#prod-only}

1. Una vez seleccionada la opción **Añadir una canalización de solo producción**, se abre el cuadro de diálogo **Añadir una canalización de solo producción**.
1. Proporcione un **nombre para la canalización**. Las opciones y funcionalidades restantes del cuadro de diálogo funcionan igual que las del cuadro de diálogo de creación de canalización asociada estándar. Haga clic en **Guardar** para guardar la canalización.

   ![Creación de una canalización de solo producción](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Ejecutar canalizaciones solo de producción y solo de fase {#running}

Las canalizaciones solo de producción y solo de fase se ejecutan de la misma manera que [todas las demás canalizaciones se ejecutan](/help/using/managing-pipelines.md#running-pipelines). Consulte esa documentación para obtener más detalles.

Además, la ejecución de una canalización de solo producción se puede activar directamente desde los detalles de ejecución de una canalización de solo fase.

### Canalizaciones solo de fase {#stage-only-run}

Una canalización de solo fase se ejecuta casi del mismo modo que las canalizaciones asociadas estándar. Sin embargo, al final de la ejecución, después de los pasos de pruebas, el botón **Promocionar versión** permite iniciar una ejecución de canalización de solo producción que utilice los artefactos implementados en el escenario por esta ejecución y los implemente en la producción.

![Ejecución de canalización de solo fase](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

El botón **Promocionar versión** solo aparece si se encuentra en la última ejecución correcta de canalización de solo fase. Una vez que se ha hecho clic en, se le pide que confirme la ejecución de la canalización de solo producción o que cree una canalización de solo producción si aún no existe.

### Canalizaciones de solo producción {#prod-only-run}

Para las canalizaciones de solo producción es importante identificar los artefactos de origen que se van a implementar en la producción. Estos detalles se encuentran en el paso **Preparación de artefactos**. Puede navegar a esas ejecuciones para obtener más detalles y registros.

![Detalles del artefacto](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
