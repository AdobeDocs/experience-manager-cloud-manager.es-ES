---
title: Supervisar entornos
description: Obtenga información sobre cómo monitorizar los entornos en Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 53fb666ab6caff7a697d7f1942ce25f2bf27a2ce
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 98%

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
1. En el menú, bajo el encabezado **Administrar**, haga clic en **Mostrar supervisión** para abrir la página **Informes** que muestra información de supervisión del sistema.

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

* **Carga por núcleo**: El número de procesos que está ejecutando la CPU. O bien, el número de procesos en cola que están en estado de espera promediado en un período de uno (load1), cinco (load5) y quince (load15) minutos.
* **Recuento de procesos**: Número de procesos abiertos actualmente
* **Recuento de usuarios**: Número de usuarios con una sesión de contenedor activa.
* **Uso de memoria**: Porcentaje de memoria del sistema asignado actualmente.
* **Memoria JVM**: Tamaño (en megabytes) del montón de Java asignado.
* **Espacio de generación antigua**: Porcentaje de memoria de generación antigua de JVM asignado actualmente.

#### Red {#network}

* **Comprobación de puerto CQ**: Tiempo de respuesta en segundos para acceder al puerto de AEM o Dispatcher. Existen diferentes métricas para creación, publicación y Dispatcher.

#### Almacenamiento {#storage}

* **Espacio en el disco**: Espacio en disco usado (en megabytes) para cada punto de montaje en el host. Hay diferentes métricas para cada punto de montaje. Como mínimo, existen métricas para `/` y `/mnt`, pero es posible que haya métricas de punto de montaje adicionales disponibles en función de la configuración de instancia específica.
* **Tamaño de carpeta**
* **Almacenamiento de segmentos de AEM**: Espacio en disco utilizado (en gigabytes) para el almacenamiento de segmentos de AEM.

#### Aplicación {#application}

* **Agente de replicación**: tiempo (en segundos) para un evento de replicación de prueba
   * Hay métricas independientes para cada agente de replicación.
* **Vaciado de Dispatcher**: Número de elementos que hay actualmente en la cola de vaciado de Dispatcher

## Creación de informes de SLA {#sla-reporting}

Puede ver el rendimiento de su entorno de AEM de producción en relación con el contrato de nivel de servicio (SLA).

El gráfico siguiente muestra los logros mensuales de SLA para 2019.

![Gráfico de SLA de 2018](/help/assets/SLA-Reports-one.png)

Al igual que con los gráficos de monitorización del sistema, si se desplaza por un punto de datos, se muestran los valores específicos de ese mes.

![Sustitución de puntos de datos](/help/assets/SLA-Reports-two.png)

La sección **Análisis de eventos** bajo este gráfico muestra el conjunto de incidentes que ocurrieron para el programa durante el año seleccionado. Cada incidente tiene un intervalo de tiempo, una causa y un conjunto de comentarios.

![Análisis de eventos](/help/assets/sla-reporting3.png)

## Métricas de SLA {#sla-metrics}

* **Contrato de creación**: Este es el SLA definido en su contrato con Adobe Managed Services para el nivel de creación.
* **SLA de creación de AMS**: Este es el tiempo de actividad medido de los incidentes de factorización de nivel de creación de producción causados por Adobe o proveedores.
* **SLA de creación**: El tiempo de actividad medido del nivel de creación que ignora el tiempo de inactividad programado, como los períodos de mantenimiento.
* **Contrato de usuario final**: El SLA definido en su contrato con Adobe Managed Services para el nivel de publicación.
* **SLA de usuario final de AMS**: El tiempo de actividad medido de los incidentes de factorización del nivel de publicación de producción causados por Adobe o proveedores.
* **SLA de usuario final**: El tiempo de actividad medido del nivel de publicación que ignora el tiempo de inactividad programado, como los períodos de mantenimiento.

## Tutorial de vídeo {#video-tutorial}

Este vídeo proporciona información general sobre el uso de los gráficos creados por los informes de Cloud Manager para obtener una vista de los entornos de su programa.

>[!VIDEO](https://video.tv.adobe.com/v/34624?captions=spa)
