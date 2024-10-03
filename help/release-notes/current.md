---
title: Notas de la versión 2024.10.0 de Cloud Manager
description: Estas son las notas de la versión 2024.10.0 de Cloud Manager.
feature: Release Information
source-git-commit: 94d5f3487408f9d8908bb15221c48ef768390527
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 26%

---

# Notas de la versión 2024.10.0 de Cloud Manager {#release-notes}

Esta página documenta las notas de la versión 2024.10.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Para las notas de la última versión de Cloud Manager en AEM as a Cloud Service, consulte [las notas de la versión actuales de Cloud Manager en AEM as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).



## Fecha de lanzamiento {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

La fecha de la versión de [!UICONTROL Cloud Manager] 2024.10.0 es el 3 de octubre de 2024.

La próxima versión está planificada para el viernes, 14 de noviembre de 2024.



## Novedades {#what-is-new}

* <!-- BOTH CS & AMS --> AEM La versión del tipo de archivo utilizada en Cloud Manager ahora se actualiza a la versión 26. Ver [https://github.com/adobe/aem-project-archetype/releases](https://github.com/adobe/aem-project-archetype/releases)
<!-- (CMGR-59817) -->



## Programa para primeros usuarios {#early-adoption}

Forme parte del programa de adopción anticipada de Cloud Manager y tenga la oportunidad de probar las próximas funciones.

### Traiga su propio Git: ahora con soporte para GitLab y Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

La función **Traer tu propio Git** se ha ampliado para incluir compatibilidad con repositorios externos como GitLab y Bitbucket. Esta nueva compatibilidad se suma a la compatibilidad ya existente con repositorios de GitHub privados y empresariales. Al añadir estos nuevos repositorios, también puede vincularlos directamente a sus canalizaciones. Puede alojar estos repositorios en plataformas de nube públicas o dentro de su infraestructura o nube privada. Esta integración también elimina la necesidad de una sincronización constante del código con el repositorio de Adobe y proporciona la capacidad de validar las solicitudes de extracción antes de combinarlas en una rama principal.

Consulte [Agregar repositorios externos en Cloud Manager](/help/managing-code/external-repositories.md).

![Cuadro de diálogo Agregar repositorio](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Actualmente, las comprobaciones de calidad del código de las solicitudes de extracción listas para usar son exclusivas de los repositorios alojados en GitHub, pero se está trabajando en una actualización para ampliar esta funcionalidad a otros proveedores de Git.

Si está interesado en probar esta nueva característica y compartir sus comentarios, envíe un mensaje de correo electrónico a [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) desde su dirección de correo electrónico asociada a su Adobe ID. Asegúrese de incluir qué plataforma Git desea utilizar y si se encuentra en una estructura de repositorio privada/pública o empresarial.

### Canalizaciones solo de fase y de producción {#staging-production-only-pipelines}

El Adobe anuncia la introducción de la compatibilidad con [canalizaciones solo de ensayo y de producción](/help/using/stage-prod-only.md). Esta nueva función le permite dividir las canalizaciones de implementación de producción de pila completa en implementaciones más pequeñas y especializadas.

Si desea probar esta función y proporcionar comentarios, envíe un mensaje de correo electrónico a [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com) desde la dirección de correo electrónico asociada a su Adobe ID.

<!-- ## Bug fixes

* text
-->

## Problemas conocidos {#known-issues}

{{content-copy-known-issues}}
