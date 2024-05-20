---
title: Canalizaciones de solo fase y de solo producción
description: Descubra cómo puede dividir las implementaciones de ensayo y producción mediante canalizaciones dedicadas.
source-git-commit: c09fbf30270523018a36b128d43cbf10e65daf54
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 1%

---


# Canalizaciones solo de fase y de producción {#stage-prod-only}

Descubra cómo puede dividir las implementaciones de ensayo y producción mediante canalizaciones dedicadas.

>[!NOTE]
>
>Esta funcionalidad solo está disponible para [el programa de clientes pioneros.](/help/release-notes/current.md#early-adoption)

## Información general {#overview}

Los entornos de ensayo y producción están perfectamente asociados. De forma predeterminada, las implementaciones a ellas están vinculadas a una sola canalización. Es una canalización de implementación que se implementa en los entornos de ensayo y producción de ese programa. Aunque este acoplamiento suele ser adecuado, hay ciertos casos de uso en los que existen desventajas:

* Si desea implementar en solo fase, solo puede hacerlo rechazando la variable **Promocionar para producción** paso en la canalización. Sin embargo, la ejecución se marcará como cancelada.
* Si desea implementar el código más reciente en un entorno de ensayo en producción, debe volver a implementar toda la canalización, incluida la implementación de ensayo, aunque no se haya cambiado ningún código allí.
* Dado que los entornos no se pueden actualizar durante las implementaciones, si desea pausar y probar en el entorno de ensayo durante varios días antes de la promoción a producción, el entorno de producción no se puede actualizar. Esto hace que las tareas no dependan, como la actualización [variables de entorno](/help/getting-started/build-environment.md#environment-variables) imposible.

Las canalizaciones solo de fase y de solo producción ofrecen soluciones para estos casos de uso al proporcionar opciones de implementación dedicadas.

* **Canalizaciones de implementación solo de fase** implementar solo en un entorno de ensayo con la ejecución finalizada una vez realizadas la implementación y las pruebas.
   * Una canalización solo de fase se comporta de forma idéntica a la canalización de producto de pila completa acoplada estándar, pero sin los pasos de implementación de producción (aprobación, programación, implementación).
* **Canalizaciones de implementación solo de producción** implementar solo en un entorno de producción con la opción de seleccionar una ejecución finalizada y validada correctamente en el escenario e implementar sus artefactos en la producción.
   * Las canalizaciones solo de producción reutilizarán los artefactos de las implementaciones de fase, lo que omitirá la fase de creación.

Ni las canalizaciones solo de fase ni las de solo producción se ejecutarán mientras se ejecuta una canalización de producción de pila completa y viceversa.

Estas canalizaciones dedicadas ofrecen más flexibilidad, pero tenga en cuenta los siguientes detalles de funcionamiento y recomendaciones.

>[!NOTE]
>
>Las canalizaciones de solo producción siempre utilizarán los artefactos de la canalización de solo fase, independientemente de lo que se haya implementado en el escenario a través de la canalización de producción asociada estándar mientras tanto.
>
>* Esto podría provocar reversiones de código no deseadas.
>* Adobe recomienda detener el uso de la canalización de producción asociada estándar una vez que comience a utilizar las canalizaciones solo de producción y solo de fase.
>* Si todavía decide ejecutar tanto las canalizaciones acopladas estándar como las canalizaciones de solo ensayo/producción, tenga en cuenta la reutilización de artefactos para evitar reversiones del código.

## Creación de canalizaciones {#pipeline-creation}

Las canalizaciones solo de producción y solo de fase se crean de forma similar a las canalizaciones acopladas estándar [canalizaciones de producción](/help/using/production-pipelines.md) y [canalizaciones que no sean de producción.](/help/using/non-production-pipelines.md) Consulte esos documentos para obtener más información.

1. En el **Canalizaciones** ventana, toque o haga clic en **Agregar canalización**.

   * Seleccionar **Agregar canalización que no sea de producción** para crear una canalización solo de fase.
   * Seleccionar **Agregar canalización de solo producción** para crear una canalización de solo producción.

   ![Creación de una canalización de producción/solo de fase](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Algunas opciones pueden aparecer atenuadas si ya existen las canalizaciones correspondientes.
>
>* **Agregar canalización de solo producción** no estará disponible si una canalización solo de fase aún no existe.
>* **Agregar canalización de producción** no estará disponible si ya existe una canalización acoplada estándar.
>* Solo se permite una canalización de solo producción y una de solo fase por programa.

### Canalizaciones solo de fase {#stage-only}

1. Una vez seleccionada la variable **Agregar canalización que no sea de producción** , la opción **Agregar canalización que no sea de producción** se abre.
1. Para crear una canalización solo de fase, seleccione el entorno de fase en la **Entornos de implementación aptos** para la canalización. Complete los campos restantes y toque o haga clic en **Continuar**.

   ![Creación de una canalización solo de fase](/help/assets/configure-pipelines/stage-only.png)

1. En el **Fase de prueba** , puede definir las pruebas que deben realizarse en el entorno de ensayo. Haga clic o pulse **Guardar** para guardar la nueva canalización.

   ![Parámetros de prueba para una canalización solo de fase](/help/assets/configure-pipelines/stage-only-test.png)

### Canalizaciones de solo producción {#prod-only}

1. Una vez seleccionada la variable **Agregar canalización de solo producción** , la opción **Agregar canalización de solo producción** se abre.
1. Proporcione un **Nombre de canalización**. Las opciones y funcionalidades restantes del cuadro de diálogo funcionan igual que las del cuadro de diálogo de creación de canalización asociada estándar. Haga clic o pulse **Guardar** para guardar la canalización.

   ![Creación de una canalización solo de producción](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Ejecución de canalizaciones solo de producción y solo de fase {#running}

Las canalizaciones solo de producción y solo de fase se ejecutan del mismo modo que [se ejecutan todas las demás canalizaciones.](/help/using/managing-pipelines.md#running-pipelines) Consulte esa documentación para obtener más información.

Además, una ejecución de canalización solo de producción se puede activar directamente desde los detalles de ejecución de una canalización solo de fase.

### Canalizaciones solo de fase {#stage-only-run}

Una canalización solo de fase se ejecuta casi del mismo modo que las canalizaciones acopladas estándar. Sin embargo, al final de la ejecución, después de los pasos de prueba, una **Promocionar compilación** permite iniciar una ejecución de canalización de solo producción que utilice los artefactos implementados en el escenario por esta ejecución y los implemente en la producción.

![Ejecución de canalización solo de fase](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

El **Promocionar compilación** solo aparece si se encuentra en la última ejecución correcta de canalización solo de fase. Una vez que se pulse o se haga clic en esta opción, se le pedirá que confirme la ejecución de la canalización solo de producción o que cree una canalización solo de producción si aún no existe ninguna.

### Canalizaciones de solo producción {#prod-only-run}

Para las canalizaciones solo de producción es importante identificar los artefactos de origen que se van a implementar en la producción. Estos detalles se encuentran en la **Preparación de artefactos** paso. Puede navegar a esas ejecuciones para obtener más detalles y registros.

![Detalles del artefacto](/help/assets/configure-pipelines/prod-only-pipeline-run.png)