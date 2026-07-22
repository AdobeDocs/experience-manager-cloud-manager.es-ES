---
title: Administrar entornos
description: Aprenda a utilizar Cloud Manager para administrar sus entornos.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
TQID: https://experienceleague.adobe.com/Dz3Z5i-gSNSorc7Na74RKgm3e0P9b-3vjVRdJvu6a0c
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 0dde660205ad28bc5924a5cc14404c48a0533ceb
workflow-type: tm+mt
source-wordcount: 261
ht-degree: 57%

---

# Administrar entornos {#managing-environments}

Aprenda a utilizar Cloud Manager para administrar sus entornos.

## Página Información general {#overview-page}

La página **Información general** de Cloud Manager incluye el mosaico **Entornos** que enumera todos los entornos de AEM administrados.

Cada uno de los entornos enumerados muestra su estado asociado.

![Página Información general](/help/assets/Manage-Environ-Overview.png)

## Mosaico Entornos {#environments-tile}

El mosaico **Entornos** muestra los entornos de producción y ensayo aprovisionados en el programa junto con el estado.

El estado es el estado de energía agregado en los nodos de entorno enumerados en orden.

* Verde: todos los nodos se están ejecutando
* Rojo: uno o más nodos están detenidos.
* Azul: se están iniciando uno o más nodos.
* Amarillo: uno o varios nodos tienen un estado de alimentación no disponible.

![Mosaico Entornos](/help/assets/Environments-card-new.png)

## Administrar entornos {#managing-environments-with-cloud-manager}

En el mosaico **Entornos**, haga clic en la fila de cualquier entorno para mostrar la pantalla **Entornos**.

La pantalla **Entornos** muestra cada entorno de producción y ensayo del programa. El nombre del entorno aparece encima de cada tarjeta. La tarjeta incluye una tabla de nodos en el entorno junto con el tamaño de la CPU, el almacenamiento, la región y el estado.

>[!NOTE]
>
>El **ESTADO** del nodo representa el estado de energía de la VM y no refleja el estado de AEM en el servidor. El estado puede ser el siguiente:

* Verde: en ejecución
* Rojo: detenido
* Azul: inicio
* Amarillo: no disponible

![Pestaña Entornos](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Los detalles del entorno, como el nombre, no se pueden cambiar una vez aprovisionados.

>[!NOTE]
>
>Solicite los registros de entorno a través de su representante de éxito del cliente.

## Tutorial de vídeo {#video-tutorial}

Este vídeo proporciona una introducción a los entornos de Cloud Manager que están compuestos por instancias de AEM de creación, publicación y Dispatcher.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

*(3 minutos, 1 segundo)*
