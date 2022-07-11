---
title: Canalizaciones CI/CD
description: Obtenga información sobre las canalizaciones de CI/CD y cómo administran las implementaciones en entornos de ensayo y producción en Cloud Manager.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---


# Canalizaciones CI/CD {#ci-cd-pipeline}

Obtenga información sobre las canalizaciones de CI/CD y cómo administran las implementaciones en entornos de ensayo y producción en Cloud Manager.

## Información general {#overview}

[!UICONTROL Cloud Manager] incluye un marco de integración continua/entrega continua (CI/CD), que permite a los equipos de implementación probar y entregar rápidamente código nuevo o actualizado. Por ejemplo, los equipos de implementación pueden configurar, configurar e iniciar una canalización automatizada de CD/CI que aproveche las prácticas recomendadas de codificación de Adobe para realizar un análisis exhaustivo del código y garantizar la máxima calidad del código.

La canalización CI/CD también automatiza los procesos de prueba de unidades y performance para aumentar la eficiencia de la implementación e identificar proactivamente los problemas críticos que son costosos de solucionar después de la implementación. Los equipos de implementación pueden acceder a un informe completo de rendimiento del código para obtener visibilidad sobre el impacto potencial en los KPI y las validaciones de seguridad críticas si el código se implementa en la producción.

## El proceso de canalización {#pipeline-process}

Este diagrama ilustra lo que sucede una vez que se activa una versión en [!UICONTROL Cloud Manager] uso de una canalización.

![Proceso de canalización](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Paso de canalización | Descripción |
|---|---|
| 1. Iniciar una versión | Un administrador de implementación déclencheur una versión manualmente, con una confirmación de Git o en función de una programación recurrente. |
| 2. Crear etiqueta de versión | [!UICONTROL Cloud Manager] crea una etiqueta git para marcar la versión con un número de versión generado automáticamente, por ejemplo: `2018.531.245527.0000001222`. |
| 3. Creado como versión con versión autogenerada | [!UICONTROL Cloud Manager] crea la aplicación con el número de versión recién asignado. |
| 4. Evaluar la calidad del código | [!UICONTROL Cloud Manager] analiza el código fuente y proporciona un resumen antes de que el código se pueda implementar en el entorno de ensayo. |
| 5. Artefactos con versiones almacenados | Los artefactos de la versión se almacenan para su uso posterior en los pasos de implementación. |
| 6. Implementación automática de artefactos en el ensayo de AEM de AMS | El artefacto de la versión se implementa en el entorno de ensayo. |
| 7. Pruebas automatizadas de Déclencheur | [!UICONTROL Cloud Manager] ejecuta pruebas de rendimiento y seguridad en el artefacto. |
| 8. Implementación del déclencheur de producción | Una vez completadas las pruebas automatizadas, [!UICONTROL Cloud Manager] inicia la implementación en producción. |
| 9. [!UICONTROL Cloud Manager] obtiene artefactos para implementar | [!UICONTROL Cloud Manager] extrae los artefactos de liberación almacenados. |
| 10. Implementar artefactos en producción | Los artefactos de la versión se implementan en el entorno de producción. |

### Configuración de una canalización de CI/CD {#how-to-setup-a-ci-cd-pipeline}

Para obtener más información sobre la configuración de la canalización, consulte los documentos [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) y [Configuración de canalizaciones que no sean de producción.](/help/using/non-production-pipelines.md)

## Puertas de calidad {#quality-gates}

La canalización CI/CD proporciona puertas de calidad o criterios de aceptación que deben cumplirse para que el código pueda moverse del entorno de ensayo al entorno de implementación. Hay tres puertas en la canalización:

* Calidad de código
* Pruebas de rendimiento
* Pruebas de seguridad

Para cada una de estas puertas, hay tres niveles de problemas que se pueden identificar:

* **Importante** - Los problemas críticos identificados por la puerta causan un fallo inmediato de la tubería.
* **Importante** - Problemas importantes identificados por la puerta hacen que la canalización introduzca un estado pausado. Un administrador de implementación, un administrador de proyectos o un propietario de empresa pueden anular los problemas, en cuyo caso la canalización continúa, o pueden aceptar los problemas, en cuyo caso la canalización se detiene con un error.
* **Información** - Los problemas de información identificados por la puerta se proporcionan exclusivamente con fines informativos y no tienen impacto en la ejecución de la canalización.

Este es un ejemplo de análisis de código con problemas identificados.

![Ejemplo de análisis de código](/help/assets/quality-gate-failed.png)

### Cómo configurar las puertas {#how-to-setup-gates}

Consulte el documento [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) para obtener más información sobre la configuración de las puertas de código, calidad y rendimiento.
