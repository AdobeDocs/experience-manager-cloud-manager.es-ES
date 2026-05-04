---
title: Repositorio de códigos de origen
description: Obtenga información acerca del repositorio de Git que se aprovisiona para cada programa que tiene en Cloud Manager.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
TQID: https://experienceleague.adobe.com/hdEpqKW0NluPs-w37SeLzpd-EHJNqb2nfSAMQ35man8
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 254
ht-degree: 100%

---

# Repositorio de códigos de origen {#source-code-repository}

Obtenga información acerca del repositorio de Git que se aprovisiona para cada programa que tiene en Cloud Manager.

## Repositorio de Cloud Manager {#cloud-manager-repository}

Su suscripción a [!UICONTROL AEM Managed Services] incluye un repositorio de código fuente aprovisionado y administrado por Adobe. A cada programa se le asigna un único repositorio de Git, donde se almacena y protege su código asociado.

Como práctica recomendada, siempre debe utilizar el repositorio de Git de Cloud Manager, que viene vacío, sin ramas configuradas o proyectos de muestra. Cloud Manager proporciona un token de acceso privado para su repositorio de Git, lo que le permite utilizar cualquier cliente de Git para crear ramas, administrar código, recuperar historial de confirmaciones y mucho más.

Para obtener más información sobre la configuración de ramas en Git, consulte [Configuración de ramas de versiones](/help/getting-started/configuring-branches.md).

Para obtener más información sobre cómo utilizar el repositorio de Git de Cloud Manager con la canalización de CI/CD, consulte los documentos [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) y [Configuración de canalizaciones que no son de producción](/help/using/non-production-pipelines.md) para obtener más información.

## Repositorio On-Premise {#on-premise-repository}

Es posible que ya tenga un repositorio de Git y quiera seguir usándolo, en cuyo caso puede utilizar la funcionalidad de Git para varios repositorios remotos. El desarrollo cotidiano seguirá ocurriendo en su repositorio de Git. Cuando una rama de versión esté lista para una implementación en producción, puede insertar el código más reciente en el repositorio de Git de Cloud Manager y activar la canalización de CI/CD de Cloud Manager.

Para ver los comandos de Git comunes, consulte la [Hoja de características clave de Git](https://education.github.com/git-cheat-sheet-education.pdf).
