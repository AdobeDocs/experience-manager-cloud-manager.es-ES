---
title: Dividir canalizaciones solo de fase y solo de producción
description: Descubra cómo puede dividir las implementaciones de fase y producción mediante canalizaciones dedicadas.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
TQID: https://experienceleague.adobe.com/whq-Hkwp3mjTr0iftoKZHKdsi0xaKtVXazXjUENoaLk
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 6b0075d2405e89dce1c883a2b5fc0bd952a3fddd
workflow-type: tm+mt
source-wordcount: 975
ht-degree: 53%

---

# Dividir canalizaciones solo de fase y de producción {#stage-prod-only}

Puede dividir las implementaciones de ensayo y producción mediante canalizaciones dedicadas.

## Información general {#overview}

Los entornos de ensayo y producción están perfectamente asociados. De forma predeterminada, estas implementaciones están vinculadas a una sola canalización. Una canalización de implementación se implementa en los entornos de ensayo y producción de ese programa. Aunque este acoplamiento suele ser adecuado, hay ciertos casos de uso en los que se producen desventajas:

* Si desea implementar en el ensayo, omita el paso **Promocionar a producción** de la canalización. Sin embargo, la ejecución se marca como cancelada.
* Si desea implementar el código más reciente de un entorno de ensayo en producción, debe volver a implementar toda la canalización, incluida la implementación de ensayo, aunque no se haya cambiado ningún código allí.
* Los entornos no se pueden actualizar durante las implementaciones. Si retrasa las pruebas en el entorno de ensayo durante varios días antes de la promoción a producción, el entorno de producción permanece bloqueado y no se puede actualizar. Esto hace que las tareas no dependientes, como la actualización de las [variables de entorno](/help/getting-started/build-environment.md#environment-variables), sean imposibles.

Las canalizaciones solo de fase y de solo producción ofrecen soluciones para estos casos de uso al proporcionar opciones de implementación dedicadas.

* **Canalizaciones de implementación solo de fase:** Implementar solo en un entorno de ensayo con la ejecución finalizada una vez que se hayan realizado la implementación y las pruebas. Una canalización de solo fase se comporta de forma idéntica a la canalización de producción de pila completa asociada estándar, pero sin los pasos de implementación de producción (aprobación, programación, implementación).
* **Canalizaciones de implementación solo de producción:** Implementan solo en producción al seleccionar la ejecución de fase exitosa más reciente. A continuación, implemente los artefactos en producción. Las canalizaciones solo de producción reutilizan artefactos de implementación de fase, lo que omite la fase de compilación.

Las canalizaciones solo de fase y de solo producción no se ejecutan mientras una canalización de producción de pila completa está en curso y viceversa. Si tanto la canalización de solo fase como la de producción de pila completa tienen configurado el activador **Cambios en Git** y apuntan a la misma rama y repositorio, solo se inicia automáticamente la canalización de solo fase. Las canalizaciones de solo producción no almacenan en déclencheur a **`On Git Changes`** porque no están vinculadas directamente a un repositorio.

Las canalizaciones solo de producción se activan manualmente, ya que no están vinculadas directamente a un repositorio para **Cambios en Git**.

Estas canalizaciones dedicadas ofrecen más flexibilidad, pero tenga en cuenta los siguientes detalles de funcionamiento y recomendaciones:

>[!NOTE]
>
>Las canalizaciones solo de producción siempre utilizan artefactos de la canalización solo de fase. Este proceso sigue siendo válido incluso si la canalización de producción acoplada estándar ha implementado algo más para ensayo mientras tanto.
>
>* Este escenario provoca reversiones de código no deseadas.
>* Adobe recomienda detener el uso de la canalización de producción acoplada estándar una vez que comience a utilizar las canalizaciones solo de producción y de solo fase.
>* Si todavía decide ejecutar tanto las canalizaciones asociadas estándar como las canalizaciones de solo fase/producción, tenga en cuenta la reutilización de artefactos para evitar reversiones del código.

## Creación de canalizaciones {#pipeline-creation}

Las canalizaciones solo de producción y solo de fase se crean de manera similar a las [canalizaciones de producción](/help/using/production-pipelines.md) y [canalizaciones que no son de producción](/help/using/non-production-pipelines.md) acopladas estándar. Consulte estos documentos para obtener más información.

1. En la ventana **Canalizaciones**, haga clic en **Agregar canalización**.

   * Seleccione **Agregar canalización que no sea de producción** para crear una canalización de solo fase.
   * Seleccione **Agregar canalización de solo producción** para crear una canalización de solo producción.

   ![Creación de una canalización de solo producción/solo fase](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Algunas opciones aparecen atenuadas si ya existen las canalizaciones correspondientes.
>
>* **Agregar canalización de solo producción** no está disponible si todavía no existe una canalización de solo fase.
>* **Agregar canalización de producción** no está disponible si ya existe una canalización asociada estándar.
>* Solo se permite una canalización de solo producción y una de solo fase por programa.

### Canalizaciones de solo fase {#stage-only}

1. Una vez seleccionada la opción **Añadir canalización que no sea de producción**, se abre el cuadro de diálogo **Añadir canalización que no sea de producción**.
1. Para crear una canalización de solo fase, seleccione el entorno de fase en el campo **Entornos de implementación aptos** para la canalización.
1. Rellene los campos restantes.
1. Haga clic en **Continuar**.

   ![Creación de una canalización de solo fase](/help/assets/configure-pipelines/stage-only.png)

1. En la ficha **Prueba de ensayo**, defina la prueba que se realizará en el entorno de ensayo.
1. Haga clic en **Guardar**.

   ![Parámetros de prueba para una canalización de solo fase](/help/assets/configure-pipelines/stage-only-test.png)

### Canalizaciones de solo producción {#prod-only}

1. Después de hacer clic en **Agregar canalización solo de producción**, se abre el cuadro de diálogo asociado.
1. En el campo **Nombre de canalización**, escriba el nombre que desee. Las opciones y funcionalidades restantes del cuadro de diálogo funcionan igual que las del cuadro de diálogo de creación de canalización asociada estándar.
1. En la esquina inferior derecha del cuadro de diálogo, haga clic en **Guardar**.

   ![Creación de una canalización de solo producción](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Ejecución de canalizaciones de solo producción y de solo fase {#running}

Las canalizaciones de solo producción y de solo fase se ejecutan del mismo modo que [se ejecutan todas las demás canalizaciones](/help/using/managing-pipelines.md#running-pipelines). Consulte la documentación para obtener más detalles. Sin embargo, hay dos nuevas características de estas canalizaciones.

* Las canalizaciones solo de fase y de solo producción ofrecen un nuevo [modo de emergencia](#emergency-mode) para omitir las pruebas.
* Se puede activar una ejecución de canalización solo de producción directamente desde los detalles de ejecución de una [canalización solo de etapa](#stage-only-run).

### Modo de emergencia {#emergency-mode}

Al iniciar canalizaciones de solo producción y de solo ensayo, se le pedirá que confirme el inicio y cómo se realiza.

* **Modo normal** es una ejecución estándar e incluye pasos de prueba de etapa.
* **Modo de emergencia** omite los pasos de la prueba de fase.

![Modo de emergencia](/help/assets/configure-pipelines/emergency-mode.png)

### Canalizaciones de solo fase {#stage-only-run}

Una canalización de solo fase se ejecuta casi del mismo modo que las canalizaciones asociadas estándar. Sin embargo, al final de la ejecución, después de los pasos de prueba, aparece el botón **Promocionar compilación**. Este botón permite iniciar una ejecución de canalización solo de producción. Utiliza los artefactos que se implementaron para ensayo en la ejecución. A continuación, los implementa en producción.

![Ejecución de canalización de solo fase](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Al hacer clic en **Promocionar compilación**, se le pedirá que confirme la ejecución de la canalización de solo producción relacionada, ya sea de forma normal o en [modo de emergencia](#emergency-mode).

Si no existe ninguna canalización de solo producción, se le solicitará que cree una.

### Canalizaciones de solo producción {#prod-only-run}

Para las canalizaciones solo de producción, asegúrese de identificar los artefactos de origen que desea implementar en producción. Estos detalles se encuentran en el paso **Preparación de artefactos**. Puede navegar a esas ejecuciones para obtener más detalles y registros.

![Detalles del artefacto](/help/assets/configure-pipelines/prod-only-pipeline-run.png)

