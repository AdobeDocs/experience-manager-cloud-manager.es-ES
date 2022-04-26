---
title: Administrar los entornos
seo-title: Manage your Environments
description: Descubra el entorno de Cloud Manager
seo-description: Follow this page to view the list of production and non-production environments that are used for setting up and running the CI/CD pipeline in Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
feature: Environments
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 6ff704ec11dd4a5f73d5b5df5721c4fee649527b
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 6%

---

# Administrar los entornos {#manage-your-environments}

>[!NOTE]
>Para obtener información sobre la administración de entornos para Cloud Manager en AEM as a Cloud Service, consulte [here](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=es#using-cloud-manager).

La variable **Información general** La página de Cloud Manager incluye la variable **Entornos** mosaico que enumera todos los entornos de AEM administrados.

Cada uno de los entornos enumerados muestra su estado asociado.

![](assets/Manage-Environ-Overview.png)

## Tutorial de vídeo {#video-tutorial}

### Descripción general del entorno de Cloud Manager {#environ-video}

El siguiente vídeo proporciona información general sobre los entornos de Cloud Manager compuestos por instancias de AEM Author, AEM Publish y Dispatcher.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

## Acceso a entornos en Cloud Manager {#accessing-environments-in-cloud-manager}

La variable **Entornos** mosaico muestra los entornos de producción y fase aprovisionados en el programa junto con el estado .

El estado es el estado de alimentación resumido en los nodos del entorno. Es verde si todos los nodos se están ejecutando, rojo si incluso se detiene un nodo, azul si aparece incluso un nodo y amarillo si incluso un nodo tiene un estado de alimentación no disponible (en este orden de prioridad).

![](assets/Environments-card-new.png)

### Entornos {#environments}

Haga clic en **Administrar** para mostrar el **Entornos** en el Navegador.

La variable **Entornos** pantalla muestra una tarjeta para *Producción* y *Prueba* entornos (según corresponda) en su programa. El nombre del entorno se muestra encima de cada tarjeta. La tarjeta incluye una tabla de nodos en el entorno junto con el tamaño de la camiseta de la cpu, el almacenamiento, la región y el estado.

>[!NOTE]
>
>La variable **ESTADO** del nodo representa el estado de energía de la VM y no refleja el estado de AEM en el servidor. El estado puede ser **Ejecución** (círculo verde), **Detenido** (círculo rojo), **Próximamente** (círculo azul) o **No disponible** (círculo amarillo).

![](assets/Environments-tab.png)

>[!NOTE]
>
>Si necesita los registros de entorno, se pueden solicitar a través de su ingeniero de éxito del cliente.
