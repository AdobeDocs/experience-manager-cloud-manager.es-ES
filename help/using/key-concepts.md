---
title: Conceptos clave
seo-title: Conceptos clave
description: Esta página enumera los términos clave asociados con Cloud Manager.
seo-description: Siga esta página para comprender los términos clave asociados con Cloud Manager.
uuid: 2a37810b-98f8-4f01-90de-1e52c754ad16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introducción
discoiquuid: b702dfc0-3534-4d90-af19-8559d8baf6a6
translation-type: tm+mt
source-git-commit: aa4ff4eb2f3292fe4cb0baf8087b4d0213443cf4

---


# Conceptos clave {#key-concepts}

En esta página se describe una terminología básica utilizada en Cloud Manager. Le recomendamos encarecidamente que lea esta página antes de revisar el resto de la documentación de Cloud Manager.

**Aplicación** Conjunto de personalizaciones y configuraciones creadas por un cliente (o su cliente) para adaptar la solución subyacente a sus necesidades y casos de uso específicos. Una aplicación es una unidad lógica que puede estar compuesta de varios artefactos.

Por ejemplo, *We.Retail*.

**Artefacto** Unidad desplegable. Resultado de un proceso de compilación que transforma el código fuente en una sola unidad. Por ejemplo, un archivo Zip que contiene el código fuente.

**Repositorio** de artefactos Ubicación de almacenamiento en la que se guardan y protegen los artefactos específicos del cliente.

**Entorno** Un único grupo de máquinas virtuales dentro de un programa. Para AEM, se compone de una instancia de autor (opcionalmente con una instancia de autor en espera en frío adicional), cero o más instancias de publicación, una o más instancias de despachante y un equilibrador de carga.

**Repositorio** Git Ubicación en la que se almacena el código fuente específico del cliente, accesible mediante el protocolo Git.

**Instancia** Un servidor virtual específico que ejecuta la solución AEM. Las instancias representan una sola unidad lógica desde la perspectiva de la implementación.

**Organización** de construcción de Adobe que representa a un cliente de Enterprise. Una empresa puede tener varias organizaciones en función de cómo se aprovisionaron originalmente en el sistema de gestión de identidades de Adobe.

**Canalización** Conjunto de pasos de implementación que se ejecutan de forma secuencial.

**Producto** Un conjunto específico de funcionalidades dentro de una solución con licencia de una organización. Diferentes programas dentro de una organización pueden tener derecho a diferentes conjuntos de productos. Por ejemplo, Sitios, Recursos de formularios.

**Programa** Conjunto de entornos que admiten una agrupación lógica de iniciativas de clientes, que generalmente corresponden a un contrato de nivel de servicio (SLA) adquirido. Cada programa tiene exactamente un entorno de producción y puede tener muchos entornos que no son de producción.

**Solución** Una de las soluciones de Adobe [!UICONTROL Experience Cloud] . Por ejemplo, Adobe Experience Manager, Adobe Target o Adobe Analytics.

**Paso** Un conjunto de instrucciones configurado que logra alguna unidad de trabajo, bloque de creación de una tubería.
