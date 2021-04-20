---
title: Seguridad y privacidad
seo-title: Seguridad y privacidad para AEM Cloud Manager
description: Siga esta página para conocer la seguridad y privacidad de sus recursos (código/artefactos).
seo-description: Siga esta página para conocer la seguridad y privacidad de sus recursos (código/artefactos) mediante AEM Cloud Manager.
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
feature: Getting Started
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 3%

---


# Seguridad y privacidad {#security-and-privacy}

[!UICONTROL Cloud Manager] tiene funciones preconfiguradas con los permisos adecuados. Esta sección resalta la seguridad y privacidad de sus recursos (código/artefactos) mediante AEM Cloud Manager. Además, [!UICONTROL Cloud Manager] tiene funciones preconfiguradas con los permisos adecuados.

Para obtener más información sobre las posibles funciones que puede asignar en los permisos de rol de Admin Console y usuario, consulte [Permisos basados en roles](/help/using/role-based-permissions.md).


## Aislamiento de recursos {#resource-isolation}

Los clientes que utilicen [!UICONTROL Cloud Manager] necesitarán sus credenciales de IMS para autenticarse, ya que todos los permisos vinculados a [!UICONTROL Cloud Manager] se configurarán y vincularán a su organización IMS. Durante el proceso de incorporación, el equipo de aprovisionamiento garantiza que el aislamiento de recursos se aplique en [!UICONTROL Cloud Manager].

## Seguridad de datos {#data-security}

El código de [!UICONTROL Cloud Manager] está cifrado en tránsito. Los binarios que crea Cloud Manager también se cifran en tránsito y se cifran cuando se almacenan.

Cada cliente obtiene su propio **Repositorio Git** y su código es seguro y no se comparte con ninguna otra **Organización**.

## Privacidad de datos {#data-privacy}

[!UICONTROL Cloud Manager] se adhiere a los principios de privacidad definidos por el Adobe. Los desarrolladores insertan código de forma segura en el **Repositorio Git** a través de HTTPS.

La interfaz de usuario (IU) para [!UICONTROL Cloud Manager] se basa en servicios que cumplen con un marco de control común definido por el Adobe. La interfaz de usuario para [!UICONTROL Cloud Manager] utiliza servicios seguros de varios proveedores de la nube.
