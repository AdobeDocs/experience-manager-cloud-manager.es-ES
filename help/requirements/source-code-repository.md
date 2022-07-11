---
title: Repositorio de códigos de origen
description: Obtenga información sobre el repositorio de Git que se aprovisiona para cada programa que tiene en Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 2%

---


# Repositorio de códigos de origen {#source-code-repository}

Obtenga información sobre el repositorio de Git que se aprovisiona para cada programa que tiene en Cloud Manager.

## Repositorio de Cloud Manager {#cloud-manager-repository}

Su [!UICONTROL AEM Managed Services] la suscripción incluye un repositorio de código fuente aprovisionado y administrado por Adobe. A cada programa se le asigna un único repositorio de Git, donde se almacena y protege su código asociado.

Como práctica recomendada, siempre debe utilizar el repositorio de Git de Cloud Manager, que está vacío sin ramas configuradas o proyectos de muestra. Para utilizar el repositorio Git de Cloud Manager, se le proporcionará un token de acceso privado que le permitirá utilizar cualquier cliente Git para crear ramas, almacenar y recuperar su código, enumerar el historial de confirmaciones, etc.

Para obtener más información sobre cómo configurar ramas en Git, consulte [Configuración de ramas de versiones.](/help/getting-started/configuring-branches.md)

Para obtener más información sobre cómo utilizar el repositorio Git de Cloud Manager con la canalización CI/CD, consulte los documentos [Configurar canalizaciones de producción](/help/using/production-pipelines.md) y [Configuración de canalizaciones que no sean de producción](/help/using/non-production-pipelines.md) para obtener más información.

## Repositorio local {#on-premise-repository}

Es posible que tenga un repositorio de Git existente y desee seguir usándolo, en cuyo caso puede utilizar la función de Git para varios repositorios remotos. El desarrollo diario seguiría ocurriendo en su repositorio de Git. Cuando una rama de lanzamiento esté lista para una implementación en producción, puede insertar el código más reciente en el repositorio de Git de Cloud Manager y almacenar en déclencheur la canalización CI/CD de Cloud Manager.

Para ver los comandos de git comunes, consulte la [Hoja de referencia de Git](https://education.github.com/git-cheat-sheet-education.pdf) en el sitio web de GitHub.
