---
title: Notas de la versión 2025.2.0 de Cloud Manager
description: Obtenga información sobre la versión de Cloud Manager 2025.2.0 en Adobe Managed Services.
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 51dd060ec9b922ace9ce537cac669c61154284e8
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 26%

---

# Notas de la versión de Cloud Manager 2025.2.0 en Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

Obtenga información sobre la versión de [!UICONTROL Cloud Manager] 2025.2.0 en Adobe Managed Services.

Vea también las [notas de la versión actual de Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/release-notes/home).

## Fechas de lanzamiento {#release-date}

La fecha de lanzamiento de la versión 2025.2.0 de [!UICONTROL Cloud Manager] es el viernes, 13 de febrero de 2025.

La próxima versión planificada es el viernes, 13 de marzo de 2025.

## Novedades {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* **SonarQube actualizado**

  A partir del jueves, 13 de febrero de 2025, el paso de calidad del código de Cloud Manager ahora utiliza SonarQube 9.9.5.90363.

  Las reglas actualizadas, disponibles para AMS en [este vínculo](/help/using/code-quality-testing.md#code-quality-testing-step), determinan las puntuaciones de seguridad y la calidad del código para las canalizaciones de Cloud Manager.

* SonarQube 9.9 es ahora el motor de análisis de calidad de código predeterminado para todos los clientes.

* **Compatibilidad con el entorno de compilación Java 17 y Java 21**

  Los clientes ahora pueden, opcionalmente, compilar con Java 17 o Java 21, beneficiándose de las mejoras de rendimiento y de las nuevas funciones del lenguaje. Consulte [Entorno de compilación](/help/getting-started/build-environment.md) para ver los pasos de configuración, incluida la actualización de la descripción del proyecto Maven, y ciertas versiones de la biblioteca.

  >[!NOTE]
  >En entornos Cloud Service, cuando la versión de compilación se establece en Java 17 o Java 21, el tiempo de ejecución predeterminado es Java 21.

* **Validaciones de copia de contenido extendidas**

  Se han actualizado las reglas de validación de copia de contenido. Con esta versión, los usuarios ya no pueden almacenar en déclencheur una copia de contenido si hay ejecuciones de canalización activas en el entorno de origen o de destino. Los usuarios deben esperar hasta que se completen todas las ejecuciones de canalización en curso antes de iniciar una copia de contenido.

<!-- 
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features.

### Bring Your Own Git - now with support for GitLab and Bitbucket {#gitlab-bitbucket}

The **Bring Your Own Git** feature has been expanded to include support for external repositories, such as GitLab and Bitbucket. This new support is in addition to the already existing support for private and enterprise GitHub repositories. When you add these new repos, you can also link them directly to your pipelines. You can host these repositories on public cloud platforms or within your private cloud or infrastructure. This integration also removes the need for constant code synchronization with the Adobe repository and provides the ability to validate pull requests before merging them into a main branch.

Pipelines using external repositories (excluding GitHub-hosted ones) and the **Deployment Trigger** set to **On Git Changes** now start automatically.

See [Add external repositories in Cloud Manager](/help/managing-code/external-repositories.md).

![Add Repository dialog box](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Currently, the out-of-the-box pull request code quality checks are exclusive to GitHub-hosted repositories, but an update to extend this functionality to other Git vendors is in the works.

If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
