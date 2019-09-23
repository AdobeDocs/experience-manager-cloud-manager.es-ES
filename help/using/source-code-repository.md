---
title: Repositorio de códigos de origen
seo-title: Repositorio de código fuente para Adobe AEM Cloud Manager
description: Siga esta página para obtener información sobre el repositorio de Git que está aprovisionado para cada programa que tenga en Cloud Manager.
seo-description: Siga esta página para obtener información sobre el repositorio de Git suministrado para cada programa que tenga en Adobe AEM Cloud Manager.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requisitos
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
translation-type: tm+mt
source-git-commit: 697311cd00ef96568f6befd2fe76febafc27961e

---


# Repositorio de códigos de origen {#source-code-repository}

## Repositorio de Cloud Manager {#cloud-manager-repository}

Su suscripción incluirá un repositorio de código fuente suministrado y administrado por Adobe. [!UICONTROL AEM Managed Services] A cada programa del cliente se le asigna un único y único **repositorio** Git, donde se almacenará y asegurará el código asociado.

Como práctica recomendada, siempre debe utilizar el repositorio Git del Administrador de nube, que está vacío sin ninguna rama configurada o proyecto de muestra. Para utilizar el repositorio Git del Administrador de nube, se le proporcionará un autentificador **de acceso** privado que le permitirá utilizar cualquier cliente compatible con Git para crear ramas, almacenar y recuperar su código, enumerar el historial de confirmaciones, etc.

Para obtener más información sobre cómo configurar ramas en Git, consulte [Configuración de ramas](configure-your-release-branches.md)de versión.

Para obtener más información sobre cómo utilizar el repositorio **Git** del Administrador de nube con la canalización CI/CD, consulte [Configuración de la canalización](configuring-pipeline.md)CI/CD.

## Repositorio local {#on-premise-repository}

En algunos casos, tendrá un repositorio Git existente y desea seguir utilizándolo. En estos casos, puede utilizar la función admitida por Git para varios repositorios remotos. El desarrollo diario continuaría ocurriendo en su repositorio Git. Cuando una rama de lanzamiento esté lista para una implementación en producción, insertará su código más reciente en el repositorio Git del Administrador de nube y activará el flujo de CD/CI de Cloud Manager.

>[!NOTE]
>
>Para ver los comandos Git comunes, consulte la [hoja](https://education.github.com/git-cheat-sheet-education.pdf)Git.

