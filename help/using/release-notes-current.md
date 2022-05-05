---
title: Notas de la versión 2022.5.0
description: Estas son las notas de la versión de Cloud Manager 2022.5.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 84cc4352488002ad40102ea2c507af652d9012a1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 29%

---


# Notas de la versión para la versión 2022.5.0 de Cloud Manager {#release-notes}

Esta página documenta las notas de la versión de [!UICONTROL Cloud Manager] versión 2022.5.0.

>[!NOTE]
>
>Para las notas de la última versión de Cloud Manager en AEM as a Cloud Service, consulte [Cloud Manager en las notas de la versión actuales de AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Fecha de la versión {#release-date}

La fecha de la versión de [!UICONTROL Cloud Manager] la versión 2022.5.0 es el 5 de mayo de 2022. La próxima versión está planificada para el 9 de junio de 2022.

## Novedades {#what-is-new}

Las solicitudes HTTP salientes de las pruebas de recursos ahora provienen de un intervalo IP fijo.

## Correcciones de errores {#bug-fixes}

* La opción de cambios &quot;Saltar equilibrador de carga&quot; no se ha podido desactivar.
* La opción Omitir cambios del equilibrador de carga no se mostraba en el flujo de trabajo de la canalización de edición de Desplegar desarrollador de AMS.
* Un subconjunto de repositorios GIT creados manualmente tenía un valor de nombre incorrecto que impedía que la función de reutilización de artefactos de compilación fuera efectiva. Los nombres de esos repositorios se han cambiado y los usuarios verán el nombre corregido en la IU/API de Cloud Manager.
* Los artefactos de compilación de las canalizaciones que no son de producción se reutilizaron de forma incorrecta en las canalizaciones full stack de producción.
* Al añadir o editar una canalización de calidad de código, ya no se muestran las opciones para gestionar errores de métricas.
* Algunas configuraciones de variables de canalización inesperadas podrían causar errores en el paso de compilación.
