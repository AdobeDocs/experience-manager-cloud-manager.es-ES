---
title: Administrar los entornos
seo-title: Administrar los entornos
description: Descubra el entorno de Cloud Manager
seo-description: Siga esta página para ver la lista de entornos de producción y no de producción que se usan para configurar y ejecutar la canalización de CI/CD en Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
feature: Environments
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 4%

---


# Administrar los entornos {#manage-your-environments}

La página **Información general** de Cloud Manager incluye el mosaico **Entornos** que enumera todos los entornos de AEM administrados.

Cada uno de los entornos enumerados muestra su estado asociado.

![](assets/Manage-Environ-Overview.png)

## Tutorial de vídeo {#video-tutorial}

### Descripción general del entorno de Cloud Manager {#environ-video}

El siguiente vídeo proporciona información general sobre los entornos de Cloud Manager compuestos por instancias de AEM Author, AEM Publish y Dispatcher.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

## Acceso a los entornos en Cloud Manager {#accessing-environments-in-cloud-manager}

El mosaico **Environments** muestra los entornos de producción y fase aprovisionados en el programa junto con el estado .

El estado es el estado de alimentación resumido en los nodos del entorno. Es verde si todos los nodos se están ejecutando, rojo si incluso se detiene un nodo, azul si aparece incluso un nodo y amarillo si incluso un nodo tiene un estado de alimentación no disponible (en este orden de prioridad).

![](assets/Environments-card-new.png)

### Entornos {#environments}

Haga clic en **Administrar** para mostrar la pantalla **Entornos**.

La pantalla **Environments** muestra una tarjeta para entornos *Production* y *Stage* (según corresponda) en el programa. El nombre del entorno se muestra encima de cada tarjeta. La tarjeta incluye una tabla de nodos en el entorno junto con el tamaño de la camiseta de la cpu, el almacenamiento, la región y el estado.

>[!NOTE]
>
>El **STATUS** del nodo representa el estado de energía de la VM y no refleja el estado de AEM en el servidor. El estado puede ser **Running** (círculo verde), **Stopped** (círculo rojo), **Coming up** (círculo azul) o **Unavailable** (círculo amarillo).

![](assets/Environments-tab.png)
