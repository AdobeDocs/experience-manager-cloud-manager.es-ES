---
title: Monitorización de entornos
description: Obtenga información sobre cómo monitorizar los entornos en Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 5907ca6337d33c26ff19a14bfeb358cd9f7b935d
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---


# Monitorización de entornos {#monitoring-environments}

Obtenga información sobre cómo monitorizar los entornos en Cloud Manager.

## Umbrales de métrica {#thresholds}

Monitorización del sistema en [!UICONTROL Cloud Manager] se realiza observando las instancias individuales dentro de un entorno y rastreando una variedad de métricas para cada instancia. Cada métrica tiene dos umbrales definidos: un umbral de advertencia y un umbral crítico.

Si una métrica supera su umbral crítico, se considera que está en estado crítico. Si una métrica supera su umbral de advertencia (pero está por debajo de su umbral crítico), se considera que está en estado de advertencia. Los umbrales los establece Adobe Managed Services y se pueden visualizar en [!UICONTROL Cloud Manager]. En la mayoría de los casos, los umbrales son coherentes entre los clientes, pero en algunos casos Adobe Managed Services modificará los umbrales para adaptarlos a los requisitos específicos del cliente. Las preguntas sobre los umbrales deben dirigirse a su ingeniero de éxito del cliente (CSE).

## Acceso a la supervisión del sistema {#accessing-system-monitoring}

Siga estos pasos para acceder a Supervisión del sistema.

1. Iniciar sesión en **Managed Services: Programas** página de aterrizaje.

   ![Programas de servicios administrados](/help/assets/ProgramLanding.png)

1. Haga clic en el cuarto icono de la tarjeta del programa.

   ![Configuración](/help/assets/first-timea1.png)


También puede navegar hasta el **Monitorización del sistema** página de aterrizaje a través de **Informes** elemento de menú de navegación global dentro de [!UICONTROL Cloud Manager].

## Información general sobre la supervisión del sistema {#system-monitoring-overview}

La página de información general de Supervisión del Sistema enumera los entornos supervisados en el programa e informa sobre su estado de salud de alto nivel en cuatro categorías diferentes:

* Host
* Almacenamiento
* Red
* Aplicación

El estado de cada categoría es un resumen de métricas individuales. Si alguna métrica de una categoría está en estado crítico, toda la categoría se encuentra en estado crítico para los fines de la página de información general. La misma síntesis se puede ver a nivel de entorno y de instancia.

