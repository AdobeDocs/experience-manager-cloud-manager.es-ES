---
title: Evaluación
seo-title: Evaluación
description: 'Esta página sirve como punto de partida para el aprendizaje de la fase de evaluación en el Asistente para la actualización de productos. '
seo-description: Esta página sirve como punto de partida para el aprendizaje de la fase de evaluación en el Asistente para la actualización de productos.
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
feature: Getting Started
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 1%

---


# Fase de evaluación {#evaluation}

La primera fase del asistente de actualización de producto es **[!UICONTROL Evaluation]**.
Aquí puede evaluar la complejidad de la actualización con el detector de patrones al que puede acceder directamente desde el asistente. Al final de este paso, tendrá acceso al informe de evaluación.

El informe generado permite comprobar la actualización de la instancia de autor detectando patrones que:

* Infrinja ciertas reglas y se realizan en áreas que se verán afectadas o sobrescritas por la actualización.

* Utilice una función AEM 6.x o una API que no sea compatible con la nueva AEM y que pueda romperse después de la actualización.

Esto sirve para evaluar el esfuerzo de desarrollo que implica la actualización a Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Para obtener más información sobre el detector de patrones, consulte [Evaluación de la complejidad de la actualización con Pattern Detector](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Ejecución del evaluador {#running-evaluator}

Siga los pasos a continuación para generar un informe de evaluación:

1. Haga clic en **[!UICONTROL Run Evaluation]**.

   >[!NOTE]
   >
   >El detector de patrones se puede ejecutar en cualquier entorno. Sin embargo, para aumentar la tasa de detección y evitar cualquier ralentización en las instancias críticas para el negocio, Cloud Manager la ejecutará en el entorno de ensayo en la instancia de autor.

   ![](assets/Run-Evaluation.png)

1. El asistente le informa del estado de la acción. Verá **In progress** o **completed** según corresponda cuando se genere el informe de evaluación.

   Una vez generado el informe, puede hacer clic en **[!UICONTROL Download report]** para guardar una copia.

   ![](assets/Evaluation-1.png)


   >[!NOTE]
   >
   >La versión actual del asistente de actualización de producto en Cloud Manager solo admite la fase **Evaluación**. Las otras cuatro fases, a saber **Remediation**, **Execution**, **Validation** y **Completion**, están a punto de llegar próximamente.
