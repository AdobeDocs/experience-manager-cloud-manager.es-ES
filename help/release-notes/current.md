---
title: Notas de la versión 2024.5.0
description: Estas son las notas de la versión 2024.5.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 395fe2a42fc2d6413dff38c9e4620c62039f87e2
workflow-type: ht
source-wordcount: '287'
ht-degree: 100%

---


# Notas de la versión 2024.5.0 de Cloud Manager {#release-notes}

Esta página documenta las notas de la versión 2024.5.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Para las notas de la última versión de Cloud Manager en AEM as a Cloud Service, consulte [Cloud Manager en las notas de la versión actuales de AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=es)

## Fecha de la versión {#release-date}

La fecha de lanzamiento de la versión 2024.5.0 de [!UICONTROL Cloud Manager] es el 9 de mayo de 2024. La próxima versión está planificada para el 6 de junio de 2024.

## Novedades {#what-is-new}

* El paso Auditoría de contenido ahora se omite cuando se ejecuta una canalización en [modo de emergencia.](/help/using/code-deployment.md#emergency-pipeline)

## Programa para primeros usuarios {#early-adoption}

Participe en nuestro programa para clientes pioneros y tenga la oportunidad de probar algunas de las próximas funciones

### Canalizaciones solo de fase y de producción {#staging-production-only-pipelines}

Se ha introducido la compatibilidad con las [canalizaciones solo de ensayo y solo de producción](/help/using/stage-prod-only.md), lo que le permite dividir canalizaciones de implementación de la producción de pila completa en implementaciones más pequeñas y especializadas.

Si está interesado en probar esta nueva función y en compartir sus comentarios, envíe un correo electrónico a `Grp-cloudmanager_splitpipelines@adobe.com` desde la dirección de correo electrónico asociada a su Adobe ID.

### Traer su propio GitHub {#byo-github}

Si utiliza GitHub para administrar sus repositorios, [ahora puede validar códigos directamente dentro de sus repositorios de GitHub a través de Cloud Manager.](/help/managing-code/byo-github.md)Esta integración elimina la necesidad de sincronizar el código de forma coherente con el repositorio de Adobe y le permite comprobar las solicitudes de extracción antes de combinarlas en las ramas principales. Esta funcionalidad es exclusiva de GitHub público. La compatibilidad con GitHub autoalojado no está disponible.

Si está interesado en probar esta nueva funcionalidad y en compartir sus comentarios, envíe un correo electrónico a `Grp-CloudManager_BYOG@adobe.com` desde su dirección de correo electrónico asociada a su Adobe ID.

## Correcciones de errores {#bug-fixes}

* Se ha corregido un error por el que Cloud Manager reutilizaba artefactos con el hash de confirmación incorrecto.
