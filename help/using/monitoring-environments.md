---
title: Supervisar entornos
description: Obtenga información sobre cómo monitorizar los entornos en Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 4c4a2688cab8e5c81efa4b7b5e26f3c7b5dc30d6
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 34%

---


# Monitorización de entornos {#monitoring-environments}

Obtenga información sobre cómo monitorizar los entornos en Cloud Manager.

## Umbrales de métrica {#thresholds}

La Monitorización del sistema, en [!UICONTROL Cloud Manager], se lleva a cabo observando las instancias individuales dentro de un entorno y con el seguimiento de una variedad de métricas para cada una. Cada métrica tiene dos umbrales definidos: un umbral *advertencia* y un umbral *crítico*.

Si una métrica supera su umbral de advertencia (pero está por debajo del esencial), se considera que está en estado de advertencia.

Si una métrica supera su umbral esencial, se considera que está en estado crítico.

Adobe Managed Services establece los umbrales, que puede ver en [!UICONTROL Cloud Manager]. En la mayoría de los casos, los umbrales son coherentes entre los clientes, pero, en algunos casos, Adobe Managed Services los edita para adaptarlos a los requisitos específicos del cliente. Dirija cualquier pregunta que tenga acerca de los umbrales a su ingeniero de éxito del cliente (Customer Success Engineer, CSE).

## Monitorización del sistema de acceso {#accessing-system-monitoring}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) y seleccione la organización y programa adecuados.

1. Haga clic en el botón de los tres puntos del programa que desea supervisar.
1. En el menú, bajo el encabezado **Administrar**, haga clic en **Mostrar supervisión** para abrir la página **Informes** que muestra información de supervisión del sistema.

   ![Configuración](/help/assets/first-timea1.png)

.

## Información general de monitorización del sistema {#system-monitoring-overview}

La sección **Monitorización del sistema** de la página **Informes** enumera los entornos supervisados en el programa. Informa sobre su estado de salud de alto nivel en las cuatro categorías siguientes:

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

Para ver los detalles de métricas específicas, haga clic en una de las columnas de categoría de una instancia específica o en el título de categoría en el panel de navegación izquierdo. Cada página de detalles muestra una serie de gráficos para las métricas dentro de esa categoría. Puede ver las métricas de todas las instancias de un entorno o de una específica. Puede cambiar entre el entorno y las instancias mediante los cuadros desplegables de la esquina superior derecha.

![Selección del entorno](/help/assets/System_Monitoring1.png)

La navegación de la izquierda muestra las métricas disponibles dentro de la categoría seleccionada actualmente para la que hay datos para el entorno y las instancias seleccionados actualmente.

El gráfico individual muestra el estado y un gráfico de los datos en el tiempo junto con los umbrales. Si se muestran varias instancias, los datos de cada una se muestran en una serie independiente.

![Gráfico de métricas](/help/assets/Monitoring_Graphs1.png)

Las series individuales pueden ocultarse en un gráfico haciendo clic en la serie de la leyenda.
Por ejemplo, si hace clic en la serie de umbrales de advertencia, solo verá el umbral esencial.

![Modificación del gráfico](/help/assets/Monitoring_Graphs2.png)

### Definiciones de métricas {#metric-definitions}

#### Host {#host}

* **Carga por núcleo**: El número de procesos que está ejecutando la CPU. O bien, el número de procesos en cola que están en estado de espera promediado en un período de uno (load1), cinco (load5) y quince (load15) minutos.
* **Recuento de procesos**: El número de procesos abiertos actualmente.
* **Recuento de usuarios**: El número de usuarios con una sesión de shell activa.
* **Uso de memoria**: porcentaje de memoria del sistema asignado actualmente.
* **Memoria JVM**: El tamaño (en megabytes) del montón de Java asignado.
* **Espacio de generación antigua**: Porcentaje de memoria de generación antigua de JVM asignado actualmente.

#### Red {#network}

* AEM **Comprobación de puerto CQ**: Tiempo de respuesta en segundos para acceder al puerto de Dispatcher o de la interfaz de usuario de la interfaz de usuario de la aplicación de acceso a la interfaz de usuario de. Existen diferentes métricas para creación, publicación y Dispatcher.

#### Almacenamiento {#storage}

* **Espacio en disco**: Espacio en disco usado (en megabytes) para cada punto de montaje en el host. Hay diferentes métricas para cada punto de montaje. Como mínimo, hay métricas para `/` y `/mnt`, pero es posible que haya métricas de punto de montaje adicionales disponibles en función de la configuración de instancia específica.
* **Tamaño de carpeta**
* AEM AEM **Almacén de segmentos de**: El espacio en disco utilizado (en gigabytes) para el Almacén de segmentos de la lista de segmentos de la lista de distribución.

#### Aplicación {#application}

* **Agente de replicación**: tiempo (en segundos) para un evento de replicación de prueba
   * Hay métricas independientes para cada agente de replicación.
* **Vaciado de Dispatcher**: El número de elementos que hay actualmente en la cola de vaciado de Dispatcher

## Informes de SLA {#sla-reporting}

Puede ver el rendimiento de su entorno de AEM de producción en relación con el contrato de nivel de servicio (SLA).

El gráfico siguiente muestra los logros mensuales de SLA para 2019.

![Gráfico de SLA de 2018](/help/assets/SLA-Reports-one.png)

Al igual que con los gráficos de monitorización del sistema, si se desplaza por un punto de datos, se muestran los valores específicos de ese mes.

![Sustitución de puntos de datos](/help/assets/SLA-Reports-two.png)

La sección **Análisis de eventos** de este gráfico muestra el conjunto de incidentes que ocurrieron para el programa durante el año seleccionado. Cada incidente tiene un intervalo de tiempo, una causa y un conjunto de comentarios.

![Análisis de eventos](/help/assets/sla-reporting3.png)

## Métricas de SLA {#sla-metrics}

* **Contrato de autor**: el SLA definido en su contrato con Adobe Managed Services para el nivel de autor.
* **SLA de creación de AMS**: tiempo de actividad medido del nivel de creación de producción, incidentes de factorización causados por proveedores o por Adobe.
* **SLA de autor**: tiempo de actividad medido del nivel de creación que ignora el tiempo de inactividad programado, como los períodos de mantenimiento.
* **Contrato de usuario final**: SLA definido en su contrato con Adobe Managed Services para el nivel de publicación.
* **SLA de usuario final de AMS**: los tiempos de actividad medidos del nivel de publicación de producción, los incidentes de factorización causados por proveedores o por Adobe.
* **SLA de usuario final**: el tiempo de actividad medido del nivel de publicación que ignora el tiempo de inactividad programado, como los períodos de mantenimiento.

## Tutorial de vídeo {#video-tutorial}

Este vídeo proporciona información general sobre el uso de los gráficos creados por los informes de Cloud Manager para obtener una vista de los entornos de su programa.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
