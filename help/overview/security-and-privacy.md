---
title: Seguridad y privacidad
description: Obtenga información sobre la seguridad y privacidad de los recursos de código y artefactos en Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: d7751757c1d3bda3d60406a1d39cb41c61f5c863
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 3%

---


# Seguridad y privacidad {#security-and-privacy}

Obtenga información sobre la seguridad y privacidad de los recursos de código y artefactos en Cloud Manager.

## Roles y permisos {#roles}

[!UICONTROL Cloud Manager] tiene funciones preconfiguradas con los permisos adecuados.

Para obtener más información sobre las posibles funciones que puede asignar en los permisos de rol de Admin Console y usuario, consulte el documento [Permisos basados en roles.](/help/requirements/role-based-permissions.md)

## Aislamiento de recursos {#resource-isolation}

[!UICONTROL Cloud Manager] los clientes necesitan sus credenciales de IMS para autenticarse, ya que todos los permisos vinculados a [!UICONTROL Cloud Manager] están vinculados a sus organizaciones IMS. Durante el proceso de incorporación, el equipo de aprovisionamiento garantiza que el aislamiento de recursos se aplique en [!UICONTROL Cloud Manager].

## Seguridad de los datos {#data-security}

Código de [!UICONTROL Cloud Manager] está cifrado en tránsito. Los binarios que crea Cloud Manager también se cifran en tránsito y se cifran cuando se almacenan.

Cada cliente obtiene su propio repositorio de Git y el código es seguro y no se comparte con ninguna otra organización.

## Privacidad de datos {#data-privacy}

[!UICONTROL Cloud Manager] se adhiere a los principios de privacidad definidos por el Adobe. Los desarrolladores insertan código de forma segura en los repositorios Git a través de HTTPS.

[!UICONTROL Cloud Manager]La interfaz de usuario de se basa en los servicios que cumplen con un marco de control común de Adobe que: [!UICONTROL Cloud Manager]La interfaz de usuario de utiliza servicios seguros de varios proveedores de la nube.
