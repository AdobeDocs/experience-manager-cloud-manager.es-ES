---
title: Seguridad y privacidad
seo-title: Seguridad y privacidad de AEM Cloud Manager
description: Siga esta página para conocer la seguridad y privacidad de sus recursos (código/artefactos).
seo-description: Siga esta página para conocer la seguridad y privacidad de sus recursos (código/artefactos) mediante AEM Cloud Manager.
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: 7cbc42108a6ccc8f7303eb76fd8ca2e9027f49e0

---


# Seguridad y privacidad {#security-and-privacy}

[!UICONTROL Cloud Manager] tiene funciones preconfiguradas con los permisos adecuados. Esta sección resalta la seguridad y la privacidad de sus recursos (código/artefactos) mediante AEM Cloud Manager. Además, [!UICONTROL Cloud Manager] tiene funciones preconfiguradas con los permisos adecuados.

Para obtener información sobre las posibles funciones que puede asignar en la Consola de administración y los permisos de funciones de usuario, consulte Permisos [basados en](/help/using/role-based-permissions.md)roles.


## Aislamiento de recursos {#resource-isolation}

Los clientes que utilicen [!UICONTROL Cloud Manager] sus credenciales de IMS deberán autenticarse, ya que todos los permisos vinculados a [!UICONTROL Cloud Manager] se configurarán y se vincularán a su organización de IMS. Durante el proceso de integración, el equipo de aprovisionamiento garantiza que se aplique el aislamiento de recursos en [!UICONTROL Cloud Manager].

## Seguridad de datos {#data-security}

El código en [!UICONTROL Cloud Manager] se cifra en tránsito. Los binarios que crea Coud Manager también se cifran en tránsito y se cifran cuando se almacenan.

Cada cliente obtiene su propio **repositorio** Git y su código es seguro y no se comparte con ninguna otra **organización**.

## Privacidad de datos {#data-privacy}

[!UICONTROL Cloud Manager] se adhiere a los principios de privacidad definidos por Adobe. Los desarrolladores insertan código de forma segura en el repositorio **** Git a través de HTTPS.

La interfaz de usuario (UI) de [!DNL para [!UICONTROL Cloud Manager]] se basa en los servicios que cumplen con un marco de control común definido por Adobe. [!Interfaz de usuario DNL (IU) para [!UICONTROL Cloud Manager]] usa servicios seguros de varios proveedores de nube.
