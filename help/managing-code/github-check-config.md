---
title: Configuración de comprobación de GitHub para repositorios privados
description: Obtenga información sobre cómo controlar las canalizaciones que se crean automáticamente para validar cada solicitud de extracción en un repositorio privado.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 39%

---

# GitHub comprueba la configuración de los repositorios privados {#github-check-config}

Obtenga información sobre cómo controlar las canalizaciones que se crean automáticamente para validar cada solicitud de extracción en un repositorio privado.

## Configuración de las comprobaciones de GitHub {#configuration}

Al usar [repositorios privados](private-repositories.md#using), se crea automáticamente una [canalización de calidad de código de pila completa](/help/overview/ci-cd-pipelines.md). Esta canalización se inicia en cada actualización de solicitud de extracción.

Puede controlar estas comprobaciones creando un archivo `.cloudmanager/pr_pipelines.yml` en la rama predeterminada del repositorio privado.

```yaml
github:
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
| `shouldDeletePreviousComment` | `true` o `false` | `false` | Si se conserva solo el último comentario con los resultados del análisis de código de esta solicitud de extracción de GitHub o se conserva todo. |
| `type` | `CI_CD` | N/D | Define el comportamiento de una canalización de CI/CD. |
| `template.programID` | Entero | No se reutilizan variables de canalización | Puede reutilizar las [variables de canalización](/help/getting-started/build-environment.md#pipeline-variables) establecidas en una canalización existente, que cada PR crea automáticamente. |
| `template.pipelineID` | Entero | No se reutilizan variables de canalización | Puede reutilizar las [variables de canalización](/help/getting-started/build-environment.md#pipeline-variables) establecidas en una canalización existente, que cada PR crea automáticamente. |
| `namePrefix` | Cadena | `Full Stack Code Quality Pipeline for PR` | Se utiliza para establecer el nombre de la canalización que se crea automáticamente. |
| `importantMetricsFailureBehavior` | `CONTINUE` o `FAIL` o `PAUSE` | `CONTINUE` | Establece el comportamiento de la métrica importante de la canalización<br>`CONTINUE` = Si falla una métrica importante, la canalización avanza automáticamente<br>`FAIL` = La canalización termina con un estado FALLIDO si falla una métrica importante<br>`PAUSE` = El paso de análisis de código recibe un estado ESPERANDO cuando falla una métrica importante y debe reanudarse manualmente. |
