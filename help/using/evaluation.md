---
title: Evaluación
seo-title: Evaluación
description: 'Esta página sirve como punto de partida para la fase de evaluación del aprendizaje en el Asistente de actualizaciones de productos. '
seo-description: Esta página sirve como punto de partida para la fase de evaluación del aprendizaje en el Asistente de actualizaciones de productos.
uuid: 62 d 68 e 79-c 2 ba -4 d 8 b-ba 7 d -33709014 d 5 b 6
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc 91 a 5-be 9 e -4684-8146-d 88 f 4013 d 4 d 1
translation-type: tm+mt
source-git-commit: 47331787d45fe68144cb90c4b907560fe0079b3c

---


# Evaulation Phase {#evaluation}

Una vez que haga clic en Iniciar actualización, la primera fase del Asistente de actualización de producto es la fase de evaluación. En esta fase, puede evaluar la complejidad de la actualización con el detector de patrones accesible directamente desde el asistente. Al finalizar este paso, tendrá acceso al informe de evaluación.

El informe generado permite comprobar la capacidad de actualización de Autor mediante la detección de patrones en uso que:

* Infringe ciertas reglas y se realiza en áreas que se verán afectadas o sobrescribidas por la actualización.

* Utilice una función AEM 6. x o una API que no sea compatible con el nuevo AEM y que pueda pausar después de la actualización.


Esto sirve como una evaluación del esfuerzo de desarrollo que está involucrando la actualización a Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>To learn more about pattern detector, refer to [Assessing the Upgrade Complexity with the Pattern Detector](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Running the Evaluator {#running-evaluator}

Siga los pasos a continuación para ejecutar el evaluador:

1. Select [!UICONTROL Run evaluation] to run the pattern detector. El detector de patrones puede ejecutarse en cualquier entorno. Sin embargo, para aumentar la tasa de detección y evitar cualquier ralentización en las instancias críticas comerciales, el Administrador de nube lo ejecutará en el entorno de ensayo en la instancia de autor.

1. El asistente le informa el estado de la acción. You will notice **In progress** or **completed** as applicable when the evaluation report is being generated.

Once the report is generated, you can select [!UICONTROL Download] to save a copy of the evaluation report.

>[!NOTE]
>The other four phases succeeding **Evaluation** namely **Remediation**, **Execution**, **Validation**, and **Completion** are coming soon and are not available in the current release.
