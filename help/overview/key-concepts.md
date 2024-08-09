---
title: Conceptos clave
description: Al igual que todas las herramientas potentes, Cloud Manager engloba muchos conceptos y términos. Este documento resume algunos de los más importantes para usted a medida que comienza a utilizarlo.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 70%

---


# Conceptos clave {#key-concepts}

Al igual que todas las herramientas potentes, Cloud Manager engloba muchos conceptos y términos. Este documento resume algunos de los más importantes para usted a medida que comienza a utilizarlo.

## Aplicación {#application}

Una aplicación es el conjunto de personalizaciones y configuraciones creadas por un cliente para adaptar la [solución](#solution) subyacente (como AEM Sites o AEM Assets) para sus casos de uso y necesidades específicos. Una aplicación es una unidad lógica que puede estar compuesta por varios [artefactos](#artifact).

Una aplicación de ejemplo es la aplicación de estilo de vida [WKND](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=es) ficticia.

## Artefacto {#artifact}

Un artefacto es una unidad implementable y el resultado de algún proceso de compilación que transforma el código fuente en una sola unidad. Por ejemplo, un archivo .zip que contenga el código fuente.

## Repositorio de artefactos {#artifact-repository}

Un repositorio de artefactos es un lugar de almacenamiento en el que se guardan y aseguran [artefactos](#artifact) específicos del cliente.

## Entorno {#environment}

Un entorno es un único clúster de máquinas virtuales dentro de un [programa](#program). AEM Por ejemplo, se compone de una instancia de creación (opcionalmente con una instancia de creación de espera pasiva adicional), cero o más instancias de publicación, una o más instancias de Dispatcher y un equilibrador de carga.

## Repositorio de Git {#git-repository}

Un repositorio de Git es una ubicación donde se almacena código fuente específico del cliente y se puede acceder a [usando Git](https://git-scm.com).

## Instancia {#instance}

AEM Una instancia es un servidor virtual específico que ejecuta la [solución](#solution) de la. Las instancias representan una sola unidad lógica desde la perspectiva de la implementación.

## Organización {#organization}

Una organización es un constructo de Adobe que representa a un cliente empresarial. Una compañía puede tener varias organizaciones en función de cómo se hayan aprovisionado en el sistema Identity Management de Adobe (IMS).

## Canalización {#pipeline}

Una canalización es un conjunto de pasos de implementación que se ejecutan de forma secuencial.

## Producto {#product}

Un producto es un conjunto específico de funcionalidades dentro de una [solución](#solution) con licencia de una organización. Diferentes [programas](#program) dentro de una organización pueden tener derecho a diferentes conjuntos de productos, por ejemplo, AEM Sites, AEM Assets o AEM Forms.

## Programa {#program}

Un programa es un conjunto de entornos que admiten una agrupación lógica de iniciativas de clientes, que generalmente corresponden a contratos de nivel de servicio (SLA) adquiridos. Cada programa tiene exactamente un entorno de producción y puede tener muchos entornos que no sean de producción.

## Solución {#solution}

Una solución es la que ofrece Adobe [!UICONTROL Experience Cloud]. Por ejemplo, Adobe Experience Manager, Adobe Target o Adobe Analytics.

## Etapa {#step}

Un paso es un conjunto de instrucciones configurado que logra alguna unidad de trabajo como componente básico de una [canalización](#pipeline).
