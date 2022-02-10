---
title: Canalización de CI/CD
seo-title: CI/CD Pipeline
description: Información general sobre la canalización de CI/CD, que gestiona las implementaciones en la fase y producción en Cloud Manager
seo-description: Follow this section to learn about the CI/CD pipeline, which handles deployments to stage and production in Cloud Manager
uuid: 763ddb24-05cd-463f-8d72-a2e69bbe6b7e
topic-tags: introduction
discoiquuid: 1cdb76eb-1a91-4689-8579-0fa9fccc0592
feature: CI-CD Pipeline
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 1%

---

# Canalización de CI/CD {#ci-cd-pipeline}

## Información general de canalización {#pipeline-overview}

[!UICONTROL Cloud Manager] incluye un marco de integración continua (CI) y entrega continua (CD) que permite a los equipos de implementación probar y entregar rápidamente código nuevo o actualizado. Por ejemplo, los equipos de implementación pueden configurar, configurar e iniciar una canalización automatizada de CD/CI que aproveche las prácticas recomendadas de codificación de Adobe para realizar un análisis exhaustivo del código y garantizar la máxima calidad del código.

La canalización CI/CD también automatiza los procesos de prueba de unidades y performance para aumentar la eficiencia de la implementación e identificar de manera proactiva los problemas críticos que son costosos de solucionar después de la implementación. Los equipos de implementación pueden acceder a un informe completo de rendimiento del código para obtener visibilidad sobre el impacto potencial en los KPI y las validaciones de seguridad críticas si el código se implementa en la producción.

## Proceso de canalización {#pipeline-process}

El diagrama siguiente ilustra lo que sucede una vez que se activa una versión en [!UICONTROL Cloud Manager]. La tabla adjunta explica cada paso del flujo de trabajo.

![](assets/screen_shot_2018-05-30at82457pm.png)

La siguiente tabla detalla lo que está sucediendo durante cada paso del proceso:

| Paso del proceso de canalización | ¿Qué está pasando? |
|---|---|
| 1. Iniciar una versión | Un administrador de implementación déclencheur una versión manualmente, con una confirmación de Git o según una programación recurrente. |
| 2. Crear etiqueta de versión | [!UICONTROL Cloud Manager] crea una etiqueta Git para marcar la versión con un número de versión generado automáticamente. Por ejemplo: 2018,531,245527,0000001222 |
| 3. Creado como versión con versión generada automáticamente | [!UICONTROL Cloud Manager] crea la aplicación con el número de versión recién asignado. |
| 4. Evaluar la calidad del código | [!UICONTROL Cloud Manager] analiza el código fuente y proporciona un resumen antes de que el código se pueda implementar en el entorno de ensayo |
| 5. Artefactos con versión almacenados | Los artefactos de la versión se almacenan para su uso posterior en los pasos de implementación. |
| 6. Despliegue automático de artefactos en la fase de AEM de AMS | El artefacto de la versión se implementa en el entorno de ensayo. |
| 7. Déclencheur de pruebas automatizadas | [!UICONTROL Cloud Manager] ejecuta las pruebas de rendimiento y seguridad en el artefacto. |
| 8. Implementación del Déclencheur de producción | Una vez completadas las pruebas automatizadas [!UICONTROL Cloud Manager] inicia la implementación en producción. |
| 9. [!UICONTROL Cloud Manager] obtiene artefactos para implementar | [!UICONTROL Cloud Manager] extrae los artefactos de liberación almacenados. |
| 10. Propagación de artefactos a la producción | Los artefactos de la versión se implementan en el entorno de producción. |

### Configuración de una canalización de CI/CD {#how-to-setup-a-ci-cd-pipeline}

Para obtener más información sobre la configuración de la canalización, consulte los documentos [Configuración de canalizaciones de producción](configuring-production-pipelines.md) y [Configuración de canalizaciones que no sean de producción.](configuring-non-production-pipelines.md)

## Puertas de calidad {#quality-gates}

La canalización de CI/CD proporciona puertas de calidad o criterios de aceptación que deben cumplirse antes de poder mover el código del entorno de ensayo al entorno de implementación. Hay tres puertas en la canalización:

* Calidad de código
* Pruebas de rendimiento
* Pruebas de seguridad

Para cada una de estas puertas, hay tres niveles de problemas identificados:

* **Importante** - problemas identificados por la puerta que causan un fallo inmediato de la tubería.
* **Importante** - problemas identificados por la puerta que hacen que la canalización entre en estado pausado. Un administrador de implementación, un administrador de proyectos o un propietario de empresa pueden anular los problemas, en cuyo caso la canalización continúa, o pueden aceptar los problemas, en cuyo caso la canalización se detiene con un error.
* **Información** - problemas identificados por la puerta que se proporcionan exclusivamente con fines informativos y no tienen impacto en la ejecución de la canalización.

El siguiente es un ejemplo de análisis de código con problemas identificados para el código:

![](assets/quality-gate-failed.png)

### Configuración de puertas {#how-to-setup-gates}

Consulte el documento [Configuración de canalizaciones de producción](configuring-production-pipelines.md) para obtener más información sobre la configuración de las puertas de código, calidad y rendimiento.
