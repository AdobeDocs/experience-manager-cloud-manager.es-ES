---
title: Administración de entornos
description: Aprenda a utilizar Cloud Manager para administrar sus entornos.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 80f8707e00357f5a08dd835b846c9ee610f3e573
workflow-type: ht
source-wordcount: '263'
ht-degree: 100%

---


# Administración de entornos {#managing-environments}

Aprenda a utilizar Cloud Manager para administrar sus entornos.

## Página Información general {#overview-page}

La página **Información general** de Cloud Manager incluye el mosaico **Entornos** que enumera todos los entornos de AEM administrados.

Cada uno de los entornos enumerados muestra su estado asociado.

![Página Información general](/help/assets/Manage-Environ-Overview.png)

## Mosaico Entornos {#environments-tile}

El mosaico **Entornos** muestra los entornos de producción y ensayo aprovisionados en el programa junto con el estado.

El estado es el resultado de la energía resumido en los nodos del entorno en el siguiente orden de prioridad.

* Verde: todos los nodos se están ejecutando
* Rojo: están detenidos uno o más nodos.
* Azul: uno o más nodos se están acercando.
* Amarillo: uno o varios nodos tienen un estado de alimentación no disponible.

![Mosaico Entornos](/help/assets/Environments-card-new.png)

## Administración de entornos {#managing-environments-with-cloud-manager}

En el mosaico **Entornos**, haga clic en **Administrar** para mostrar la pantalla **Entornos**.

La pantalla **Entornos** muestra una tarjeta para los entornos de producción y ensayo (según corresponda) de su programa. El nombre del entorno se muestra encima de cada tarjeta. La tarjeta incluye una tabla de nodos en el entorno junto con el tamaño de la CPU, el almacenamiento, la región y el estado.

>[!NOTE]
>
>El **ESTADO** del nodo representa el estado de energía de la VM y no refleja el estado de AEM en el servidor. El estado puede ser el siguiente:

* Verde: en ejecución
* Rojo: detenido
* Azul: próximamente
* Amarillo: no disponible

![Pestaña Entornos](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Si necesita los registros de entorno, se pueden solicitar a través de su ingeniero de éxito del cliente.

## Tutorial de vídeo {#video-tutorial}

Este vídeo proporciona información general sobre los entornos de Cloud Manager que están compuestos por instancias AEM de creación, publicación y Dispatcher.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)
