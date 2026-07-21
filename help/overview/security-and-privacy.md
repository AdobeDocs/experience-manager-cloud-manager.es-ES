---
title: Seguridad y privacidad
description: Obtenga información acerca de la seguridad y privacidad de los recursos de código y artefactos en Adobe Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
TQID: https://experienceleague.adobe.com/mtWOzJnzV8k403LlyD9Fn9WSE5XTgjHzyVuA4j62MMg
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: d5a34a9f6d050eaff241c0f42c9cf023cbc8036a
workflow-type: tm+mt
source-wordcount: 201
ht-degree: 26%

---

# Seguridad y privacidad {#security-and-privacy}

Obtenga información acerca de la seguridad y privacidad de los recursos de código y artefactos en Adobe Cloud Manager.

## Funciones y permisos {#roles}

Cloud Manager tiene funciones preconfiguradas con los permisos adecuados.

Para obtener más información acerca de las posibles funciones que puede asignar en Admin Console y los permisos de funciones de usuario, consulte el documento [Permisos basados en funciones](/help/requirements/role-based-permissions.md).

## Aislamiento de recursos {#resource-isolation}

Los clientes de Cloud Manager necesitan sus credenciales de IMS para autenticarse, ya que todos los permisos vinculados a Cloud Manager están vinculados a sus organizaciones IMS. Durante el proceso de incorporación, el equipo de aprovisionamiento garantiza que el aislamiento de recursos se aplique en Cloud Manager.

## Seguridad de datos {#data-security}

El código Cloud Manager está cifrado en tránsito. Cloud Manager crea binarios que también se cifran durante la transmisión y se almacenan en un formato cifrado.

Cada cliente obtiene su propio repositorio de Git y el código está protegido y no se comparte con ninguna otra organización.

## Privacidad de datos {#data-privacy}

Cloud Manager se adhiere a los principios de privacidad definidos por Adobe. Los desarrolladores insertan código de forma segura en los repositorios de Git a través de HTTPS.

La interfaz de usuario de Cloud Manager utiliza servicios que cumplen con el Marco de control común de Adobe. La interfaz de usuario de Cloud Manager utiliza servicios seguros de varios proveedores de la nube.
