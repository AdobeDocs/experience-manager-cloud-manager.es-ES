---
title: Repositorio de códigos de origen
description: Obtenga información acerca del repositorio de Git que se aprovisiona para cada programa que tiene en Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 20%

---


# Repositorio de código de Source {#source-code-repository}

Obtenga información acerca del repositorio de Git que se aprovisiona para cada programa que tiene en Cloud Manager.

## Repositorio de Cloud Manager {#cloud-manager-repository}

Su suscripción a [!UICONTROL AEM Managed Services] incluye un repositorio de código fuente aprovisionado y administrado por Adobe. A cada programa se le asigna un único repositorio de Git, donde se almacena y protege su código asociado.

Como práctica recomendada, siempre debe utilizar el repositorio Git de Cloud Manager, que viene vacío, sin ramas configuradas o proyectos de muestra. Cloud Manager proporciona un token de acceso privado para su repositorio de Git, lo que le permite utilizar cualquier cliente de Git para crear ramas, administrar código, recuperar historial de confirmaciones y mucho más.

Para obtener más información sobre cómo configurar ramas en Git, consulte [Configuración de ramas de versiones](/help/getting-started/configuring-branches.md).

Para obtener más información sobre cómo usar el repositorio de Git de Cloud Manager con la canalización de CI/CD, consulte [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) y [Configuración de canalizaciones que no son de producción](/help/using/non-production-pipelines.md) para obtener más información.

## Repositorio On-Premise {#on-premise-repository}

Es posible que ya tenga un repositorio de Git y quiera seguir usándolo, en cuyo caso puede utilizar la función de Git para varios repositorios remotos. El desarrollo cotidiano seguirá ocurriendo en su repositorio de Git. Cuando una rama de versión esté lista para su implementación en producción, puede insertar el código más reciente en el repositorio de Git de Cloud Manager y almacenar en déclencheur la canalización de CI/CD de Cloud Manager.

Para ver los comandos de Git comunes, consulte la [Hoja de características clave de Git](https://education.github.com/git-cheat-sheet-education.pdf).
