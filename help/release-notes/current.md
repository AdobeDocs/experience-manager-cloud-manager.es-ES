---
title: Notas de la versión de Cloud Manager 2024.8.0
description: Obtenga información acerca de las notas de la versión para Cloud Manager 2024.8.0.
feature: Release Information
source-git-commit: dd764bb17127ba0a1e88e85592329cc9ddff42e3
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 3%

---


# Notas de la versión de Cloud Manager 2024.8.0 {#release-notes}

Esta página documenta las notas de la versión de [!UICONTROL Cloud Manager] 2024.8.0.

>[!NOTE]
>
>Para ver las últimas notas de la versión de Cloud Manager en AEM as a Cloud Service, consulte [Cloud Manager en las notas de la versión actuales de AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Fecha de lanzamiento {#release-date}

La fecha de la versión de [!UICONTROL Cloud Manager] 2024.8.0 es el 14 de agosto de 2024. La próxima versión está planificada para el 14 de septiembre de 2024.

## Novedades {#what-is-new}

* Para canalizaciones solo de fase y de producción (disponibles como parte del [programa de adopción anticipada](#staging-production-only-pipelines)), ahora puede ejecutarlas en [modo de emergencia](/help/using/stage-prod-only.md#emergency-mode), omitiendo la prueba de fase.

## Programa de adopción temprana {#early-adoption}

Forme parte del programa de adopción anticipada de Adobe y tenga la oportunidad de probar algunas de las próximas funciones.

### Canalizaciones solo de ensayo y de producción {#staging-production-only-pipelines}

El Adobe se complace en anunciar la presentación de la compatibilidad con [canalizaciones solo de ensayo y de producción](/help/using/stage-prod-only.md). Esta nueva función le permite dividir las canalizaciones de implementación de producción de pila completa en implementaciones más pequeñas y especializadas.

Si desea probar esta función y proporcionar comentarios, envíe un mensaje de correo electrónico a `Grp-cloudmanager_splitpipelines@adobe.com` con la dirección de correo electrónico asociada a su Adobe ID.

## Corrección de errores

* Se ha corregido un problema poco habitual en el que los pasos de la canalización se ejecutaban después de eliminarse.
* Volver a ejecutar la canalización ahora funciona en el primer intento, lo que corrige un problema poco frecuente en el que se tenía que iniciar una nueva ejecución varias veces.
* Los pasos de implementación programados para canalizaciones de pila completa ahora respetan la fecha programada seleccionada y no revierten a **Ahora**.
* Los estados de las tareas de copia de contenido con error ahora se reflejan correctamente y ya no muestran incorrectamente un estado `In Progress` en circunstancias excepcionales.

## Problemas conocidos {#known-issues}

{{content-copy-known-issues}}
