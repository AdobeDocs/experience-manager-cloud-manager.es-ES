---
title: Comprobaciones de solicitudes de extracción para repositorios privados
description: Obtenga información sobre cómo controlar las canalizaciones que se crean automáticamente para validar cada solicitud de extracción en un repositorio privado.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
TQID: https://experienceleague.adobe.com/duceoXUt2SqWI0ZXzyuqZtszLfJkWr53G5O5ze4nxTY
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: b52942282fe5f825181123b3839ef155753c5e23
workflow-type: tm+mt
source-wordcount: 237
ht-degree: 91%

---

# La solicitud de extracción comprueba los repositorios privados {#github-check-config}

<!--OLD TITLE THAT I THOUGHT WAS BETTER Check configuration for private repositories -->

Obtenga información sobre cómo controlar las canalizaciones que se crean automáticamente para validar cada solicitud de extracción en un repositorio privado.

## Configuración de comprobaciones de repositorios privados {#configuration}

Cuando se usan [repositorios privados](private-repositories.md#using), se crea automáticamente una [canalización de calidad de código de pila completa](/help/overview/ci-cd-pipelines.md). Esta canalización se inicia en cada actualización de solicitud de extracción.

Puede controlar estas comprobaciones creando un archivo `.cloudmanager/pr_pipelines.yml` en la rama predeterminada del repositorio privado.

```yaml
pullRequest:
  shouldDeletePreviousComment: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR
    importantMetricsFailureBehavior: CONTINUE
```

| Parámetro | Valores posibles | Predeterminado | Descripción |
| --- | --- | --- | --- |
| `shouldDeletePreviousComment` | `true` o `false` | `false` | Si se conserva solo el último comentario con los resultados del análisis de código de esta solicitud de extracción de GitHub o si se conserva todo. |
| `type` | `CI_CD` | N/D | Define el comportamiento de una CI/CD Pipeline. |
| `template.programID` | Entero | No se reutilizan variables de canalización | Puede reutilizar las [variables de canalización](/help/getting-started/build-environment.md#pipeline-variables) establecidas en una canalización existente, que cada PR crea automáticamente. |
| `template.pipelineID` | Entero | No se reutilizan variables de canalización | Puede reutilizar las [variables de canalización](/help/getting-started/build-environment.md#pipeline-variables) establecidas en una canalización existente, que cada PR crea automáticamente. |
| `namePrefix` | Cadena | `Full Stack Code Quality Pipeline for PR` | Se utiliza para establecer el nombre de la canalización que se crea automáticamente. |
| `importantMetricsFailureBehavior` | `CONTINUE` o `FAIL` o `PAUSE` | `CONTINUE` | Establece el comportamiento de las métricas importantes de la canalización<br>`CONTINUE` = Si falla una métrica importante, la canalización avanzará automáticamente<br>`FAIL` = La canalización finalizará con el estado ERROR si falla una métrica importante<br>`PAUSE` = El paso de análisis de código recibirá un estado de ESPERA cuando falle una métrica importante y se deberá reanudar manualmente. |
