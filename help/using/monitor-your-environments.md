---
title: Monitorear sus entornos
seo-title: Monitorear sus entornos
description: nulo
seo-description: Siga esta página para obtener información sobre la supervisión del sistema en el Administrador de nube que se realiza observando las instancias individuales dentro de un entorno y rastreando una variedad de métricas para cada instancia.
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Monitoreo del sistema {#system-monitoring}

La supervisión del sistema se [!UICONTROL Cloud Manager] realiza observando las instancias individuales dentro de un entorno y rastreando una variedad de métricas para cada instancia. Cada métrica tiene dos umbrales definidos: un umbral *de advertencia* y un umbral *crítico*.

Si una métrica está en el umbral crítico, se considera que está en un estado crítico; si una métrica está sobre el umbral de advertencia (pero por debajo de su umbral crítico), se considera que está en estado de advertencia. Los umbrales son establecidos por Adobe Managed Services y se pueden visualizar en [!UICONTROL Cloud Manager]. En la mayoría de los casos, los umbrales son coherentes entre los clientes, pero existen casos en los que Adobe gestiona los umbrales para que coincidan con los requisitos específicos de los clientes. Las preguntas sobre los umbrales deberían dirigirse a su ingeniero de éxito de clientes (CSE).

## Navegación al monitoreo del sistema {#navigating-system-monitoring}

La navegación a la función Monitoreo del sistema se puede realizar de dos maneras.

1. Inicie sesión en **los servicios gestionados: página** de aterrizaje de programas.

   ![](assets/ProgramLanding.png)

1. Haga clic en el tercer icono de la tarjeta de programa.

   ![](assets/program-card.png)

   *O bien*,

* Vaya a la página **de aterrizaje Monitoreo** del sistema a través del elemento **de** menú de navegación global Informes dentro [!UICONTROL Cloud Manager]de.


## Página Información general del sistema {#system-monitoring-overview-page}

La página Información general sobre supervisión del sistema enumera los entornos monitoreados en el programa e informa sobre su estado de alto nivel en cuatro categorías diferentes:

* **Host**
* **Almacenamiento**
* **Red**
* **Aplicación**

El estado de cada categoría es un resumen de métricas individuales: si alguna métrica en una categoría está en el estado crítico, toda la categoría está en un estado crítico para el propósito de la página de información general. La misma resumen puede verse a nivel de entorno y a nivel de instancia.

![](assets/Reports.png)

>[!NOTE]
>
>De forma predeterminada, al navegar a esta página, las instancias de entorno de producción son visibles, pero también se pueden abrir otros entornos.

## Detalle de monitoreo del sistema {#system-monitoring-detail}

Para ver los detalles de métricas específicas, puede hacer clic en una de las categorías de la navegación izquierda o hacer clic en uno de los indicadores de categoría para una instancia específica. Cada página de detalles muestra una serie de gráficos de las métricas dentro de esa categoría. Puede ver las métricas de todas las instancias en un entorno o en una instancia específica. Puede cambiar entre el entorno y las instancias utilizando los cuadros desplegables en la esquina superior derecha.

![](assets/System_Monitoring1.png)

La navegación a la izquierda mostrará las métricas disponibles dentro de la categoría seleccionada actualmente para la cual hay datos para el entorno y las instancias actualmente seleccionados.

![](assets/System_Monitoring2.png)

Un gráfico individual mostrará el estado y un gráfico de los datos a lo largo del tiempo junto con los umbrales. Si se muestran varias instancias, los datos de cada instancia estarán en una serie separada.

![](assets/System-Monitoring3.png)

La serie individual puede ocultarse en un gráfico haciendo clic en la serie de la leyenda.
Por ejemplo, si hace clic en la serie de umbral de advertencia, solo verá el umbral crítico.

![](assets/System_Monitoring4.png)

### Definiciones de métricas {#metric-definitions}

**Host**

* Cargar por núcleo: el número de proceso que ejecuta la CPU o que tiene un estado de espera promedio sobre uno (load 1), cinco (load 5) y quince (load 15) minutos de minutos.
* Recuento de procesos: el número de procesos abiertos actualmente.
* Recuento de usuarios: el número de usuarios con una sesión shell activa.
* Uso de memoria: el porcentaje de memoria del sistema asignada actualmente.
* Memoria JVM (heap): el tamaño (en Megabytes) del área de Java asignada.
* Espacio de generación antigua: el porcentaje de memoria antigua de JVM asignada actualmente.

**Red**

* Comprobación del puerto de CQ: Tiempo de respuesta en segundos para acceder al puerto AEM o Dispatcher. Existen diferentes métricas para autor, publicación y dispatcher.

**Almacenamiento**

* Espacio en disco: Espacio en disco utilizado (en Megabytes) para cada punto de montaje del host. Existen diferentes métricas para cada punto de montaje. Como mínimo, verá métricas para &quot;/&quot; y &quot;/&quot;, pero las métricas de punto de montaje adicionales pueden estar disponibles en función de la configuración de instancia específica.
* Tamaño de carpeta: Tienda de segmentos de AEM: Espacio en disco utilizado (en Gigabytes) para la tienda de segmentos de AEM.

**Aplicación**

* Agente de replicación: Tiempo, en segundos, para un evento de replicación de prueba. Existen métricas independientes para cada agente de replicación.
* Despachante de despachante: El número de elementos que hay actualmente en la cola de vaciado.

## Informes SLA {#sla-reporting}

Los clientes pueden ver el rendimiento de su entorno de producción de AEM en relación con su contrato de nivel de servicio (SLA) contractual. Esta opción está disponible a través de un submenú en la pantalla Informes.
Por ejemplo: el gráfico de abajo muestra el resultado mensual del SLA para 2018.

![](assets/sla-reporting1.png)

Al igual que con los gráficos de monitoreo del sistema, el desplazamiento sobre un punto de datos muestra los valores específicos de ese mes.

![](assets/sla-reporting2.png)

La sección Análisis de eventos de este gráfico muestra el conjunto de incidentes que se produjeron para el programa durante el año seleccionado. Cada incidente tiene un intervalo de tiempo, una causa y un conjunto de comentarios.

![](assets/sla-reporting3.png)

## Métricas de SLA {#sla-metrics}

* **Contrato de autor**: Este es el SLA definido en su contrato con Adobe Managed Services para el nivel de autor.

* **SLA Author Author**: Es el tiempo de actividad medido de los incidentes de factorización del nivel de autor de producción causado por Adobe o nuestros proveedores.

* **SLA del autor**: Es la hora uptime medida del nivel de autor que ignora el tiempo de inactividad programado como ventanas de mantenimiento.

* **Contrato de usuario final**: Este es el SLA definido en su contrato con Adobe Managed Services para el nivel de publicación.

* **SLA del usuario final AMS**: Es el tiempo de actividad medido de los incidentes de factorización de nivel de publicación de producción provocados por Adobe o nuestros proveedores.

* **SLA del usuario final**: Es la hora uptime medida del nivel de publicación que ignora el tiempo de inactividad programado como ventanas de mantenimiento.