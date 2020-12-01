---
title: Canalización de CI/CD
seo-title: Canalización de CI/CD
description: nulo
seo-description: Siga esta sección para obtener información sobre el canalizador de CI/CD, que gestiona las implementaciones en el escenario y la producción en Cloud Manager.
uuid: 763ddb24-05cd-463f-8d72-a2e69bbe6b7e
topic-tags: introduction
discoiquuid: 1cdb76eb-1a91-4689-8579-0fa9fccc0592
translation-type: tm+mt
source-git-commit: 8580cec50ac5dafb4e2525371a39d58c82f1cbc9
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 1%

---


# Canalización de CI/CD {#ci-cd-pipeline}

## Información general de canalización {#pipeline-overview}

[!UICONTROL Cloud Manager] incluye un módulo de integración continua (CI) y Envío continuo (CD) que permite a los equipos de implementación probar y entregar rápidamente código nuevo o actualizado. Por ejemplo, los equipos de implementación pueden configurar, configurar y inicio una canalización automatizada de CI/CD que aprovecha las optimizaciones de codificación de Adobe para realizar un análisis de código exhaustivo y garantizar la máxima calidad del código.

La canalización CI/CD también automatiza los procesos de prueba de unidades y performance para aumentar la eficiencia de la implementación e identificar de manera proactiva los problemas críticos que son costosos de solucionar después de la implementación. Los equipos de implementación pueden acceder a un informe de rendimiento de código completo para obtener visibilidad sobre el impacto potencial en los KPI y las validaciones de seguridad críticas si el código se implementa en la producción.

## Proceso de canalización {#pipeline-process}

El diagrama siguiente ilustra lo que sucede una vez que se activa una versión en [!UICONTROL Cloud Manager]. La tabla adjunta explica cada paso del flujo de trabajo.

![](assets/screen_shot_2018-05-30at82457pm.png)

En la tabla siguiente se detalla lo que sucede durante cada paso del proceso:

| Etapa de proceso de canalización | ¿Qué está pasando? |
|---|---|
| 1. Inicio de una versión | Un administrador de implementación desencadena una versión manualmente, con una confirmación Git o según una programación recurrente. |
| 2. Crear etiqueta de lanzamiento | [!UICONTROL Cloud Manager] crea una etiqueta Git para marcar la versión con un número de versión generado automáticamente. Por ejemplo: 2018.531.245527.0000001222 |
| 3. Creado como versión con versión generada automáticamente | [!UICONTROL Cloud Manager] crea la aplicación con el número de versión recién asignado. |
| 4. Evaluar la calidad del código | [!UICONTROL Cloud Manager] analiza el código fuente y proporciona un resumen antes de que el código se pueda implementar en el entorno del escenario |
| 5. Artefactos con versión almacenados | Los artefactos de lanzamiento se almacenan para su uso posterior en los pasos de implementación. |
| 6. Implementación automática de artefactos en la fase de AEM de AMS | El artefacto de liberación se implementa en el entorno del escenario. |
| 7. Activar pruebas automatizadas | [!UICONTROL Cloud Manager] ejecuta las pruebas de rendimiento y seguridad del artefacto. |
| 8. Implementación del activador de producción | Una vez finalizadas las pruebas automatizadas, [!UICONTROL Cloud Manager] inicio la implementación en producción. |
| 9. [!UICONTROL Cloud Manager] obtiene artefactos para implementar | [!UICONTROL Cloud Manager] extrae los artefactos de liberación almacenados. |
| 10. Depurar artefactos a la producción | Los artefactos de la versión se implementan en el entorno de producción. |

### Cómo configurar una canalización CI/CD {#how-to-setup-a-ci-cd-pipeline}

Para obtener más información sobre la configuración de canalización, consulte [configuración de canalización](configuring-pipeline.md).

## Gates de calidad {#quality-gates}

La canalización CI/CD proporciona puertas de calidad, o criterios de aceptación, que deben cumplirse antes de que el código pueda moverse del entorno del escenario al entorno de implementación. Hay tres puertas en el oleoducto:

* Calidad del código
* Prueba de rendimiento
* Pruebas de seguridad

Para cada una de estas puertas, hay tres niveles de problemas identificados:

* **Críticos** : problemas identificados por la puerta que causan un fallo inmediato en la tubería.
* **Importante** : Problemas identificados por la puerta que hacen que la tubería entre en estado de pausa. Un administrador de implementación, un jefe de proyecto o un propietario de empresa pueden anular los problemas, en cuyo caso la canalización continúa, o pueden aceptar los problemas, en cuyo caso la canalización se detiene con un error.
* **Información** : los problemas identificados por la puerta que se proporcionan exclusivamente con fines informativos y no tienen impacto en la ejecución de la tubería.

A continuación se muestra un ejemplo de un análisis de código con problemas identificados para el código:

![](assets/quality-gate-failed.png)

### Cómo configurar las puertas {#how-to-setup-gates}

Consulte **[Configuración de puertas](configuring-pipeline.md)** para obtener más información sobre la configuración de las puertas de código, calidad y rendimiento.
