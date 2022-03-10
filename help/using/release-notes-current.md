---
title: Notas de la versión 2022.3.0
description: Estas son las notas de la versión de Cloud Manager 2022.3.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 6e98f9d2fcd69799bad86d1e247212b26273bd0b
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 4%

---


# Notas de la versión para Cloud Manager versión 2022.3.0 {#release-notes}

Esta página documenta las notas de la versión de [!UICONTROL Cloud Manager] versión 2022.3.0.

>[!NOTE]
>
>Para las notas de la última versión de Cloud Manager en AEM as a Cloud Service, consulte [Cloud Manager en las notas de la versión actuales de AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Fecha de la versión {#release-date}

La fecha de la versión de [!UICONTROL Cloud Manager] la versión 2022.3.0 es 10 de marzo de 2022. La próxima versión está prevista para el 7 de abril de 2022.

## Novedades {#what-is-new}

* [La variable `reliability_rating` métrica crítica](understand-your-test-results.md) se ha desactivado.
* Ahora un usuario puede ordenar las columnas de la **Canalizaciones** en Cloud Manager.

## Corrección de errores {#bug-fixes}

* [La variable **Omitir cambios del equilibrador de carga** option](configuring-production-pipelines.md#adding-production-pipeline) ahora se puede deshabilitar correctamente.
* [La variable **Omitir cambios del equilibrador de carga** option](configuring-production-pipelines.md#adding-production-pipeline) ahora se muestra para el flujo de trabajo de edición de la canalización de implementación.
* Un subconjunto de repositorios git creados manualmente tenía valores de nombre incorrectos que afectaban a [la función de reutilización de artefactos de compilación.](setting-up-project.md#build-artifact-reuse) Los nombres de esos repositorios se han cambiado y los usuarios verán el nombre corregido en la interfaz de usuario/API de Cloud Manager.
* [Al añadir o editar una canalización de calidad de código,](configuring-non-production-pipelines.md) ya no se muestran las opciones para gestionar errores de métricas.
* Las configuraciones de variables de canalización inesperadas ya no causan errores en el paso de compilación.
