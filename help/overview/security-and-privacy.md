---
title: Seguridad y privacidad
description: Obtenga información acerca de la seguridad y privacidad de los activos de código y artefactos en Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: d7751757c1d3bda3d60406a1d39cb41c61f5c863
workflow-type: ht
source-wordcount: '205'
ht-degree: 100%

---


# Seguridad y privacidad {#security-and-privacy}

Obtenga información acerca de la seguridad y privacidad de los activos de código y artefactos en Cloud Manager.

## Funciones y permisos {#roles}

[!UICONTROL Cloud Manager] tiene funciones preconfiguradas con los permisos adecuados.

Para obtener más información acerca de las posibles funciones que puede asignar en Admin Console y los permisos de funciones de usuario, consulte el documento [Permisos basados en funciones.](/help/requirements/role-based-permissions.md)

## Aislamiento de recursos {#resource-isolation}

Los clientes de [!UICONTROL Cloud Manager] necesitan sus credenciales de IMS para autenticarse, ya que todos los permisos vinculados a [!UICONTROL Cloud Manager] están vinculados a sus organizaciones IMS. Durante el proceso de incorporación, el equipo de aprovisionamiento garantiza que el aislamiento de recursos se aplique en [!UICONTROL Cloud Manager].

## Seguridad de datos {#data-security}

El código de [!UICONTROL Cloud Manager] está cifrado en tránsito. Los binarios que crea Cloud Manager también se cifran en tránsito y cuando se almacenan.

Cada cliente obtiene su propio repositorio de Git y el código es seguro y no se comparte con ninguna otra organización.

## Privacidad de datos {#data-privacy}

[!UICONTROL Cloud Manager] se adhiere a los principios de privacidad definidos por Adobe. Los desarrolladores insertan código de forma segura en los repositorios de Git a través de HTTPS.

La interfaz de usuario de [!UICONTROL Cloud Manager] se basa en los servicios que cumplen con un marco de control común de Adobe. La interfaz de usuario de [!UICONTROL Cloud Manager] utiliza servicios seguros de varios proveedores de la nube.
