---
title: Fase de evaluación
seo-title: Evaluation Phase
description: Descubra cómo la fase de evaluación del Asistente para actualización de productos evalúa la complejidad de la actualización con el detector de patrones.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: ce2145da3b9e605e8a41bac28df520f14e255557
workflow-type: ht
source-wordcount: '296'
ht-degree: 100%

---


# Fase de evaluación {#evaluation}

La primera fase del asistente de actualización de productos es la de **[!UICONTROL Evaluación]**, que mide la complejidad de la actualización con el detector de patrones directamente dentro del asistente. Al final de este paso, tendrá acceso a un informe de evaluación.

El informe generado permite comprobar la idoneidad de la instancia de autor para la actualización mediante la detección de patrones que realizan lo siguiente:

* Infringen ciertas reglas con respecto a las áreas que se verán afectadas o sobrescritas por la actualización.

* Utilizan una función AEM 6.x o una API que no sea compatible con la nueva versión de AEM y que pueda romperse después de la actualización.

El informe sirve para evaluar las actividades de desarrollo que se realizan para actualizar a Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Para obtener más información sobre el detector de patrones, consulte el documento [Evaluación de la complejidad de la actualización con Pattern Detector.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=es)

## Ejecución de la evaluación {#running}

El detector de patrones se puede ejecutar en cualquier entorno. Sin embargo, para aumentar la tasa de detección y evitar cualquier ralentización en las instancias esenciales para el negocio, Cloud Manager la ejecutará en el entorno de ensayo de la instancia de autor.

Siga estos pasos para generar el informe de evaluación.

1. Inicie el asistente como se describe en el documento [Asistente para la actualización de productos.](/help/product-update-wizard/overview.md)

1. Haga clic en **[!UICONTROL Ejecutar evaluación]**.

   ![Ejecutar evaluación](/help/assets/Run-Evaluation.png)

1. El asistente informa el estado de la acción. Cuando se genere el informe de evaluación, verá **En curso** o **completado** según corresponda.

1. Una vez generado el informe, puede hacer clic en **[!UICONTROL Descargar informe]** para guardar una copia.

   ![Informe creado](/help/assets/Evaluation-1.png)

La versión actual del Asistente para la actualización de productos en Cloud Manager es compatible con la fase de **Evaluación** solamente. Las otras cuatro fases, a saber: **Corrección**, **Ejecución**, **Validación** y **Finalización** aparecerán pronto.
