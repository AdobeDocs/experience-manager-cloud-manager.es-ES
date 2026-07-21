---
title: Anotaciones de comprobación de GitHub
description: Descubra cómo GitHub comprueba las PR de anotación de sus repositorios privados para proporcionarle comentarios útiles.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 147eec6368875aabb252d759909c0309a82ef3db
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 32%

---


# Anotaciones de comprobación de GitHub {#github-annotations}

Descubra cómo GitHub comprueba las PR de anotación de sus repositorios privados para proporcionarle comentarios.

## Información general {#overview}

Si usa [repositorios privados](private-repositories.md) para su programa de Cloud Manager, comprueba que GitHub se ejecute automáticamente para cada solicitud de extracción. Estas comprobaciones incluyen anotaciones con información que le ayudará a identificar cualquier problema con su código lo antes posible.

![Ejemplo de anotaciones de comprobación de GitHub](assets/github-check-annotations.png)

Los problemas de [calidad de código](/help/using/code-quality-testing.md) detectados por [SonarQube](/help/using/custom-code-quality-rules.md) se enumeran claramente.

![Ejemplo de anotación de problema de código](assets/github-check-annotations-example.png)

Se proporciona la línea de código exacta con el problema y puede seleccionarla para ver el código correspondiente. Estas anotaciones se proporcionan para todos los problemas de código, no solo para los de la solicitud de extracción.

![Ejemplo de anotación de problema de código](assets/github-check-annotations-example-code.png)

Todas las líneas anotadas se añaden a la pestaña **Archivos modificados** en la solicitud de extracción de GitHub. Las anotaciones para archivos no modificados en la solicitud de extracción aparecen en una sección independiente.

![Ejemplo de anotaciones en la pestaña de archivos modificados](assets/github-check-annotations-files-changed.png)

## Código de calidad de las canalizaciones {#code-quality-pipelines}

Los resultados de [Calidad del código](/help/using/code-quality-testing.md) también están visibles en la canalización, que Cloud Manager déclencheur automáticamente, en la parte inferior de la pestaña **Comprobaciones**. También se puede acceder a él desde los **detalles** de la comprobación de la solicitud de extracción.

![Ejemplo de anotaciones](assets/github-check-annotations-code-quality.png)

![Ejemplo de anotaciones](assets/github-check-annotations-code-quality-2.png)

También puede ver los problemas como archivo CSV. Puede acceder a esta información [viendo los detalles de la ejecución de la canalización en Cloud Manager](/help/using/managing-pipelines.md).
