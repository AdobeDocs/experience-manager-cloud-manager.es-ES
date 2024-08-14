---
title: Canalizaciones de solo fase y de producción
description: Descubra cómo puede dividir las implementaciones de fase y producción mediante canalizaciones dedicadas.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: 77eb1c824ba766e43dfd8e2b0f6f6edc71f043e5
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 31%

---

# Canalizaciones solo de fase y de producción {#stage-prod-only}

Descubra cómo puede dividir las implementaciones de fase y producción mediante canalizaciones dedicadas.

>[!NOTE]
>
>Esta característica solo está disponible para [el programa que la adoptó por primera vez](/help/release-notes/current.md#early-adoption).

## Información general {#overview}

Los entornos de ensayo y producción están perfectamente asociados. De forma predeterminada, estas implementaciones están vinculadas a una sola canalización. Es decir, una canalización de implementación se implementa en los entornos de ensayo y producción de ese programa. Aunque este acoplamiento suele ser adecuado, hay ciertos casos de uso en los que existen desventajas:

* Si desea implementar solo en fase, rechaza el paso **Promocionar a producción** de la canalización. Sin embargo, la ejecución se marca como cancelada.
* Si desea implementar el código más reciente en un entorno de ensayo en producción, debe volver a implementar toda la canalización, incluida la implementación de ensayo, aunque no se haya cambiado ningún código allí.
* Los entornos no se pueden actualizar durante las implementaciones. Si se detiene para probar en el entorno de ensayo durante varios días antes de pasar a producción, el entorno de producción permanece bloqueado y no se puede actualizar. Este escenario hace que las tareas que no dependen, como actualizar [variables de entorno](/help/getting-started/build-environment.md#environment-variables), sean imposibles.

Las canalizaciones de solo fase y producción ofrecen soluciones para estos casos de uso al proporcionar opciones de implementación dedicadas.

* **Canalizaciones de implementación solo de fase:** Implementa solo en un entorno de ensayo y finaliza la ejecución una vez que se han realizado la implementación y las pruebas. Una canalización de solo fase se comporta de forma idéntica a la canalización de producción de pila completa asociada estándar, pero sin los pasos de implementación de producción (aprobación, programación, implementación).
* **Canalizaciones de implementación solo de producto:** se implementa solamente en producción al seleccionar una ejecución de fase que se realizó correctamente. A continuación, implemente sus artefactos en producción. Las canalizaciones solo de producción reutilizan artefactos de implementación de fase, omitiendo la fase de compilación.

Las canalizaciones solo de fase y de solo producción no se ejecutan mientras una canalización de producción de pila completa está en curso y viceversa. Si tanto la canalización de solo fase como la de producción de pila completa tienen configurado el activador **Cambios en Git** y apuntan a la misma rama y repositorio, solo se inicia automáticamente la canalización de solo fase. Las canalizaciones de solo producción no inician **`On Git Changes`** porque no están vinculadas directamente a un repositorio.

Las canalizaciones solo de producción se activan manualmente, ya que no están vinculadas directamente a un repositorio para **Cambios en Git**.

Estas canalizaciones dedicadas ofrecen más flexibilidad, pero debe tener en cuenta los siguientes detalles de funcionamiento y recomendaciones.

>[!NOTE]
>
>Las canalizaciones solo de producción siempre utilizan artefactos de la canalización solo de fase. Este proceso sigue siendo válido incluso si la canalización de producción acoplada estándar ha implementado algo más para ensayo mientras tanto.
>
>* Este tipo de escenario podría provocar reversiones de código no deseadas.
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

1. En la ficha **Prueba de ensayo**, puede definir las pruebas que se deben realizar en el entorno de ensayo. Haga clic en **Guardar** para guardar su nueva canalización.

   ![Parámetros de prueba para una canalización de solo fase](/help/assets/configure-pipelines/stage-only-test.png)

### Canalizaciones de solo producción {#prod-only}

1. Una vez seleccionada la opción **Agregar canalización solo de producción**, se abrirá el cuadro de diálogo **Agregar canalización solo de producción**.
1. Proporcione un **nombre para la canalización**. Las opciones y funciones restantes del cuadro de diálogo funcionan igual que las opciones que se encuentran en el cuadro de diálogo de creación de canalización acoplada estándar. Haga clic en **Guardar** para guardar la canalización.

   ![Creación de una canalización de solo producción](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Ejecutar canalizaciones solo de producción y solo de fase {#running}

Las canalizaciones de solo producción y de solo fase se ejecutan en gran medida de la misma manera que [ todas las demás canalizaciones.](/help/using/managing-pipelines.md#running-pipelines) Consulte esa documentación para obtener detalles. Sin embargo, hay dos nuevas características de estas canalizaciones.

* Las canalizaciones solo de fase y de solo producción ofrecen un nuevo [modo de emergencia](#emergency-mode) para permitir omitir las pruebas.
* La ejecución de canalizaciones solo de producción se puede activar directamente a partir de los detalles de ejecución de una canalización [solo de etapa.](#stage-only-run)

### Modo de emergencia {#emergency-mode}

Siempre que inicie canalizaciones solo de producción y en línea de ensayo, se le pedirá que confirme el inicio y cómo se iniciará.

* **Modo normal** es una ejecución estándar e incluye pasos de prueba de etapa.
* **Modo de emergencia** omite los pasos de la prueba de fase.

![Modo de emergencia](/help/assets/configure-pipelines/emergency-mode.png)

### Canalizaciones solo de fase {#stage-only-run}

Una canalización de solo fase se ejecuta casi del mismo modo que las canalizaciones asociadas estándar. Sin embargo, al final de la ejecución, después de los pasos de prueba, aparece el botón **Promocionar compilación**. Este botón permite iniciar una ejecución de canalización solo de producción utilizando los artefactos implementados en el escenario en la ejecución e implementarlos en la producción.

![Ejecución de canalización de solo fase](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Al hacer clic en **Promocionar compilación**, se le solicitará que confirme la ejecución de la canalización de solo fase relacionada, ya sea de forma normal o en [modo de emergencia.](#emergency-mode)

Si no existe ninguna canalización de solo producción, se le solicitará que cree una.

### Canalizaciones de solo producción {#prod-only-run}

Para las canalizaciones solo de producción, es importante identificar los artefactos de origen que se van a implementar en la producción. Estos detalles se encuentran en el paso **Preparación de artefactos**. Puede navegar a esas ejecuciones para obtener más detalles y registros.

![Detalles del artefacto](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
