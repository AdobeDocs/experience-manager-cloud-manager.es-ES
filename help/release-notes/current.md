---
title: Notas de la versión de Cloud Manager 2026.11.0
description: Obtenga información acerca del lanzamiento de Cloud Manager 2026.11.0 en Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: 'https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro'
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ed762d86-a04b-452b-a08f-86359bb8ff27
    internal-label: Configuration and operations
subfeature_v2:
  - id: c21ccc2b-e0c8-4853-bf41-f12259ed93f8
    internal-label: Release information
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: b48085c8209c0802f6f2d321865bd1a1ee786139
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 8%
---

# Notas de la versión de Cloud Manager 2026.11.0 en Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Obtenga información acerca del lanzamiento de [!UICONTROL Cloud Manager] 2026.11.0 en Adobe Managed Services.

Consulte también las [notas de la versión actual de Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/release-notes/home).

## Fechas de lanzamiento {#release-date}

La fecha de la versión de [!UICONTROL Cloud Manager] 2026.11.0 es el jueves, 5 de noviembre de 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La próxima versión planificada es el jueves, 3 de diciembre de 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Nuevas funciones {#new-features}

### Canalizaciones de nivel web para AEM Managed Services {#web-tier-pipelines}

Cloud Manager ahora admite canalizaciones de nivel web dedicadas para programas de AMS, lo que permite a los equipos implementar configuraciones de nivel web y Dispatcher independientemente de las implementaciones de pila completa. Esto permite una iteración más rápida en los cambios del nivel web y reduce las ejecuciones innecesarias de la canalización completa.

Cuando se configura una canalización de nivel web, las canalizaciones de pila completa omiten automáticamente la implementación de nivel web para ese entorno para evitar conflictos de implementación. Al eliminar la canalización de nivel web, se restaura automáticamente el comportamiento de implementación predeterminado. <!-- CMGR-27553 -->

Consulte [Canalizaciones de configuración de nivel web](/help/overview/ci-cd-pipelines.md#web-tier-config-pipelines).

## Programas Beta {#beta-program}

Actualmente no hay oportunidades de programas beta disponibles.

<!--
To get exclusive access to upcoming features before their general release, participate in Cloud Manager's beta programs.

>[!IMPORTANT]
>
>Beta releases contain issues and are provided without warranty of any kind. Adobe has no obligation to maintain, correct, update, change, modify or otherwise support (through Adobe Support Services or otherwise) the beta releases. Customers use beta releases at their own risk. Do not rely on the correct functioning or performance of beta releases, or on any accompanying documentation or materials. Features and APIs in beta are subject to change without notice. Any use of the beta releases is entirely at the customer's own risk.

The following beta program opportunity is currently available:
-->

## Corrección de errores {#bug-fixes}


* El análisis de calidad del código falla en proyectos grandes. El análisis de calidad del código (SonarQube) genera registros de depuración de varios gigabytes y se desactiva al analizar determinadas bibliotecas agrupadas, lo que produce un error en la compilación. El análisis se ha corregido para que se complete normalmente en los proyectos afectados. (CMGR-80025)

* La exportación del CSV de uso de sitios mostró etiquetas de mes desplazadas en un mes. En la página Licencia > Detalles de uso del sitio, la exportación a CSV muestra las etiquetas de mes cambiadas un mes antes para los usuarios de zonas horarias posteriores a UTC. La exportación ahora muestra las etiquetas de mes correctas, independientemente de la zona horaria del usuario. (CMGR-80903)

* La reutilización de un nombre de token de acceso ya no sobrescribe el token existente. Al reutilizar un nombre de token de acceso existente dentro de un programa, se sobrescribe el token compartido y se crean secretos de acceso duplicados. Cloud Manager ahora gestiona correctamente la reutilización de nombres de tokens, lo que evita sobrescrituras y duplicados accidentales. (CMGR-81236)


<!--
Known Issues {#known-issues}
-->
