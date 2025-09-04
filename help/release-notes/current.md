---
title: Notas de la versión 2025.9.0 de Cloud Manager
description: Obtenga información sobre la versión de Cloud Manager 2025.9.0 en Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 68e546c1337122f823d63529ebd68d6966bb132a
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 75%

---

# Notas de la versión de Cloud Manager 2025.9.0 en Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Obtenga información sobre la versión de [!UICONTROL Cloud Manager] 2025.9.0 en Adobe Managed Services.

Consulte también las [notas de la versión actual de Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/release-notes/home).

## Fechas de lanzamiento {#release-date}

La fecha de lanzamiento de la versión 2025.9.0 de [!UICONTROL Cloud Manager] es el viernes, 04 de septiembre de 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La próxima versión está planificada para el viernes, 02 de octubre de 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## Novedades {#what-is-new}

* **Se ha agregado compatibilidad para repositorios privados de Azure DevOps**

  Las actualizaciones de la documentación incluyen pasos de configuración para Traer su propio Git con Azure DevOps y validación de solicitudes de extracción. Consulte [Agregar repositorios externos en Cloud Manager](/help/managing-code/external-repositories.md).

* **Comprobaciones de solicitudes de extracción para repositorios privados**

  Cloud Manager ahora admite canalizaciones de configuración con repositorios privados en GitHub, Bitbucket, Azure DevOps y GitLab. Consulte ![Comprobaciones de solicitudes de extracción para repositorios privados](/help/managing-code/github-check-config.md).

## Programas Beta {#beta-program}

Participe en los programas de Beta de Cloud Manager para obtener acceso exclusivo a las próximas funciones antes de su lanzamiento general.

Actualmente están disponibles las siguientes oportunidades:


### Traiga su propio Git (BYOG) {#gitlab-bitbucket-azure-vsts}

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

No hay correcciones de errores significativas en la versión de agosto de Cloud Manager.

<!--
Known Issues {#known-issues}

* A -->
