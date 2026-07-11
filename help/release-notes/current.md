---
title: Notas de la versión de Cloud Manager 2026.7.0
description: Obtenga información acerca de la versión de Cloud Manager 2026.7.0 en Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: acd33650c938d49bac5c319f8c938202fe543bbd
workflow-type: tm+mt
source-wordcount: 391
ht-degree: 14%

---


# Notas de la versión de Cloud Manager 2026.7.0 en Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Obtenga información acerca del lanzamiento de [!UICONTROL Cloud Manager] 2026.6.0 en Adobe Managed Services.

Consulte también las [notas de la versión actual de Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/release-notes/home).

## Fechas de lanzamiento {#release-date}

La fecha de la versión de [!UICONTROL Cloud Manager] 2026.7.0 es el jueves, 9 de julio de 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La próxima versión planificada es el jueves, 6 de agosto de 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Novedades {#what-is-new}

<!-- There are no significant new features in the June 2026 Cloud Manager on AMS release. -->

* **Rendimiento de compilación mejorado con almacenamiento en caché de módulos**
Un nuevo modelo de compilación compila solo los módulos modificados (en lugar de todo el repositorio) mediante el almacenamiento en caché de nivel de módulo para mejorar el rendimiento de la compilación. Se aplica a las canalizaciones de producción. Usted controla qué canalizaciones de producción utilizan **Smart Build**.

  Para obtener más información, consulte lo siguiente:

   * [Acerca del uso de Smart Build en una canalización de producción](/help/using/production-pipelines.md#about-smart-build) y [Acerca del uso de Smart Build en una canalización que no es de producción](/help/using/non-production-pipelines.md#about-smart-build)
   * [Agregar una canalización de producción](/help/using/production-pipelines.md##adding-production-pipeline) y [Agregar una canalización que no sea de producción](/help/using/non-production-pipelines.md#add-non-production-pipeline).

## Programas Beta {#beta-program}

Participe en los programas Beta de Cloud Manager para obtener acceso exclusivo a las próximas funciones antes de su lanzamiento general.

>[!IMPORTANT]
>
>Las versiones de Beta contienen defectos y se proporcionan &quot;TAL CUAL&quot; sin garantía de ningún tipo. Adobe no tiene obligación de mantener, corregir, actualizar, cambiar, modificar o admitir de otro modo (mediante los Servicios de soporte de Adobe o de otro modo) las versiones beta. Los clientes utilizan las versiones beta por su cuenta y riesgo, y no deben confiar en el funcionamiento o el rendimiento correctos de las versiones beta ni en la documentación o los materiales adjuntos. Las funciones y las API de la versión beta están sujetas a cambios sin previo aviso. Cualquier uso de las versiones beta corre por cuenta y riesgo del cliente.

Actualmente están disponibles las siguientes oportunidades del programa beta:

### Canalizaciones de nivel web para AEM Managed Services {#web-tier-pipelines}

Cloud Manager ahora admite canalizaciones de nivel web dedicadas para programas de AMS, lo que permite a los equipos implementar configuraciones de nivel web y Dispatcher independientemente de las implementaciones de pila completa. Esto permite una iteración más rápida en los cambios del nivel web y reduce las ejecuciones innecesarias de la canalización completa. Cuando se configura una canalización de nivel web, las canalizaciones de pila completa omiten automáticamente la implementación de nivel web para ese entorno para evitar conflictos de implementación. Al eliminar la canalización de nivel web, se restaura automáticamente el comportamiento de implementación predeterminado.

Para unirse a Beta, póngase en contacto con su ingeniero de éxito del cliente de Adobe para obtener más información.




## Correcciones de errores {#bug-fixes}

No hay correcciones de errores significativas en la versión de julio de 2026 de Cloud Manager en AMS.

<!--
Known Issues {#known-issues}

* A 
-->
