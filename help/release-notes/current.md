---
title: Notas de la versión 2023.12.0
description: Estas son las notas de la versión 2023.12.0 de Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 2ac254508e4015fea21c4fcd087703ac5fbeeec6
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 70%

---


# Notas de la versión 2023.12.0 de Cloud Manager {#release-notes}

Esta página documenta las notas de la versión 2023.12.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Para las notas de la última versión de Cloud Manager en AEM as a Cloud Service, consulte [Cloud Manager en las notas de la versión actuales de AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=es)

## Fecha de la versión {#release-date}

La fecha de lanzamiento de la versión 2023.12.0 de [!UICONTROL Cloud Manager] es el 14 de diciembre de 2023. La próxima versión está planificada para el 18 de enero de 2024.

## Novedades {#what-is-new}

* [Permisos personalizados de Cloud Manager](/help/using/custom-permissions.md) le permite crear nuevos perfiles de permisos personalizados con permisos configurables para restringir el acceso a programas, canalizaciones y entornos para los usuarios de Cloud Manager.
* Los despliegues de actualizaciones en la [entorno de compilación](/help/getting-started/build-environment.md) que fueron [anunciado e iniciado con la versión de octubre de Cloud Manager](/help/release-notes/2023/2023-10-0.md) se han completado.
   * Se ha añadido compatibilidad con el nodo 18 para [canalizaciones front-end y full stack.](/help/overview/ci-cd-pipelines.md)
   * Se ha actualizado Java 8 versión secundaria a `jdk1.8.0_371`.
   * Se ha actualizado Java 11 versión menor a `jdk-11.0.20`.
   * Maven se ha actualizado a la versión 3.8.8
      * Maven ahora deshabilita todo lo inseguro `http://*` duplicaciones de forma predeterminada.
      * [Adobe recomienda](/help/getting-started/build-environment.md#https-maven) Los usuarios de actualizan sus repositorios de Maven para utilizar HTTPS en lugar de HTTP.
* La imagen base del contenedor de compilación se actualizó a Ubuntu 22.04.

## Programa para primeros usuarios {#early-adoption}

Participe en nuestro programa para clientes pioneros y tenga la oportunidad de probar algunas de las próximas funciones

### Traer su propio GitHub {#byo-github}

Si utiliza GitHub para administrar sus repositorios, [ahora puede validar códigos directamente dentro de sus repositorios de GitHub a través de Cloud Manager.](/help/managing-code/byo-github.md)Esta integración elimina la necesidad de sincronizar el código de forma coherente con el repositorio de Adobe y le permite comprobar las solicitudes de extracción antes de combinarlas en las ramas principales.

Si está interesado en probar esta nueva funcionalidad y en compartir sus comentarios, envíe un correo electrónico a `Grp-CloudManager_BYOG@adobe.com` desde su dirección de correo electrónico asociada a su Adobe ID.
