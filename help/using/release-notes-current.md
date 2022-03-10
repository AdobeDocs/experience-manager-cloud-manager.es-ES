---
title: Notas de la versión 2022.3.0
description: Estas son las notas de la versión de Cloud Manager 2022.3.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 7611667d8c617d501f9b69cbc7c854c195a5ebbe
workflow-type: tm+mt
source-wordcount: '210'
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

* Las solicitudes HTTP salientes de las pruebas de recursos ahora provienen de un intervalo IP fijo.


## Corrección de errores {#bug-fixes}

* La variable **Omitir cambios del equilibrador de carga** no se pudo desactivar.
*El **Omitir cambios del equilibrador de carga** no se mostraba en la implementación de desarrolladores de AMS **Editar flujo de trabajo de canalización**.
* Un subconjunto de repositorios Git creados manualmente tenía un valor de nombre incorrecto que impedía que la función de reutilización de artefactos de compilación fuera efectiva. Los nombres de esos repositorios se han cambiado y los usuarios verán el nombre corregido en la interfaz de usuario/API de Cloud Manager.
* Los artefactos de compilación de las canalizaciones que no son de producción se reutilizaron incorrectamente en las canalizaciones de pila completas de producción.
* Al añadir o editar una canalización de calidad de código, ya no se muestran las opciones para gestionar errores de métricas.
* Algunas configuraciones de variables de canalización inesperadas podrían causar en el paso de compilación.
