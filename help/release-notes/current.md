---
title: Notas de la versión 2024.7.0
description: Obtenga información acerca de las notas de la versión de Cloud Manager 2024.7.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 4%

---


# Notas de la versión de Cloud Manager 2024.7.0 {#release-notes}

Esta página documenta las notas de la versión de [!UICONTROL Cloud Manager] 2024.7.0.

>[!NOTE]
>
>Para ver las últimas notas de la versión de Cloud Manager en AEM as a Cloud Service, consulte [Cloud Manager en las notas de la versión actuales de AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Fecha de lanzamiento {#release-date}

La fecha de la versión de [!UICONTROL Cloud Manager] 2024.7.0 es el 18 de julio de 2024. La próxima versión está planificada para el 13 de agosto de 2024.

## Novedades {#what-is-new}

* La [canalización de producción](/help/using/production-pipelines.md#adding-production-pipeline) y la [canalización que no es de producción](/help/using/non-production-pipelines.md#adding-non-production-pipeline) tienen el déclencheur **Cambios en Git** para iniciar la canalización en una confirmación y ya están disponibles para [repositorios privados](/help/managing-code/private-repositories.md).
* Una canalización previa a la producción solo se puede activar manualmente y no se puede configurar como **Cambios en Git**.
* En el caso de las canalizaciones solo de producción, la lista de ejecuciones promovibles incluye las ejecuciones con una versión de artefacto mayor que la versión de artefacto implementada en el entorno de producción.
* AEM [El tipo de archivo del proyecto de](https://experienceleague.adobe.com/es/docs/experience-manager-core-components/using/developing/archetype/overview) se ha actualizado a la [versión 49](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49).

## Programa de adopción temprana {#early-adoption}

Forme parte del programa de adopción anticipada de Cloud Manager y tenga la oportunidad de probar algunas de las próximas funciones

### Canalizaciones solo de ensayo y solo de producción {#staging-production-only-pipelines}

Ahora se presenta compatibilidad con [canalizaciones solo de ensayo y de producción](/help/using/stage-prod-only.md), lo que le permite dividir canalizaciones de implementación de producción de pila completa en implementaciones más pequeñas y especializadas.

Si está interesado en probar esta nueva característica y compartir sus comentarios, envíe un mensaje de correo electrónico a `Grp-cloudmanager_splitpipelines@adobe.com` desde su dirección de correo electrónico asociada a su Adobe ID.
