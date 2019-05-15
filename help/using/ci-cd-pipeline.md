---
title: Pipeline CI/CD
seo-title: Pipeline CI/CD
description: nulo
seo-description: Siga esta sección para obtener información sobre la canalización CI/CD, que gestiona las implementaciones en fases y producción en Cloud Manager.
uuid: 763 ddb 24-05 cd -463 f -8 d 72-a 2 e 69 bbe 6 b 7 e
topic-tags: introducción
discoiquuid: 1 cdb 76 eb -1 a 91-4689-8579-0 fa 9 fccc 0552
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Pipeline CI/CD {#ci-cd-pipeline}

## Información general de Pipeline {#pipeline-overview}

[!UICONTROL Cloud Manager] incluye un marco de integración continua (CI) y de envío continuo (CD) que permite a los equipos de implementación probar y entregar rápidamente código nuevo o actualizado. Por ejemplo, los equipos de implementación pueden configurar, configurar e iniciar una canalización automatizada de CI/CD que aproveche las prácticas recomendadas de codificación de Adobe para realizar un análisis de código exhaustivo y garantizar la mayor calidad de código.

La canalización CI/CD automatiza los procesos de prueba de rendimiento y unidad para aumentar la eficacia de la implementación e identificar de forma proactiva los problemas críticos que resultan costosos de corregir después de la implementación. Los equipos de implementación pueden acceder a un informe exhaustivo de rendimiento de código para obtener información sobre el impacto potencial en los KPI y las validaciones de seguridad críticas si el código se implementa en la producción.

## Proceso de pipeline {#pipeline-process}

The following diagram illustrates what happens once a release is triggered in [!UICONTROL Cloud Manager]. La tabla adjunta explica cada paso del flujo de trabajo.

![](assets/screen_shot_2018-05-30at82457pm.png)

La siguiente tabla detalla lo que está sucediendo durante cada paso del proceso:

| Etapa del proceso de Pipeline | ¿Qué está sucediendo? |
|---|---|
| 1. Iniciar una versión | Un administrador de implementación desencadena una versión manualmente, con una implementación de Git o basada en un programa recurrente. |
| 2. Crear versión, etiqueta | [!UICONTROL Cloud Manager] crea una etiqueta Git para marcar la versión utilizando un número de versión generado automáticamente. Por ejemplo: 2018.531.245527.0000001222 |
| 3. Creado como versión con versión generada automáticamente | [!UICONTROL Cloud Manager] crea la aplicación con el número de versión recién asignado. |
| 4. Evaluar calidad del código | [!UICONTROL Cloud Manager] escanea el código fuente y proporciona un resumen antes de que el código se pueda implementar en el entorno de etapa |
| 5. Artefactos de versiones almacenados | Los artefactos de lanzamiento se almacenan para su uso posterior en los pasos de implementación. |
| 6. Implementación automática de artefactos en la etapa de AEM de AMS | El artefacto de lanzamiento se implementa en el entorno de etapa. |
| 7. Activar pruebas automatizadas | [!UICONTROL Cloud Manager] ejecuta las pruebas de rendimiento y seguridad en el artefacto. |
| 8. Implementación del activador de producción | Una vez completadas las pruebas [!UICONTROL Cloud Manager] automatizadas, se inicia la implementación en producción. |
| 9. [!UICONTROL Cloud Manager] Obtiene artefactos para implementar | [!UICONTROL Cloud Manager] extrae los artefactos de lanzamiento almacenados. |
| 10. Desextender artefactos a producción | Los artefactos de lanzamiento se implementan en el entorno Producción. |

### Cómo configurar un flujo de CI/CD {#how-to-setup-a-ci-cd-pipeline}

Para obtener más información sobre la configuración del canal, consulte [la configuración de canalización](configuring-pipeline.md).

## Puertas de calidad {#quality-gates}

El canal de CI/CD proporciona puertas de calidad o criterios de aceptación que deben cumplirse antes de que el código se pueda mover del entorno de etapa al entorno de implementación. Hay tres puertas en el canal:

* Calidad del código
* Prueba de rendimiento
* Prueba de seguridad

Para cada una de estas puertas, hay tres niveles de problemas identificados:

* **Críticas** : problemas identificados por la puerta de enlace que provocan un fallo inmediato en la canalización.
* **Importante** : los problemas identificados por la puerta de enlace que hacen que el canal introduzca un estado pausado. Un administrador de implementación, un administrador de proyectos o un propietario comercial pueden anular los problemas, en cuyo caso el canalizador continúa o puede aceptar los problemas, en cuyo caso la canalización se detiene con un error.
* **Información** : problemas identificados por la compuerta que se proporcionan exclusivamente con fines informativos y que no tienen impacto en la ejecución del canal.

A continuación se muestra un ejemplo de un código de barras con problemas identificados para el código:

![](assets/quality-gate-failed.png)

### Cómo configurar las puertas {#how-to-setup-gates}

Consulte **[Configuración de puertas](configuring-pipeline.md)** para obtener más información sobre la configuración de las puertas de código, calidad y rendimiento.
