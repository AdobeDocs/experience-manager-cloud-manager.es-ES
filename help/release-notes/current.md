---
title: Notas de la versión 2025.8.0 de Cloud Manager
description: Obtenga información sobre la versión de Cloud Manager 2025.8.0 en Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: b64b8529e4c6072c9bcb7438dc2d89098d29115d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 61%

---

# Notas de la versión de Cloud Manager 2025.8.0 en Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Obtenga información sobre la versión de [!UICONTROL Cloud Manager] 2025.8.0 en Adobe Managed Services.

Consulte también las [notas de la versión actual de Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/release-notes/home).

## Fechas de lanzamiento {#release-date}

La fecha de lanzamiento de la versión 2025.8.0 de [!UICONTROL Cloud Manager] es el viernes, 07 de agosto de 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La próxima versión está planificada para el viernes, 04 de septiembre de 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## Novedades {#what-is-new}

* **Adobe Experience Hub próximamente**

  A partir del 19 de agosto de 2025, Adobe comienza un despliegue gradual del nuevo Experience Hub para todos los usuarios de Adobe Experience Manager.

  Experience Hub es un punto de partida unificado que ofrece experiencias personalizadas y contextuales para ayudar a los usuarios a lograr sus objetivos más rápido. El despliegue finaliza el 26 de agosto de 2025, y está disponible para todos los usuarios. Se puede acceder directamente al nuevo Experience Hub en [experience.adobe.com](https://experience.adobe.com/). Para obtener más información, consulta [Adobe Experience Hub](/help/experience-hub.md).

* **Canalizaciones solo de ensayo y de producción**

  Cloud Manager ahora es compatible con canalizaciones solo de ensayo y de producción. Esta función le permite dividir implementaciones de producción de pila completa en canalizaciones más pequeñas y específicas para fines específicos. <!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![Agregar cuadro de diálogo de canalización que no sea de producción con el botón de opción Código de pila completa seleccionado y el entorno de ensayo seleccionado](/help/release-notes/assets/add-non-production-pipeline.png)

  Consulte [Canalizaciones solo de fase y solo de producción](/help/using/stage-prod-only.md).

* **Canalizaciones favoritas**

  En esta versión, Cloud Manager introduce la capacidad de fijar canalizaciones favoritas, lo que permite marcar canalizaciones específicas como favoritas para que aparezcan en la parte superior de la lista en la página **Canalizaciones**. Esta mejora facilita la búsqueda y ejecución de las canalizaciones a las que se accede con frecuencia. <!-- CMGR-68293 -->

  ![Canalizaciones marcadas como favoritas](/help/release-notes/assets/pipeline-favorites.png) *Dos canalizaciones marcadas como favoritas.*

  Consulte [Marcado de canalizaciones como favoritas](/help/using/managing-pipelines.md#pipeline-favorites).


## Programas de Beta {#beta-program}

Participe en los programas de Beta de Cloud Manager para obtener acceso exclusivo a las próximas funciones antes de su lanzamiento general.

Actualmente están disponibles las siguientes oportunidades:


### Trae tu propio Git (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Los clientes ahora pueden incorporar sus repositorios Git de Azure DevOps en Cloud Manager, con compatibilidad tanto con los repositorios modernos de Azure DevOps como con los repositorios heredados de VSTS (Visual Studio Team Services).

* Para los usuarios de Edge Delivery Services, el repositorio incorporado se puede utilizar para sincronizar e implementar el código del sitio.
* Para los usuarios de AEM as a Cloud Service y Adobe Managed Services (AMS), el repositorio se puede vincular a canalizaciones de pila completa y de front-end.

La compatibilidad con tipos de canalización adicionales y la validación de solicitudes de extracción a través de canalizaciones de calidad de código estará disponible pronto.

Consulte [Adición de repositorios externos en Cloud Manager](/help/managing-code/external-repositories.md).

![Cuadro de diálogo Añadir repositorio](/help/release-notes/assets/azure-repo.png)

Si le interesa probar esta nueva función y compartir sus comentarios, envíe un correo electrónico a [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) desde su dirección de correo electrónico asociada a su Adobe ID. Asegúrese de incluir qué plataforma Git desea utilizar y si se encuentra en una estructura de repositorio privado/público o de empresa.

#### Administrar tókenes de acceso{#manage-access-tokens}

Use **Administrar tokens de acceso** en Cloud Manager para ver, cambiar el nombre y eliminar los tokens de acceso asociados con repositorios BYOG externos, como GitHub Enterprise, GitLab, Bitbucket y Azure DevOps.

Consulte [Administración de tokens de acceso](/help/managing-code/manage-access-tokens.md).

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

## Correcciones de errores {#bug-fixes}

No hay correcciones de errores significativas en la versión de julio de Cloud Manager.

<!--
Known Issues {#known-issues}

* A -->
