---
title: Integración de Git con Adobe Cloud Manager
description: Esta serie de vídeos analiza la configuración e integración de un repositorio de Git administrado por el cliente (On-Premise) con Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 91e909273bf2b21d7f6413731923011915079e45
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 100%

---


# Integración de Git con Adobe Cloud Manager

Adobe Cloud Manager incluye un único repositorio de Git que se utiliza para implementar código mediante las canalizaciones CI/CD de Cloud Manager. Puede utilizar el repositorio de Git de Cloud Manager de forma predeterminada o también tiene la opción de integrar un repositorio de Git administrado por el cliente o local con Cloud Manager.

## Información general sobre la integración de Git

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

Esta serie de vídeos explora varios casos de uso relacionados con la integración de un repositorio de Git administrado por el cliente con Cloud Manager.

* [Sincronización inicial](#initial-sync)
* [Estrategia básica de ramas](#branching-strategy)
* [Desarrollo de ramas de características](#feature-development)
* [Implementación de producción](#production-deployment)
* [Sincronización de etiquetas de versión](#sync-tags)

Esta serie de vídeos supone un conocimiento básico de la gestión de Git y control de fuentes. Consulte los [recursos adicionales a continuación](#additional-resources) para obtener más información sobre Git.

Los pasos y las convenciones de nomenclatura descritos en esta serie de vídeos representan algunas prácticas recomendadas para trabajar con un repositorio de Git administrado por el cliente y Cloud Manager. Se espera que los convenios y flujos de trabajo descritos se adapten a los equipos de desarrollo individuales.

Para obtener una descripción general completa de Cloud Manager, consulte el documento [Introducción a Cloud Manager.](/help/introduction.md)

## Sincronización inicial {#initial-sync}

Primeros pasos para sincronizar un repositorio de Git administrado por el cliente con el repositorio de Git de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Estrategia básica de ramas {#branching-strategy}

Configure una estrategia básica de ramificación para aprovechar las ventajas de las [canalizaciones de producción](/help/using/production-pipelines.md) y [que no sean de producción](/help/using/non-production-pipelines.md) de Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Desarrollo de ramas de funciones {#feature-development}

Utilice una rama de características para aislar los cambios de código en un repositorio de Git administrado por el cliente y sincronizarlo con el repositorio de Git de Cloud Manager para utilizar una canalización que no sea de producción para las pruebas de calidad y validación del código.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Implementación de producción {#production-deployment}

Prepare código para una versión de producción en un repositorio de Git administrado por el cliente y sincronícelo con el repositorio de Git de Cloud Manager para poder implementarlo en los entornos de ensayo y producción.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Sincronización de etiquetas de versión {#sync-tags}

Sincronice las etiquetas de versión de un repositorio de Git de Cloud Manager en un repositorio de Git administrado por el cliente para proporcionar visibilidad sobre qué código se ha implementado en los entornos de ensayo y producción.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Recursos adicionales {#additional-resources}

* [Introducción a Cloud Manager](/help/introduction.md)
* [Recursos de GitHub](https://try.github.io)
* [Tutoriales de Atlassian Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Hoja de Git Cheat](https://education.github.com/git-cheat-sheet-education.pdf)
