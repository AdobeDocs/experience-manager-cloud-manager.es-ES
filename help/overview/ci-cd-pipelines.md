---
title: Canalizaciones de CI/CD
description: Obtenga información acerca de las canalizaciones de CI/CD y cómo administran las implementaciones en entornos de ensayo y producción en Cloud Manager.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '562'
ht-degree: 100%

---


# Canalizaciones de CI/CD {#ci-cd-pipeline}

Obtenga información acerca de las canalizaciones de CI/CD y cómo administran las implementaciones en entornos de ensayo y producción en Cloud Manager.

## Información general {#overview}

[!UICONTROL Cloud Manager] incluye un marco de trabajo de integración continua/envío continuo (CI/CD), que permite a los equipos de implementación probar y entregar rápidamente código nuevo o actualizado. Los equipos de implementación pueden configurar e iniciar una canalización automatizada de CD/CI. Esta canalización sigue las prácticas recomendadas de codificación de Adobe para realizar un análisis exhaustivo del código y garantizar la máxima calidad.

La canalización de CI/CD también automatiza los procesos de prueba de unidades y de rendimiento para aumentar la eficiencia e identificar proactivamente los problemas críticos que son costosos de solucionar tras la implementación. Los equipos de implementación pueden acceder a un informe completo de rendimiento del código para obtener visibilidad sobre el impacto potencial en los indicadores clave de rendimiento (KPI) y las validaciones de seguridad críticas si el código se implementa en producción.

## Acerca del proceso de canalización {#pipeline-process}

Este diagrama ilustra lo que sucede una vez que se activa una versión en [!UICONTROL Cloud Manager] mediante una canalización.

![El proceso de canalización](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Paso de canalización | Descripción |
| --- | --- |
| 1. Iniciar una versión | Un administrador de implementación activa una versión manualmente, con una confirmación de Git o en función de una programación recurrente. |
| 2. Crear una etiqueta de versión | [!UICONTROL Cloud Manager] crea una etiqueta de Git para marcar la versión con un número de versión generado automáticamente, por ejemplo, `2018.531.245527.0000001222`. |
| 3. Compilar como versión de forma autogenerada | [!UICONTROL Cloud Manager] compila la aplicación con el número de versión recién asignado. |
| 4. Evaluar la calidad del código | [!UICONTROL Cloud Manager] analiza el código fuente y proporciona un resumen antes de que se pueda implementar en el entorno de ensayo. |
| 5. Artefactos con versiones almacenados | Los artefactos de la versión se almacenan para su uso posterior en los pasos de implementación. |
| 6. Implementar automáticamente artefactos en el ensayo de AEM de AMS | El artefacto de la versión se implementa en el entorno de ensayo. |
| 7. Activar pruebas automatizadas | [!UICONTROL Cloud Manager] ejecuta pruebas de rendimiento y seguridad en el artefacto. |
| 8. Implementar el activador de producción | Una vez completadas las pruebas automatizadas, [!UICONTROL Cloud Manager] inicia la implementación en producción. |
| 9. [!UICONTROL Cloud Manager] obtiene artefactos para implementar | [!UICONTROL Cloud Manager] extrae los artefactos de la versión almacenados. |
| 10. Implementar artefactos en producción | Los artefactos de la versión se implementan en el entorno de producción. |

### Configuración de una canalización de CI/CD {#how-to-setup-a-ci-cd-pipeline}

Para obtener más información acerca de la configuración de la canalización, consulte los documentos [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) y [Configuración de canalizaciones que no son de producción](/help/using/non-production-pipelines.md).

## Puertas de calidad {#quality-gates}

La canalización de CI/CD proporciona puertas de calidad o criterios de aceptación que deben cumplirse para que el código pueda moverse del entorno de ensayo al de implementación. Hay tres puertas en la canalización:

* Calidad de código
* Pruebas de rendimiento
* Pruebas de seguridad

Para cada una de estas puertas, hay tres niveles de problemas que se pueden identificar:

* **Crítico**: los problemas críticos identificados por la puerta causan un fallo inmediato de la canalización.
* **Importante**: los problemas importantes identificados por la puerta hacen que la canalización entre en un estado de pausa. Un administrador de implementación, un administrador de proyectos o un propietario empresarial pueden anular los problemas, lo que permite que la canalización continúe. De forma alternativa, pueden aceptar los problemas, lo cual haría que la canalización se detenga con un error. 
* **Información**: los problemas de información identificados por la puerta se proporcionan exclusivamente con fines informativos y no tienen impacto en la ejecución de la canalización.

Este es un ejemplo de análisis de código con problemas identificados.

![Ejemplo de análisis de código](/help/assets/quality-gate-failed.png)

### Cómo configurar puertas {#how-to-setup-gates}

Consulte el documento [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) para obtener más información sobre la configuración de las puertas de código, calidad y rendimiento.
