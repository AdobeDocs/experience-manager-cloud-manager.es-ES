---
title: Notas de la versión 2025.10.0 de Cloud Manager
description: Obtenga información sobre la versión de Cloud Manager 2025.10.0 en Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 03fc811a1a617263efd0f1d5667bba6975826a0e
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 59%

---

# Notas de la versión de Cloud Manager 2025.10.0 en Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Obtenga información sobre la versión de [!UICONTROL Cloud Manager] 2025.10.0 en Adobe Managed Services.

Consulte también las [notas de la versión actual de Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/release-notes/home).

## Fechas de lanzamiento {#release-date}

La fecha de lanzamiento de la versión 2025.10.0 de [!UICONTROL Cloud Manager] es el viernes, 02 de octubre de 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La próxima versión está planificada para el viernes, 06 de noviembre de 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Novedades {#what-is-new}







## Programas Beta {#beta-program}

Participe en los programas de Beta de Cloud Manager para obtener acceso exclusivo a las próximas funciones antes de su lanzamiento general.

Actualmente están disponibles las siguientes oportunidades:

### Extensibilidad y personalización de Experience Hub {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) sirve como punto de entrada a AEM, personalizado para las necesidades de la organización. Informe a Adobe sobre las extensiones de la interfaz de usuario de AEM existentes para que puedan ayudarle a habilitarlas en Experience Hub con el mínimo esfuerzo.

![Diagrama del flujo de trabajo de personalización y extensibilidad de Experience Hub](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Incruste experiencias personalizadas en Experience Hub para ampliar y personalizar el tablero de su organización. Además de los widgets integrados de Adobe, agregue los suyos propios mediante el marco de trabajo [Extensibilidad de la interfaz de usuario](https://developer.adobe.com/uix/docs/). Cree aplicaciones de interfaz de usuario basadas en JavaScript y envíelas a sus usuarios para que cumplan con los requisitos y flujos de trabajo específicos de la empresa.

¿Te interesa la versión beta? Envíe un correo electrónico a [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) con su identificador de organización de Adobe y una breve descripción de la personalización que desea crear.

### Compilaciones más rápidas con almacenamiento en caché de módulos {#quick-build-cm-pipelines}

Un nuevo modelo de compilación compila solo los módulos modificados (en lugar de todo el repositorio) mediante el almacenamiento en caché de nivel de módulo para acortar los tiempos de compilación. Se aplica a las canalizaciones de calidad de código, de pila completa y de solo ensayo.

¿Te interesa la versión beta? Envíe un correo electrónico a [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) con su identificador de organización de Adobe y el identificador de programa.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->


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

No hay correcciones de errores significativas en la versión de octubre de Cloud Manager.

<!--
Known Issues {#known-issues}

* A -->
