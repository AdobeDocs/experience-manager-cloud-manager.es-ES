---
title: Integración de Git con Adobe Cloud Manager
description: Serie de vídeos que describen la configuración e integración de un repositorio de Git administrado por el cliente (local) con Adobe Cloud Manager.
seo-title: Git Integration with Adobe Cloud Manager
seo-description: A video series that walks through the set up and integration of a customer-managed (on-premise) git repository with Adobe Cloud Manager.
feature: Git Repositories
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 0bc3e775ef2432cdb8d3bd5470953c07c6628148
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 4%

---

# Integración de Git con Adobe Cloud Manager

Adobe Cloud Manager incluye un único repositorio de Git que se utiliza para implementar código mediante las canalizaciones CI/CD de Cloud Manager. Los clientes pueden utilizar el repositorio de Git de Cloud Manager de forma predeterminada. Los clientes también tienen la opción de integrar un **gestionado por el cliente** repositorio de Git con Cloud Manager.

## Información general sobre la integración de Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

Esta serie de vídeos explora varios casos de uso cuando se trata de integrar un repositorio de Git administrado por el cliente con Cloud Manager, incluidos:

* [Sincronización inicial](#initial-sync)
* [Estrategia básica de ramas](#branching-strategy)
* [Desarrollo de ramas de funciones](#feature-development)
* [Implementación de producción](#production-deployment)
* [Sincronización de etiquetas de versión](#sync-tags)

Para obtener una descripción general completa, consulte la [Guía del usuario de Cloud Manager.](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=es) La serie de vídeos asume un conocimiento básico de la gestión de Git y control de fuentes. Consulte la [recursos adicionales a continuación](#additional-resources) para obtener más información sobre git.

>[!NOTE]
>
> Los pasos y las convenciones de nomenclatura descritos en esta serie de vídeos representan algunas prácticas recomendadas para trabajar con un repositorio de Git administrado por el cliente y Cloud Manager. Se espera que los convenios y flujos de trabajo descritos se adapten a los equipos de desarrollo individuales.

## Sincronización inicial {#initial-sync}

Primeros pasos para sincronizar un repositorio Git administrado por el cliente con el repositorio Git de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Estrategia básica de ramas {#branching-strategy}

Configure una estrategia básica de ramificación para aprovechar las ventajas de Cloud Manager [tuberías de producción y no producción.](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html)

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Desarrollo de ramas de funciones {#feature-development}

Utilice una rama de funciones para aislar los cambios de código en un repositorio de Git administrado por el cliente y sincronizar con el repositorio de Git de Cloud Manager para utilizar una canalización que no sea de producción para las pruebas de calidad y validación del código.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Implementación de producción {#production-deployment}

Prepare código para una versión de producción en un repositorio de Git administrado por el cliente y sincronícelo con el repositorio de Git de Cloud Manager para poder implementarlo en entornos de ensayo y producción.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Sincronización de etiquetas de versión {#sync-tags}

Sincronice las etiquetas de versión de un repositorio de Git de Cloud Manager en un repositorio de Git administrado por el cliente para proporcionar visibilidad sobre qué código se ha implementado en los entornos de ensayo y producción.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Recursos adicionales {#additional-resources}

* [Documentación de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)
* [Recursos de GitHub](https://try.github.io)
* [Tutorials de Git asiáticos](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Hoja de referencia de Git](https://education.github.com/git-cheat-sheet-education.pdf)
