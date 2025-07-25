---
title: Notas de la versión 2025.7.0 de Cloud Manager
description: Obtenga información sobre la versión de Cloud Manager 2025.7.0 en Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: a1f023b8ecc6fcae97832c5f3fad6bb8ae79ced1
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 69%

---

# Notas de la versión de Cloud Manager 2025.7.0 en Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Obtenga información sobre la versión de [!UICONTROL Cloud Manager] 2025.7.0 en Adobe Managed Services.

Consulte también las [notas de la versión actual de Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/release-notes/home).

## Fechas de lanzamiento {#release-date}

La fecha de lanzamiento de la versión 2025.7.0 de [!UICONTROL Cloud Manager] es el viernes, 10 de julio de 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La próxima versión está planificada para el jueves, 7 de agosto de 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## Novedades {#what-is-new}

* **Canalizaciones solo de ensayo y de producción**

  Cloud Manager ahora es compatible con canalizaciones solo de ensayo y de producción. Esta función le permite dividir implementaciones de producción de pila completa en canalizaciones más pequeñas y específicas para fines específicos. <!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![Agregar cuadro de diálogo de canalización que no sea de producción con el botón de opción Código de pila completa seleccionado y el entorno de ensayo seleccionado](/help/release-notes/assets/add-non-production-pipeline.png)

  Consulte [Canalizaciones solo de fase y solo de producción](/help/using/stage-prod-only.md).

* **Canalizaciones favoritas**

  En esta versión, Cloud Manager introduce la capacidad de fijar canalizaciones favoritas, lo que permite marcar canalizaciones específicas como favoritas para que aparezcan en la parte superior de la lista en la página **Canalizaciones**. Esta mejora facilita la búsqueda y ejecución de las canalizaciones a las que se accede con frecuencia. <!-- CMGR-68293 -->

  ![Canalizaciones marcadas como favoritas](/help/release-notes/assets/pipeline-favorites.png) *Dos canalizaciones marcadas como favoritas.*

  Consulte [Marcado de canalizaciones como favoritas](/help/using/managing-pipelines.md#pipeline-favorites).


## Programas de Alpha/Beta {#beta-program}

Participe en los programas alfa y beta de Cloud Manager para obtener acceso exclusivo a las próximas funciones antes de su lanzamiento general.

Actualmente están disponibles las siguientes oportunidades:


### Usar su propio Git: ahora se admiten GitLab y Bitbucket {#gitlab-bitbucket}

La función **Traer tu propio Git** (BYOG) se ha ampliado para incluir compatibilidad con repositorios externos, como GitLab y Bitbucket. Esta nueva compatibilidad se suma a la compatibilidad ya existente con repositorios de GitHub privados y de empresa. Al añadir estos nuevos repositorios, también puede vincularlos directamente a sus canalizaciones. Puede alojar estos repositorios en plataformas públicas en la nube o dentro de su infraestructura o nube privada. Esta integración también elimina la necesidad de sincronización constante del código con el repositorio de Adobe y proporciona la capacidad de validar las solicitudes de extracción antes de combinarlas en una rama principal.

Las canalizaciones que usan repositorios externos (excepto las alojadas en GitHub) y el **Activador de la implementación** establecido en **Cambios en Git** ahora se inician automáticamente.

Consulte [Adición de repositorios externos en Cloud Manager](/help/managing-code/external-repositories.md).

![Cuadro de diálogo Añadir repositorio](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Actualmente, las comprobaciones de calidad del código de las solicitudes de extracción listas para usar son exclusivas de los repositorios alojados en GitHub, pero se está trabajando en una actualización para ampliar esta funcionalidad a otros proveedores de Git.

Si le interesa probar esta nueva función y compartir sus comentarios, envíe un correo electrónico a [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) desde su dirección de correo electrónico asociada a su Adobe ID. Asegúrese de incluir qué plataforma Git desea utilizar y si se encuentra en una estructura de repositorio privado/público o de empresa.

#### Administrar tókenes de acceso{#access-tokens}

Use **Administrar tokens de acceso** con BYOG para ver, cambiar el nombre y eliminar los tokens de acceso asociados con repositorios externos de Git Traer su propio Git, como GitHub Enterprise, GitLab, Bitbucket y Azure DevOps.

Consulte [Administración de tokens de acceso](/help/managing-code/manage-access-tokens.md).

Si le interesa probar esta nueva función y compartir sus comentarios, envíe un correo electrónico a [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) desde su dirección de correo electrónico asociada a su Adobe ID. Asegúrese de incluir qué plataforma Git desea utilizar y si se encuentra en una estructura de repositorio privado/público o de empresa.


## Correcciones de errores {#bug-fixes}

No hay correcciones de errores significativas en la versión de julio de Cloud Manager.

<!--
Known Issues {#known-issues}

* A -->
