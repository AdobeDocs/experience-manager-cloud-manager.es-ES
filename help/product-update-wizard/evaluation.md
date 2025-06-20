---
title: Fase de evaluación
seo-title: Evaluation Phase
description: Descubra cómo la fase de evaluación del Asistente para actualización de productos evalúa la complejidad de la actualización con el detector de patrones.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 57%

---


# Fase de evaluación {#evaluation}

La primera fase del Asistente para la actualización de productos es la fase **[!UICONTROL Evaluación]**. Ejecuta el detector de patrones dentro del asistente para evaluar la complejidad de la actualización. Al final de este paso, puede ver el informe de evaluación.

El informe comprueba la preparación de la actualización de la instancia de autor mediante la detección de patrones para lo siguiente:

* Infracciones de reglas en áreas afectadas o sobrescritas por la actualización.
* Utiliza funciones o API de AEM 6.x que no son compatibles con versiones anteriores y pueden romperse después de la actualización.

Este informe ayuda a calcular el esfuerzo de desarrollo necesario para actualizar a Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Para obtener más información sobre el detector de patrones, consulte [Evaluación de la complejidad de la actualización con Pattern Detector](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector).

## Ejecutar el informe de evaluación {#running}

El detector de patrones se puede ejecutar en cualquier entorno. Sin embargo, para aumentar la tasa de detección y evitar cualquier ralentización en las instancias esenciales para el negocio, Cloud Manager la ejecutará en el entorno de ensayo de la instancia de autor.

**Para ejecutar el informe de evaluación:**

1. Inicie el asistente como se describe en el documento [Asistente para la actualización de productos](/help/product-update-wizard/overview.md).

1. Haga clic en **[!UICONTROL Ejecutar evaluación]**.

   ![Ejecutar evaluación](/help/assets/Run-Evaluation.png)

1. El asistente informa el estado de la acción. Cuando se genere el informe de evaluación, verá **En curso** o **completado** según corresponda.

1. Una vez generado el informe, puede hacer clic en **[!UICONTROL Descargar informe]** para guardar una copia.

   ![Informe creado](/help/assets/Evaluation-1.png)

El Asistente para la actualización de productos actual de Cloud Manager sólo admite la fase **Evaluación**. Las otras cuatro fases, a saber: **Corrección**, **Ejecución**, **Validación** y **Finalización** aparecerán pronto.
