---
title: Notas de la versión 2022.3.0
description: These are the release notes for Cloud Manager release 2022.3.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 79b2729814af483844d095ed8d6db6cead2ceaf7
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 3%

---


# Notas de la versión para Cloud Manager versión 2022.3.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2022.3.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service&#39;s current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Fecha de la versión {#release-date}

La fecha de la versión de [!UICONTROL Cloud Manager] la versión 2022.3.0 es 10 de marzo de 2022. The next release is planned for 7 April 2022.

## Novedades {#what-is-new}

* (Solo Cloud Service) El acceso al registro de entorno de AEM se puede realizar con la función de desarrollador.
* (AMS): Las solicitudes HTTP salientes de las pruebas de recursos ahora provienen de un intervalo IP fijo.


## Corrección de errores {#bug-fixes}

* (Solo AMS) La variable **Omitir cambios del equilibrador de carga** no se pudo desactivar.
* (AMS) El **Omitir cambios del equilibrador de carga** no se mostraba en la implementación de desarrolladores de AMS **Editar flujo de trabajo de canalización**.
* A subset of git repositories created manually had an incorrect name value which prevented the build artifact reuse feature from being effective. Los nombres de esos repositorios se han cambiado y los usuarios verán el nombre corregido en la interfaz de usuario/API de Cloud Manager.
* Los artefactos de compilación de las canalizaciones que no son de producción se reutilizaron incorrectamente en las canalizaciones de pila completas de producción.
* Al añadir o editar una canalización de calidad de código, ya no se muestran las opciones para gestionar errores de métricas.
* Algunas configuraciones de variables de canalización inesperadas podrían causar en el paso de compilación.
