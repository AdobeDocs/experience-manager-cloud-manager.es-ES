---
title: Conceptos clave
description: Al igual que todas las herramientas potentes, Cloud Manager engloba muchos conceptos y términos. Este documento resume algunos de los más importantes para usted a medida que comienza a utilizarlo.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
TQID: https://experienceleague.adobe.com/usnXqDujeZ04U5hOtiI76aemlj-ceToAOtAYS9U0UuM
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 628eceafe63153d64151937df85937135bdc8e7b
workflow-type: tm+mt
source-wordcount: 421
ht-degree: 60%

---

# Conceptos clave {#key-concepts}

Cloud Manager abarca muchos conceptos y términos. Este artículo resume algunos de los conceptos más importantes para usted a medida que comienza a utilizar Cloud Manager.

## Aplicación {#application}

Una aplicación es el conjunto de personalizaciones y configuraciones creadas por un cliente para adaptar la [solución](#solution) subyacente (como AEM Sites o AEM Assets) para sus casos de uso y necesidades específicos. Una aplicación es una unidad lógica compuesta por varios [artefactos](#artifact).

Una aplicación de ejemplo es la [aplicación de estilo de vida ficticia WKND](https://experienceleague.adobe.com/es/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview).

## Artefacto {#artifact}

Un artefacto es una unidad implementable y el resultado de un proceso de compilación que transforma el código fuente en una sola unidad. Por ejemplo, un archivo .zip que contenga el código fuente.

## Repositorio de artefactos {#artifact-repository}

Un repositorio de artefactos es un lugar de almacenamiento en el que se guardan y aseguran [artefactos](#artifact) específicos del cliente.

## Entorno {#environment}

Un entorno es un único clúster de máquinas virtuales dentro de un [programa](#program). Para AEM, este entorno se compone de una instancia de creación (opcionalmente con una instancia de creación de espera pasiva adicional), cero o más instancias de publicación, una o más instancias de Dispatcher y un equilibrador de carga.

## Repositorio de Git {#git-repository}

Un repositorio de Git es una ubicación donde el código fuente específico del cliente se almacena y es accesible [usando Git](https://git-scm.com).

## Instancia {#instance}

Una instancia es un servidor virtual específico que ejecuta la [solución](#solution) de AEM. Las instancias representan una sola unidad lógica desde la perspectiva de la implementación.

## Organización {#organization}

Una organización es un constructo de Adobe que representa a un cliente empresarial. Una empresa puede tener varias organizaciones en función de cómo se aprovisionan en el sistema Identity Management de Adobe (IMS).

## Canalización {#pipeline}

Una canalización es un conjunto de pasos de implementación que se ejecutan de forma secuencial.

## Producto {#product}

Un producto es un conjunto específico de funcionalidades dentro de una [solución](#solution) con licencia de una organización. Los diferentes [programas](#program) de una organización tienen derecho a diferentes conjuntos de productos, por ejemplo, AEM Sites, AEM Assets o AEM Forms.

## Programa {#program}

Un programa es un conjunto de entornos que admiten una agrupación lógica de iniciativas de clientes, que normalmente corresponden a un service level agreement (SLA) adquirido. Cada programa tiene exactamente un entorno de producción y muchos entornos que no son de producción.

## Solución {#solution}

Una solución es la que ofrece Adobe [!UICONTROL Experience Cloud]. Por ejemplo, Adobe Experience Manager, Adobe Target o Adobe Analytics.

## Etapa {#step}

Un paso es un conjunto de instrucciones configurado que logra alguna unidad de trabajo como componente de una [canalización](#pipeline).
