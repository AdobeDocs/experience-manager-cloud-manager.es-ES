---
title: Repositorio de códigos de origen
seo-title: Repositorio de códigos de origen para Adobe AEM Cloud Manager
description: Siga esta página para obtener más información sobre el repositorio de Git que se aprovisiona para cada programa que tenga en Cloud Manager.
seo-description: Siga esta página para obtener más información sobre el repositorio de Git que se aprovisiona para cada programa que tenga en Adobe AEM Cloud Manager.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
feature: Provisioning
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 2%

---


# Repositorio de códigos de origen {#source-code-repository}

## Repositorio de Cloud Manager {#cloud-manager-repository}

Su suscripción [!UICONTROL AEM Managed Services] incluirá un repositorio de código fuente aprovisionado y administrado por Adobe. Al programa de cada cliente se le asigna un único **Repositorio de Git**, donde el código asociado se almacenará y protegerá.

Como práctica recomendada, siempre debe utilizar el repositorio Git de Cloud Manager, que está vacío sin ramas configuradas o proyectos de muestra. Para utilizar el repositorio Git de Cloud Manager, se le proporcionará un **token de acceso privado** que le permitirá utilizar cualquier cliente compatible con Git para crear ramas, almacenar y recuperar su código, enumerar el historial de confirmaciones, etc.

Para obtener más información sobre cómo configurar ramas en Git, consulte [Configuración de las ramas de las versiones](configure-your-release-branches.md).

Para obtener más información sobre cómo utilizar el **Repositorio Git** de Cloud Manager con la canalización CI/CD, consulte [Configuración de la canalización CI/CD](configuring-pipeline.md).

## Repositorio local {#on-premise-repository}

En algunos casos, tendrá un repositorio Git existente y desea seguir usándolo. En estos casos, puede utilizar la función compatible de Git para varios repositorios remotos. El desarrollo diario seguiría ocurriendo en su repositorio Git. Cuando una rama de lanzamiento esté lista para una implementación en producción, insertará su código más reciente en el repositorio Git de Cloud Manager y déclencheur la canalización CI/CD de Cloud Manager.

>[!NOTE]
>
>Para ver los comandos Git comunes, consulte la [Hoja de referencia de Git](https://education.github.com/git-cheat-sheet-education.pdf).

