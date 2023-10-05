---
title: Notas de la versión 2023.10.0
description: Estas son las notas de la versión 2023.10.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: a5a304541409bc1775090eef2a669e1e0bcf005e
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 58%

---


# Notas de la versión 2023.10.0 de Cloud Manager {#release-notes}

Esta página documenta las notas de la versión 2023.10.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Para las notas de la última versión de Cloud Manager en AEM as a Cloud Service, consulte [Cloud Manager en las notas de la versión actuales de AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=es)

## Fecha de la versión {#release-date}

La fecha de lanzamiento de la versión 2023.10.0 de [!UICONTROL Cloud Manager] es el 5 de octubre de 2023. El próximo lanzamiento está planificado para el 2 de noviembre de 2023.

## Novedades {#what-is-new}

* El **Administrador de implementación** la función puede [AEM configure un conjunto de rutas de contenido que se invalidarán o vaciarán de la caché de Dispatcher de la red de distribución de contenido cuando se ejecute una canalización que no sea de producción.](/help/using/non-production-pipelines.md)
   * Estas acciones de caché se ejecutarán como parte del paso de canalización de implementación, justo después de implementar cualquier paquete de contenido.
   * Esta configuración utiliza el comportamiento estándar de AEM Dispatcher.
* Con la versión de octubre de 2023 de Cloud Manager, las versiones de Java se actualizan mediante una implementación gradual.
   * Las versiones de Java se actualizan al Oracle JDK 8u371 y al Oracle JDK 11.0.20.
   * [Consulte el aviso de OpenJDK](https://openjdk.org/groups/vulnerability/advisories/) para obtener más información sobre la seguridad y las correcciones de errores en estas actualizaciones de JDK.
