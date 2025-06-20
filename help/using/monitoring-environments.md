---
title: Supervisar entornos
description: Obtenga información sobre cómo monitorizar los entornos en Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 74%

---


# Supervisar entornos {#monitoring-environments}

Obtenga información sobre cómo monitorizar los entornos en Cloud Manager.

## Umbrales de métrica {#thresholds}

La Monitorización del sistema, en [!UICONTROL Cloud Manager], se lleva a cabo observando las instancias individuales dentro de un entorno y con el seguimiento de una variedad de métricas para cada una. Cada métrica tiene dos umbrales definidos: un umbral de *advertencia* y un umbral *esencial*.

Si una métrica supera su umbral de advertencia (pero está por debajo del esencial), se considera que está en estado de advertencia. 

Si una métrica supera su umbral esencial, se considera que está en estado crítico. 

Adobe Managed Services establece los umbrales, que puede ver en [!UICONTROL Cloud Manager]. En la mayoría de los casos, los umbrales son coherentes entre los clientes, pero, en algunos casos, Adobe Managed Services los modificará para adaptarlos a los requisitos específicos del cliente. Dirija cualquier pregunta que tenga acerca de los umbrales a su ingeniero de éxito del cliente (Customer Success Engineer, CSE).

## Monitorización del sistema de acceso {#accessing-system-monitoring}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) y seleccione la organización y programa adecuados.

1. Haga clic en ![icono Más, puntos suspensivos](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) del programa que desea supervisar.
1. En el menú, en **Administrar**, haga clic en **Mostrar supervisión** para abrir la página **Informes** que muestra información de supervisión del sistema.

   ![Configuración](/help/assets/first-timea1.png)

.

## Información general de monitorización del sistema {#system-monitoring-overview}

La sección **Monitorización del sistema** de la página **Informes** muestra los entornos supervisados en el programa. Informa sobre su estado de salud de alto nivel en las cuatro categorías siguientes:

* Host
* Almacenamiento
* Red
* Aplicación

El estado de cada categoría es un resumen de las métricas individuales. Si alguna métrica de una categoría está en estado esencial, toda la categoría se encuentra en dicho estado para los fines de la página de información general. La misma síntesis se puede ver en el nivel de entorno y de instancia.

![Información general de monitorización del sistema](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>De forma predeterminada, al navegar a esta página, las instancias del entorno de producción están visibles, pero también se pueden ver otros entornos.

## Detalles de monitorización del sistema {#system-monitoring-detail}

Para ver los detalles de las métricas específicas, haga clic en una de las columnas de categoría de una instancia específica o en el título de categoría en la navegación izquierda. Cada página de detalles muestra una serie de gráficos para las métricas dentro de esa categoría. Puede ver las métricas de todas las instancias de un entorno o de una específica. Puede cambiar entre el entorno y las instancias mediante los cuadros desplegables de la esquina superior derecha.

![Selección del entorno](/help/assets/System_Monitoring1.png)

La navegación de la izquierda mostrará las métricas disponibles dentro de la categoría seleccionada actualmente para la que hay datos para el entorno y las instancias que se hayan seleccionado.

El gráfico individual muestra el estado y un gráfico de los datos en el tiempo junto con los umbrales. Si se muestran varias instancias, los datos de cada una estarán en una serie independiente.

![Gráfico de métricas](/help/assets/Monitoring_Graphs1.png)

Las series individuales pueden ocultarse en un gráfico haciendo clic en la serie de la leyenda.
Por ejemplo, si hace clic en la serie de umbrales de advertencia, solo verá el umbral esencial.

![Modificación del gráfico](/help/assets/Monitoring_Graphs2.png)

### Definiciones de métricas {#metric-definitions}

#### Host {#host}

* **`Load Per Core`**: número de procesos que está ejecutando CPU. O bien, el número de procesos en cola que están en estado de espera promediado en un período de uno (load1), cinco (load5) y quince (load15) minutos.
* **P`rocess Count`**: El número de procesos abiertos actualmente.
* **`User Count`**: número de usuarios con una sesión de shell activa.
* **`Memory Usage`**: porcentaje de memoria del sistema asignado actualmente.
* **`JVM Memory`**: tamaño (en megabytes) del montón de Java asignado.
* **`Old Generation Space`**: porcentaje de memoria de generación antigua de JVM asignado actualmente.

#### Red {#network}

* **`CQ Port Check`**: tiempo de respuesta en segundos para acceder al puerto de AEM o Dispatcher. Existen diferentes métricas para creación, publicación y Dispatcher.

#### Almacenamiento {#storage}

* **`Disk Space`**: espacio en disco utilizado (en megabytes) para cada punto de montaje en el host. Hay diferentes métricas para cada punto de montaje. Como mínimo, existen métricas para `/` y `/mnt`, pero es posible que haya métricas de punto de montaje adicionales disponibles en función de la configuración de instancia específica.
* **`Folder Size`**
* **`AEM Segment Store`**: espacio en disco utilizado (en gigabytes) para el almacén de segmentos de AEM.

#### Aplicación {#application}

* **`Replication Agent`**: tiempo (en segundos) para un evento de replicación de prueba
   * Hay métricas independientes para cada agente de replicación.
* **`Dispatcher Flush`**: número de elementos que hay actualmente en la cola de vaciado de Dispatcher

## Creación de informes de SLA {#sla-reporting}

Puede ver el rendimiento de su entorno de AEM de producción en relación con el contrato de nivel de servicio (SLA).

El gráfico siguiente muestra los logros mensuales de SLA para 2019.

![Gráfico de SLA de 2018](/help/assets/SLA-Reports-one.png)

Al igual que con los gráficos de monitorización del sistema, si se desplaza por un punto de datos, se muestran los valores específicos de ese mes.

![Sustitución de puntos de datos](/help/assets/SLA-Reports-two.png)

La sección **Análisis de eventos** bajo este gráfico muestra el conjunto de incidentes que ocurrieron para el programa durante el año seleccionado. Cada incidente tiene un intervalo de tiempo, una causa y un conjunto de comentarios.

![Análisis de eventos](/help/assets/sla-reporting3.png)

## Métricas de SLA {#sla-metrics}

* **`Author Contract`**: el SLA definido en su contrato con Adobe Managed Services para el nivel de Author.
* **`AMS Author SLA`**: tiempo de actividad medido del nivel de creación de producción, incidentes de factorización causados por proveedores o por Adobe.
* **`Author SLA`**: tiempo de actividad medido del nivel de creación que ignora el tiempo de inactividad programado, como los períodos de mantenimiento.
* **`End User Contract`**: el SLA definido en su contrato con Adobe Managed Services para el nivel de publicación.
* **`AMS End User SLA`**: los tiempos de actividad medidos del nivel de publicación de producción, los incidentes de factorización causados por proveedores o por Adobe.
* **`End User SLA`**: tiempo de actividad medido del nivel de publicación que ignora el tiempo de inactividad programado, como los períodos de mantenimiento.

## Tutorial de vídeo {#video-tutorial}

Este vídeo proporciona información general sobre el uso de los gráficos creados por los informes de Cloud Manager para obtener una vista de los entornos de su programa.

>[!VIDEO](https://video.tv.adobe.com/v/34624?captions=spa)
