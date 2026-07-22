---
title: Fase de evaluación
seo-title: Evaluation Phase
description: Descubra cómo la fase de evaluación del Asistente para actualización de productos evalúa la complejidad de la actualización con el detector de patrones.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
TQID: https://experienceleague.adobe.com/dj-Wnq9FagNI3mzzVHcUH-sOufzb02D0juHqhtgpon0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 1b146c2a01d3371ed2fe014a15a84ddee2cd9b6c
workflow-type: tm+mt
source-wordcount: 270
ht-degree: 40%

---

# Fase de evaluación {#evaluation}

La primera fase del Asistente para la actualización de productos es la fase **[!UICONTROL Evaluación]**. Ejecuta el detector de patrones dentro del asistente para evaluar la complejidad de la actualización. Al final de este paso, puede ver el informe de evaluación.

El informe comprueba la preparación de la actualización de la instancia de autor mediante la detección de patrones para lo siguiente:

* Infracciones de reglas en áreas afectadas o sobrescritas por la actualización.
* Detecta funciones o API de AEM 6.x que no son compatibles con versiones anteriores y pueden fallar después de la actualización.

Este informe ayuda a calcular el esfuerzo de desarrollo necesario para actualizar a Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Para obtener más información sobre el detector de patrones, consulte [Evaluación de la complejidad de la actualización con Pattern Detector](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector).

## Ejecutar el informe de evaluación {#running}

El detector de patrones se puede ejecutar en cualquier entorno. Sin embargo, para aumentar la tasa de detección y evitar cualquier impacto en el rendimiento de las instancias críticas, Cloud Manager la ejecuta en el entorno de ensayo de la instancia de autor.

**Para ejecutar el informe de evaluación:**

1. Inicie el asistente como se describe en el documento [Asistente para la actualización de productos](/help/product-update-wizard/overview.md).

1. Haga clic en **[!UICONTROL Ejecutar evaluación]**.

   ![Ejecutar evaluación](/help/assets/Run-Evaluation.png)

1. El asistente informa el estado de la acción. Nota **En curso** o **Completada**, según corresponda, mientras se genera el informe de evaluación.

1. Una vez generado el informe, puede hacer clic en **[!UICONTROL Descargar informe]** para guardar una copia.

   ![Informe creado](/help/assets/Evaluation-1.png)

El Asistente para la actualización de productos actual de Cloud Manager sólo admite la fase **Evaluación**. Las otras cuatro fases, a saber: **Remediación**, **Ejecución**, **Validación** y **Finalización**, estarán disponibles pronto.
