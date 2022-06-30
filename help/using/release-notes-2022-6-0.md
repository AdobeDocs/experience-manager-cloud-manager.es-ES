---
title: Notas de la versión 2022.6.0
description: Estas son las notas de la versión de Cloud Manager 2022.6.0.
feature: Release Information
source-git-commit: f202b245f35bcffa56b43f26a13b97d42fdb474e
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 3%

---


# Notas de la versión para Cloud Manager versión 2022.6.0 {#release-notes}

Esta página documenta las notas de la versión de [!UICONTROL Cloud Manager] versión 2022.6.0.

>[!NOTE]
>
>Para las notas de la última versión de Cloud Manager en AEM as a Cloud Service, consulte [Cloud Manager en las notas de la versión actuales de AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Fecha de la versión {#release-date}

La fecha de la versión de [!UICONTROL Cloud Manager] la versión 2022.6.0 es 9 de junio de 2022. La próxima versión está prevista para el 30 de junio de 2022.

## Novedades {#what-is-new}

* Una nueva tarjeta de bienvenida en la página de aterrizaje de Cloud Manager permite a los usuarios acceder rápidamente a los tutoriales de incorporación y a las métricas de progreso relacionadas con el inquilino.
   * Esta función se implementará por fases en la semana siguiente a la versión 2022.06.0.
* [Ahora, los artefactos de compilación se pueden reutilizar](/help/using/setting-up-project.md#build-artifact-reuse) al usar la duplicación de Git.

## Cambios en la API {#api-changes}

* La variable [`List Programs`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getPrograms) La API de se ha desaprobado y [`List Programs for Tenant`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getProgramsForTenant) en su lugar.
   * `List Programs` sigue funcionando, pero su uso generará mensajes de advertencia en los registros.
   * Dejará de ser compatible a los tres meses.
