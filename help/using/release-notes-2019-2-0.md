---
title: Notas de la versión de 2019.2.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.2.0
description: Siga esta página para obtener información sobre la versión 2019.2.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.2.0 de AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 98395c4413b1b6bfbb3a565388ffa32dc3880dff

---


# Notas de la versión de 2019.2.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.2.0 incorpora una nueva función de supervisión del sistema. Esto permite a los clientes ver el estado de sus entornos de servicios gestionados de Adobe a nivel de sistema.


## Fecha de lanzamiento {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2019.2.0 es el 21 de febrero de 2019.

## Novedades {#whats-new}

* Nueva función de supervisión del sistema. Consulte [Monitoreo de entornos](monitor-your-environments.md) para obtener más información.
* El módulo de despachante en proyectos generados por asistente ahora contiene un archivo README.
* Se ha mejorado el orden de clasificación de los problemas de análisis de código para que coincidan con la prioridad del problema.
* Ahora, las instancias de la fase siempre se restauran en el equilibrador de carga, incluso en caso de un error de implementación.
* Hay una nueva función de desarrollador de API disponible en Admin Console que permite otorgar a usuarios específicos permiso para crear integraciones en la consola de Adobe I/O. Consulte [Administrar desarrolladores](https://www.adobe.com/go/aac_api_prod_learn) para obtener más información.
* La versión del Arquetipo Maven se actualizó a la versión 16.
* La versión de Maven se ha actualizado a la versión 3.6.0.

## Corrección de errores {#bug-fixes}

* En algunas circunstancias, las tuberías no se ejecutarían cuando el entorno de destino estaba alojado en Azure.
* El orden de los entornos era incoherente.
* La prueba de rendimiento puede fallar cuando se descubren rutas de página que contienen un carácter de coma.
* Cuando se inició una ejecución de canalización desde la interfaz de usuario web, el botón Atrás del explorador no funcionaba correctamente.
* Los vínculos Más información de la página Información general no abrieron una nueva ficha.
* Al cargar una miniatura de programa, es posible que no esté visible inmediatamente.
* En algunos casos, el análisis de código falló debido a la configuración específica del proyecto.
* El vínculo Más información de la tarjeta de oleoductos que no son de producción se encontraba en la ubicación incorrecta.
* Cuando se anulaba una puerta de calidad, el estado se mostraba de forma incoherente.
* Los clientes que utilizan topologías de espera en frío recibieron resultados incorrectos para las pruebas de seguridad.
* Al crear un nuevo proyecto con el asistente, no era posible crear una rama que contuviera el carácter de guión.

## Problemas conocidos {#known-issues}

* Cuando se actualizan los datos de supervisión, se muestran todas las series ocultas.
* Los clientes que deseen ver los informes de SLA existentes deberán desplazarse manualmente hasta la próxima versión.

   Para formular esta URL, siga el patrón (`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html`); por ejemplo, si la URL de Experience Cloud es (`https://weretailprod.experiencecloud.adobe.com`), entonces la URL de los informes SLA es (`https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`).

   Se espera que esto se resuelva en la próxima versión con la disponibilidad de informes de SLA dentro [!UICONTROL Cloud Manager].