![Información general sobre la supervisión del sistema](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>De forma predeterminada, al navegar a esta página, las instancias del entorno de producción están visibles, pero también se pueden ver otros entornos.

## Detalles de supervisión del sistema {#system-monitoring-detail}

Para ver los detalles de métricas específicas, puede hacer clic en una de las categorías en la navegación izquierda o en uno de los indicadores de categoría de una instancia específica. Cada página de detalles muestra una serie de gráficos para las métricas dentro de esa categoría. Puede ver las métricas de todas las instancias de un entorno o de una instancia específica. Puede cambiar entre el entorno y las instancias mediante los cuadros desplegables de la esquina superior derecha.

![Seleccionar entorno](/help/assets/System_Monitoring1.png)

La navegación de la izquierda mostrará las métricas disponibles dentro de la categoría seleccionada actualmente para la que hay datos para el entorno y las instancias seleccionados actualmente.

![Monitorización de métricas](/help/assets/System_Monitoring2.png)

Un gráfico individual mostrará el estado y un gráfico de los datos a lo largo del tiempo junto con los umbrales. Si se muestran varias instancias, los datos de cada instancia estarán en una serie independiente.

![Gráfico de métricas](/help/assets/Monitoring_Graphs1.png)

Las series individuales pueden ocultarse en un gráfico haciendo clic en la serie de la leyenda.
Por ejemplo, si hace clic en la serie de umbrales de advertencia, solo verá el umbral crítico.

![Modificar gráfico](/help/assets/Monitoring_Graphs2.png)

### Definiciones de métricas {#metric-definitions}

#### Host {#host}

* **Carga por núcleo**: Número de procesos que están siendo ejecutados por la CPU o que están en estado de espera, con un promedio de un período de 1 (carga1), 5 (carga5) y 15 (carga15) minutos
* **Recuento de procesos**: Número de procesos abiertos actualmente
* **Recuento de usuarios**: El número de usuarios con una sesión de shell activa
* **Uso de memoria**: El porcentaje de memoria del sistema asignado actualmente
* **Memoria JVM**: El tamaño (en megabytes) de la pila de Java asignada
* **Espacio de la vieja generación**: El porcentaje de memoria de generación antigua de JVM asignado actualmente

#### Red {#network}

* **Comprobación de puerto CQ**: El tiempo de respuesta en segundos para acceder al puerto de AEM o Dispatcher
   * Existen diferentes métricas para autor, publicación y Dispatcher.

#### Almacenamiento {#storage}

* **Espacio en disco**: Espacio en disco usado (en megabytes) para cada punto de montaje en el host
   * Hay diferentes métricas para cada punto de montaje.
   * Como mínimo, existen métricas para `/` y `/mnt`, pero es posible que haya métricas de punto de montaje adicionales disponibles en función de la configuración de instancia específica.
* **Tamaño de carpeta**
* **Almacenamiento de segmentos de AEM**: El espacio en disco utilizado (en gigabytes) para el Almacenamiento de segmentos de AEM

#### Aplicación {#application}

* **Agente de replicación**: Tiempo (en segundos) para un evento de replicación de prueba
   * Hay métricas independientes para cada agente de replicación.
* **Vaciado de Dispatcher**: El número de elementos que hay actualmente en la cola de vaciado de Dispatcher

## Creación de informes de SLA {#sla-reporting}

Los clientes pueden ver el performance de su entorno de AEM de producción en relación con su contrato de nivel de servicio (SLA, Service Level Agreement). Esto está disponible a través de un submenú en la **Informes** en el Navegador.

El gráfico siguiente muestra los logros mensuales de SLA para 2018.

![Gráfico de SLA 2018](/help/assets/SLA-Reports-one.png)

Al igual que con los gráficos de monitorización del sistema, si se desplaza por un punto de datos se muestran los valores específicos de ese mes.

![Descarga de puntos de datos](/help/assets/SLA-Reports-two.png)

La variable **Análisis de eventos** en este gráfico se muestra el conjunto de incidentes que ocurrieron para el programa durante el año seleccionado. Cada incidente tiene un intervalo de tiempo, una causa y un conjunto de comentarios.

![Análisis de eventos](/help/assets/sla-reporting3.png)

## Métricas de SLA {#sla-metrics}

* **Contrato de autor**: Este es el SLA definido en su contrato con Adobe Managed Services para el nivel de creación.
* **SLA de autor de AMS**: Este es el tiempo de actividad medido de los incidentes de factorización de nivel de autor de producción causados por el Adobe o nuestros proveedores.
* **SLA de autor**: Este es el tiempo de actividad medido del nivel de creación que ignora el tiempo de inactividad programado, como las ventanas de mantenimiento.
* **Contrato de usuario final**: Este es el SLA definido en su contrato con Adobe Managed Services para el nivel de publicación.
* **SLA de usuario final de AMS**: Este es el tiempo de actividad medido de los incidentes de factorización del nivel de publicación de producción causados por el Adobe o nuestros proveedores.
* **SLA de usuario final**: Este es el tiempo de actividad medido del nivel de publicación que ignora el tiempo de inactividad programado, como las ventanas de mantenimiento.

## Tutorial de vídeo {#video-tutorial}

Este vídeo proporciona información general sobre el uso de los gráficos creados por los informes de Cloud Manager para una vista en los entornos de sus programas.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
