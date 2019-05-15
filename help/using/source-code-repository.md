---
title: Repositorio de código fuente
seo-title: Repositorio de código fuente para Adobe AEM Cloud Manager
description: Siga esta página para obtener información sobre el repositorio de git proporcionado por cada programa que tenga en Cloud Manager.
seo-description: Siga esta página para obtener información sobre el repositorio de git proporcionado por cada programa que tenga en Adobe AEM Cloud Manager.
uuid: 2 c 42775 f -8703-43 f 7-bad 2-7 dc 086 ea 9 dd 7
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requisitos
discoiquuid: f 90 f 0 f 4 c-c 1 ff -47 f 6-8 d 97-ff 5018561 bf 2
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Repositorio de código fuente {#source-code-repository}

## Repositorio de Administrador de nube {#cloud-manager-repository}

Su [!UICONTROL AEM Managed Services] suscripción incluirá un repositorio de código fuente suministrado y administrado por Adobe. A cada programa de cliente se le asigna un único repositorio **** de Git único, donde el código asociado se almacenará y se protegerá.

Como práctica recomendada, siempre debe utilizar el repositorio Git de Cloud Manager, que queda vacío sin ninguna rama configurada o proyectos de muestra. Para utilizar el repositorio de Git de Cloud Manager, se le proporcionará un **autentificador de acceso privado** que le permitirá utilizar cualquier cliente compatible con Git para crear ramas, almacenar y recuperar su código, enumerar el historial de transferir, etc.

Para obtener más información sobre cómo configurar ramas en Git, consulte [Configuración de las ramas de lanzamiento](configure-your-release-branches.md).

Para obtener más información sobre cómo utilizar el Repositorio **de Git de Cloud Manager** con el canal CI/CD, consulte [Configuración de la cartera CI/CD](configuring-pipeline.md).

## Repositorio in situ {#on-premise-repository}

En algunos casos, tendrá un repositorio de Git existente y quiere seguir usándolo. En estos casos, puede utilizar la función admitida por Git para varios repositorios remotos. El desarrollo día a día seguirá produciéndose en el repositorio de Git. Cuando una ramificación de lanzamiento esté lista para una implementación en producción, insertará el código más reciente en el repositorio Git de Cloud Manager y activará el canal de nube CI/CD.

>[!NOTE]
>
>Para ver los comandos comunes de Git, consulte la Hoja de consejos [de Git](https://education.github.com/git-cheat-sheet-education.pdf).

