---
title: Administrar sus entornos
seo-title: Administrar sus entornos
description: nulo
seo-description: Siga esta página para ver la lista de entornos de producción y no producción que se utilizan para configurar y ejecutar la canalización CI/CD en Cloud Manager.
uuid: 04 e 67572-11 db -4 d 5 d-acf 3-fd 7 f 644 a 95 f 0
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c 5 b 39 de 2-3 a 9 b -437 f -98 e 8-e 6 e 6249 a 5 b 3 a
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Administrar sus entornos {#manage-your-environments}

La página **Información general** de Cloud Manager incluye el mosaico **Entornos** que enumera todos los entornos de AEM gestionados.

Cada uno de los entornos enumerados muestra su estado asociado.

![](assets/Manage_Environments1.png)

## Acceso a entornos en el Administrador de nube {#accessing-environments-in-cloud-manager}

El mosaico **Entornos** muestra los entornos Producción y Etapa aprovisionados en el programa junto con el estado.

El estado es el estado de potencia resumida entre los nodos del entorno. Es verde si todos los nodos se están ejecutando, rojo si se detiene incluso un nodo, azul si incluso aparece un nodo y amarillo si un nodo tiene un estado de energía no disponible (en este orden de prioridad).

![](assets/manage_environments-screen2.png)

### Entornos {#environments}

Haga clic **en Administrar** para mostrar la pantalla **Entornos** .

La pantalla **Entornos** muestra una tarjeta para los entornos *Producción* y *Etapa* (según corresponda) en el programa. El nombre del entorno se ve encima de cada tarjeta. La tarjeta incluye una tabla de nodos en el entorno junto con el tamaño de la camiseta de la cpu, el almacenamiento, la región y el estado.

>[!NOTE]
>
>**El estado STATUS** del nodo representa el estado de energía del VM y no refleja el estado de AEM en el servidor. El estado puede estar **en ejecución** (círculo verde), **Detenido** (círculo rojo), **Aparecer** (círculo azul) o **No disponible** (círculo amarillo).

![](assets/Manage_Environments2.png)
