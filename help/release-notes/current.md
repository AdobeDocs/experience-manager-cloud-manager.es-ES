---
title: Notas de la versión 2024.7.0
description: Estas son las notas de la versión 2024.7.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: d536cd96d135e48039f94fd01142a63305b6eeae
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 61%

---


# Notas de la versión 2024.7.0 de Cloud Manager {#release-notes}

Esta página documenta las notas de la versión 2024.7.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Para las notas de la última versión de Cloud Manager en AEM as a Cloud Service, consulte [Cloud Manager en las notas de la versión actuales de AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=es)

## Fecha de la versión {#release-date}

La fecha de la versión 2024.7.0 de [!UICONTROL Cloud Manager] es el 18 de julio de 2024. La próxima versión está planificada para el 8 de agosto de 2024.

## Novedades {#what-is-new}

* La [canalización de producción](/help/using/production-pipelines.md#adding-production-pipeline) y la [canalización que no es de producción](/help/using/non-production-pipelines.md#adding-non-production-pipeline) tienen el déclencheur **Cambios en Git** para iniciar la canalización en una confirmación y ya están disponibles para [repositorios privados.](/help/managing-code/private-repositories.md)
* Una canalización de preproducción solo se puede activar manualmente y no se puede configurar como **Cambios en Git**.
* En el caso de las canalizaciones solo de producción, la lista de ejecuciones promovibles incluye aquellas que tienen una versión del artefacto mayor que la versión del artefacto implementada en el entorno de producción.

## Programa para primeros usuarios {#early-adoption}

Participe en nuestro programa para clientes pioneros y tenga la oportunidad de probar algunas de las próximas funciones

### Canalizaciones solo de fase y de producción {#staging-production-only-pipelines}

Se ha introducido la compatibilidad con las [canalizaciones solo de ensayo y solo de producción](/help/using/stage-prod-only.md), lo que le permite dividir canalizaciones de implementación de la producción de pila completa en implementaciones más pequeñas y especializadas.

Si está interesado en probar esta nueva función y en compartir sus comentarios, envíe un correo electrónico a `Grp-cloudmanager_splitpipelines@adobe.com` desde la dirección de correo electrónico asociada a su Adobe ID.
