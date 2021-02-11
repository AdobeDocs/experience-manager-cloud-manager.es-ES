---
title: Administrar los entornos
seo-title: Administrar los entornos
description: Más información sobre el entorno de Cloud Manager
seo-description: Siga esta página para vista de la lista de entornos de producción y no de producción que se utilizan para configurar y ejecutar el canalizador de CI/CD en Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
translation-type: tm+mt
source-git-commit: 2dda85baa5e7ed9bfd8933df3580ec6fc3c210fd
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 3%

---


# Administrar los entornos {#manage-your-environments}

La página **Información general** de Cloud Manager incluye el mosaico **Entornos** que lista todos los entornos de AEM administrados.

Cada uno de los entornos de la lista muestra su estado asociado.

![](assets/Manage-Environ-Overview.png)

## Tutorial de vídeo {#video-tutorial}

### Información general del Entorno del Administrador de nube {#environ-video}

El siguiente vídeo proporciona información general sobre los Entornos de Cloud Manager compuestos por instancias de AEM Author, AEM Publish y Dispatcher.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

## Acceso a Entornos en Cloud Manager {#accessing-environments-in-cloud-manager}

El mosaico **Entornos** muestra los entornos Producción y Escenario aprovisionados en el programa junto con el estado.

El estado es el estado de energía resumido en los nodos del entorno. Es verde si todos los nodos se están ejecutando, rojo si se detiene un nodo, azul si se va a abrir un nodo y amarillo si incluso un nodo tiene un estado de energía no disponible (en este orden de prioridad).

![](assets/Environments-card-new.png)

### Entornos {#environments}

Haga clic en **Administrar** para mostrar la pantalla **Entornos**.

La pantalla **Entornos** muestra una tarjeta para los entornos *Producción* y *Fase* (según corresponda) del programa. El nombre del entorno se muestra encima de cada tarjeta. La tarjeta incluye una tabla de nodos en el entorno junto con el tamaño de la camiseta de la CPU, el almacenamiento, la región y el estado.

>[!NOTE]
>
>El **ESTADO** del nodo representa el estado de energía de la VM y no refleja el estado de AEM en el servidor. El estado puede ser **En ejecución** (círculo verde), **Detenido** (círculo rojo), **Próximos** (círculo azul) o **No disponible** (círculo amarillo).

![](assets/Environments-tab.png)
