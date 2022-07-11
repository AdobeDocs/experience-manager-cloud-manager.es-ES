---
title: Conceptos clave
description: Al igual que todas las herramientas potentes, Cloud Manager engloba muchos conceptos y términos. Este documento resume algunos de los más importantes para usted a medida que comienza a utilizar Cloud Manager.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: 73e322cf93dc7709b7581860974079c8d94034ba
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 4%

---


# Conceptos clave {#key-concepts}

Al igual que todas las herramientas potentes, Cloud Manager engloba muchos conceptos y términos. Este documento resume algunos de los más importantes para usted a medida que comienza a utilizar Cloud Manager.

## Aplicación {#application}

Y la aplicación es el conjunto de personalizaciones y configuraciones creadas por un cliente para adaptar el subyacente [solución](#solution) (como AEM Sites o AEM Assets) para sus casos de uso y necesidades específicos. Una aplicación es una unidad lógica que puede estar compuesta por varios [artefactos.](#artifact)

Una aplicación de ejemplo es la ficción [Aplicación de estilo de vida WKND.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=es)

## Artefacto {#artifact}

Un artefacto es una unidad implementable y es el resultado de algún proceso de compilación que transforma el código fuente en una sola unidad. Por ejemplo, un archivo .zip que contenga el código fuente.

## Repositorio de artefactos {#artifact-repository}

Un repositorio de artefactos es una ubicación de almacenamiento en la que el cliente es específico [artefactos](#artifact) se guardan y se protegen.

## creación {#environment}

Un entorno es un único clúster de máquinas virtuales dentro de un [programa.](#program) Por AEM, se compone de una instancia de creación (opcionalmente con una instancia de creación en espera en frío adicional), cero o más instancias de publicación, una o más instancias de Dispatcher y un equilibrador de carga.

## repositorio de Git {#git-repository}

Un repositorio de Git es una ubicación donde el código fuente específico del cliente se almacena y es accesible [usando git.](https://git-scm.com)

## Instancia {#instance}

Una instancia es un servidor virtual específico que ejecuta el AEM [solución.](#solution) Las instancias representan una sola unidad lógica desde la perspectiva de la implementación.

## Organización {#organization}

Una organización es una construcción de Adobe que representa a un cliente empresarial. Una empresa puede tener varias organizaciones en función de cómo se hayan aprovisionado en el sistema Identity Management de Adobe (IMS).

## Canalización {#pipeline}

Una canalización es un conjunto de pasos de implementación que se ejecutan en secuencia.

## Producto {#product}

Un producto es un conjunto específico de funcionalidades dentro de un [solución](#solution) con licencia de una organización. Different [programas](#program) dentro de una organización puede tener derecho a diferentes conjuntos de productos, por ejemplo, AEM Sites, AEM Assets o AEM Forms.

## Programa {#program}

Un programa es un conjunto de entornos que admiten una agrupación lógica de iniciativas de clientes, que generalmente corresponden a un contrato de nivel de servicio adquirido (SLA). Cada programa tiene exactamente un entorno de producción y puede tener muchos entornos que no sean de producción.

## Solución {#solution}

Una solución es uno de los Adobes [!UICONTROL Experience Cloud] soluciones. Por ejemplo, Adobe Experience Manager, Adobe Target o Adobe Analytics.

## Etapa {#step}

Un paso es un conjunto de instrucciones configurado que logra alguna unidad de trabajo como componente básico de un [canalización.](#pipeline)
