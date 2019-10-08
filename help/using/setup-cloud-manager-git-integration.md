---
title: Integración de Git con Adobe Cloud Manager
description: Una serie de vídeos que recorre la configuración y la integración de un repositorio Git administrado por el cliente (in situ) con Adobe Cloud Manager.
seo-title: Integración de Git con Adobe Cloud Manager
seo-description: Una serie de vídeos que recorre la configuración y la integración de un repositorio Git administrado por el cliente (in situ) con Adobe Cloud Manager.
translation-type: tm+mt
source-git-commit: 519f43ff16e0474951f97798a8e070141e5c124b

---


# Integración de Git con Adobe Cloud Manager

Adobe Cloud Manager se suministra con un único repositorio de Git que se utiliza para implementar código mediante las canalizaciones CI/CD de Cloud Manager. Los clientes pueden utilizar el repositorio de Git del Administrador de nube de forma predeterminada. Los clientes también tienen la opción de integrar un repositorio Git local o gestionado por el **cliente** con Cloud Manager.

## Información general sobre la integración de Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/?captions=spa)

Esta serie de vídeos explora varios casos de uso cuando se trata de integrar un repositorio Git administrado por el cliente con Cloud Manager, incluidos:

* [Sincronización inicial](#initial-sync)
* [Estrategia básica de ramas](#branching-strategy)
* [Desarrollo de rama de funciones](#feature-development)
* [Implementación de producción](#production-deployment)
* [Sincronización de etiquetas de versión](#sync-tags)

Para obtener una descripción general completa, consulte la Guía [del usuario del Administrador de](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)nube. La serie de vídeos asume un conocimiento básico de la gestión de la entrada y el control de fuentes. Consulte los recursos [adicionales a continuación](#additional-resources) para obtener más detalles sobre Git.

>[!NOTE]
>
> Los pasos y las convenciones de nombres que se describen en esta serie de vídeos representan algunas prácticas recomendadas para trabajar con un repositorio Git gestionado por el cliente y con Cloud Manager. Se prevé que las convenciones y los flujos de trabajo descritos se adapten a los distintos equipos de desarrollo.

## Sincronización inicial {#initial-sync}

Primeros pasos para sincronizar un repositorio Git administrado por el cliente con el repositorio Git de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12&captions=spa)

## Estrategia básica de ramas {#branching-strategy}

Configure una estrategia básica de ramificación para aprovechar las tuberías [de](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html)producción y no producción de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12&captions=spa)

## Desarrollo de rama de funciones {#feature-development}

Utilice una rama de funciones para aislar los cambios de código en un repositorio Git gestionado por el cliente y sincronizar con el repositorio Git de Cloud Manager para utilizar una canalización que no sea de producción para la calidad del código y las pruebas de validación.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12&captions=spa)

## Implementación de producción {#production-deployment}

Prepare el código para una versión de producción en un repositorio git gestionado por el cliente y sincronícelo con el repositorio git de Cloud Manager para poder implementarlo en entornos de producción y ensayo.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12&captions=spa)

## Sincronización de etiquetas de versión {#sync-tags}

Sincronice las etiquetas de lanzamiento de un repositorio de Git de Cloud Manager con un repositorio de Git gestionado por el cliente para proporcionar visibilidad sobre qué código se ha implementado en los entornos de ensayo y producción.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12&captions=spa)

## Additional Resources {#additional-resources}

* [Documentación de Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)
* [Recursos de GitHub](https://try.github.io)
* [Tutoriales de Atlassian Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Hoja de Chrome Git](https://education.github.com/git-cheat-sheet-education.pdf)