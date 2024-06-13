---
title: Anotaciones de comprobación de GitHub
description: Descubra cómo GitHub comprueba las PR de anotación de sus repositorios privados para proporcionarle comentarios útiles.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 210d40a5e12b40fd84efc461c6a1c48559120837
workflow-type: ht
source-wordcount: '252'
ht-degree: 100%

---


# Anotaciones de comprobación de GitHub {#github-annotations}

Descubra cómo GitHub comprueba las PR de anotación de sus repositorios privados para proporcionarle comentarios útiles.

## Información general {#overview}

Si está utilizando [repositorios privados](private-repositories.md) para su programa Cloud Manager, las comprobaciones en GitHub se ejecutan automáticamente para cada solicitud de extracción. Estas se anotan con información útil para ayudarle a comprender cualquier problema relacionado con el código lo antes posible.

![Ejemplo de anotaciones de comprobación de GitHub](assets/github-check-annotations.png)

Los problemas de [calidad de código](/help/using/code-quality-testing.md) detectados por [SonarQube](/help/using/custom-code-quality-rules.md) se enumeran claramente.

![Ejemplo de anotación de problema de código](assets/github-check-annotations-example.png)

Se proporciona la línea exacta de código donde está el problema para que pueda hacer clic en ella y ver el código afectado. Estas anotaciones se proporcionan para todos los problemas de código, no solo los modificados en la solicitud de extracción.

![Ejemplo de anotación de problema de código](assets/github-check-annotations-example-code.png)

Todas las líneas anotadas se añaden a la pestaña **Archivos modificados** en la solicitud de extracción de GitHub. Las anotaciones para archivos que no se modificaron en la solicitud de extracción aparecen en su propia sección.

![Ejemplo de anotaciones en la pestaña de archivos modificados](assets/github-check-annotations-files-changed.png)

## Código de calidad de las canalizaciones {#code-quality-pipelines}

Los resultados de [calidad de código](/help/using/code-quality-testing.md) también son visibles en la canalización, que Cloud Manager activa automáticamente en la parte inferior de la pestaña **Comprobaciones**. El acceso también es posible a través de **Detalles** de la comprobación de la solicitud de extracción.

![Ejemplo de anotaciones](assets/github-check-annotations-code-quality.png)

![Ejemplo de anotaciones](assets/github-check-annotations-code-quality-2.png)

También puede visualizar los problemas en formato CSV. Esto se puede recuperar [viendo los detalles de la ejecución de canalización en Cloud Manager.](/help/using/managing-pipelines.md)
