---
title: Notas de la versión 2024.12.0 de Cloud Manager
description: Obtenga información sobre la versión de Cloud Manager 2024.11.0 en Adobe Managed Services.
feature: Release Information
exl-id: 811567af-66c9-4c1f-ae9e-60603b70ef80
source-git-commit: e266a4192e2a897f142a6c83ae5766483946320d
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 100%

---

# Notas de la versión de Cloud Manager 2024.12.0 en Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Obtenga información sobre la versión de [!UICONTROL Cloud Manager] 2024.12.0 en Adobe Managed Services.

>[!NOTE]
>
>Consulte las [notas de la versión actuales de Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/release-notes/home).

## Fechas de lanzamiento {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

La fecha de lanzamiento de la versión 2024.12.0 de [!UICONTROL Cloud Manager] es el 5 de diciembre de 2024. 

La próxima versión planificada es el viernes, 23 de enero de 2025.

<!-- ## What's new {#what-is-new} -->

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

## Programa para primeros usuarios {#early-adoption}

Participe en nuestro programa para primeros usuarios de Cloud Manager y tenga la oportunidad de probar algunas de las próximas funciones.

### Usar su propio Git: ahora se admiten GitLab y Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

La función **Bring Your Own Git** se ha ampliado para incluir compatibilidad con repositorios externos, como GitLab y Bitbucket. Esta nueva compatibilidad se suma a la compatibilidad ya existente con repositorios de GitHub privados y de empresa. Al añadir estos nuevos repositorios, también puede vincularlos directamente a sus canalizaciones. Puede alojar estos repositorios en plataformas públicas en la nube o dentro de su infraestructura o nube privada. Esta integración también elimina la necesidad de sincronización constante del código con el repositorio de Adobe y proporciona la capacidad de validar las solicitudes de extracción antes de combinarlas en una rama principal.

Las canalizaciones que usan repositorios externos (excepto las alojadas en GitHub) y el **Activador de la implementación** establecido en **Cambios en Git** ahora se inician automáticamente.

Consulte [Adición de repositorios externos en Cloud Manager](/help/managing-code/external-repositories.md).

![Cuadro de diálogo Añadir repositorio](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Actualmente, las comprobaciones de calidad del código de las solicitudes de extracción listas para usar son exclusivas de los repositorios alojados en GitHub, pero se está trabajando en una actualización para ampliar esta funcionalidad a otros proveedores de Git.

Si le interesa probar esta nueva función y compartir sus comentarios, envíe un correo electrónico a [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) desde su dirección de correo electrónico asociada a su Adobe ID. Asegúrese de incluir qué plataforma Git desea utilizar y si se encuentra en una estructura de repositorio privado/público o de empresa.


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
