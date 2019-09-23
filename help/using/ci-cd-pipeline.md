---
title: Canalización CI/CD
seo-title: Canalización CI/CD
description: nulo
seo-description: Siga esta sección para obtener información sobre el canalizador de CI/CD, que gestiona las implementaciones en el escenario y la producción en Cloud Manager.
uuid: 763ddb24-05cd-463f-8d72-a2e69bbe6b7e
topic-tags: introducción
discoiquuid: 1cdb76eb-1a91-4689-8579-0fa9fccc0592
translation-type: tm+mt
source-git-commit: 949d3cf0239a02875ba4ad1888e081f104dec2e2

---


# Canalización CI/CD {#ci-cd-pipeline}

## Información general de canalización {#pipeline-overview}

[!UICONTROL Cloud Manager] incluye un marco de integración continua (CI) y entrega continua (CD) que permite a los equipos de implementación probar y entregar rápidamente código nuevo o actualizado. Por ejemplo, los equipos de implementación pueden configurar, configurar e iniciar una canalización automatizada de CD/CI que aprovecha las prácticas recomendadas de codificación de Adobe para realizar un análisis exhaustivo del código y garantizar la máxima calidad del código.

La canalización CI/CD también automatiza los procesos de prueba de unidades y performance para aumentar la eficiencia de la implementación e identificar de manera proactiva los problemas críticos que son costosos de solucionar después de la implementación. Los equipos de implementación pueden acceder a un informe de rendimiento de código completo para obtener visibilidad sobre el impacto potencial en los KPI y las validaciones de seguridad críticas si el código se implementa en la producción.

## Proceso de canalización {#pipeline-process}

El siguiente diagrama ilustra qué sucede una vez que se activa una versión en [!UICONTROL Cloud Manager]. La tabla adjunta explica cada paso del flujo de trabajo.

![](assets/screen_shot_2018-05-30at82457pm.png)

En la tabla siguiente se detalla lo que sucede durante cada paso del proceso:

| Etapa de proceso de canalización | ¿Qué está pasando? |
|---|---|
| 1. Iniciar una versión | Un administrador de implementación activa una versión manualmente, con una confirmación Git o según una programación recurrente. |
| 2. Crear etiqueta de lanzamiento | [!UICONTROL Cloud Manager] crea una etiqueta Git para marcar la versión con un número de versión generado automáticamente. Por ejemplo: 2018.531.245527.0000001222 |
| 3. Creado como versión con versión generada automáticamente | [!UICONTROL Cloud Manager] crea la aplicación con el número de versión recién asignado. |
| 4. Evaluar la calidad del código | [!UICONTROL Cloud Manager] analiza el código fuente y proporciona un resumen antes de que el código se pueda implementar en el entorno de escenario |
| 5. Artefactos con versión almacenados | Los artefactos de lanzamiento se almacenan para su uso posterior en los pasos de implementación. |
| 6. Implementación automática de artefactos en AMS AEM Stage | El artefacto de lanzamiento se implementa en el entorno de ensayo. |
| 7. Activar pruebas automatizadas | [!UICONTROL Cloud Manager] ejecuta las pruebas de rendimiento y seguridad del artefacto. |
| 8. Implementación del activador de producción | Una vez completadas las pruebas automatizadas, [!UICONTROL Cloud Manager] comienza la implementación en producción. |
| 9. [!UICONTROL Cloud Manager] consigue la implementación de artefactos | [!UICONTROL Cloud Manager] extrae los artefactos de liberación almacenados. |
| 10. Propagar artefactos a la producción | Los artefactos de la versión se implementan en el entorno de producción. |

### Cómo configurar una canalización CI/CD {#how-to-setup-a-ci-cd-pipeline}

Para obtener más información sobre la configuración de canalización, consulte [Configuración de canalización](configuring-pipeline.md).

## Gates de calidad {#quality-gates}

La canalización CI/CD proporciona puertas de calidad, o criterios de aceptación, que deben cumplirse para que el código pueda moverse del entorno de etapa al entorno de implementación. Hay tres puertas en el oleoducto:

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

Consulte **[Configuración de puertas](configuring-pipeline.md)** para obtener más información sobre la configuración del código, la calidad y las puertas de rendimiento.
