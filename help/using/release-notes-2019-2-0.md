---
title: Notas de la versión 2019.2.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.2.0
description: Siga esta página para obtener información sobre la versión 2019.2.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.2.0 de AEM Cloud Manager.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 4%

---


# Notas de la versión 2019.2.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.2.0 agrega una nueva capacidad de supervisión del sistema. Esto permite a los clientes ver el estado de los entornos de Adobe Managed Services a nivel de sistema.


## Fecha de la versión {#release-date}

La fecha de versión de la versión 2019.2.0 de [!UICONTROL Cloud Manager] es el 21 de febrero de 2019.

## Novedades {#whats-new}

* Nueva función de supervisión del sistema. Consulte [Supervisar los entornos](monitor-your-environments.md) para obtener más información.
* El módulo de Dispatcher en proyectos generados por asistente ahora contiene un archivo README.
* Se ha mejorado la ordenación de los problemas de análisis de código para que coincidan con la prioridad del problema.
* Las instancias de fase ahora siempre se restauran al equilibrador de carga incluso en caso de un error de implementación.
* Hay disponible una nueva función de desarrollador de API en el Admin Console que permite conceder a usuarios específicos el permiso para crear integraciones en la consola de Adobe I/O. Consulte [Administrar desarrolladores](https://www.adobe.com/go/aac_api_prod_learn) para obtener más información.
* La versión del tipo de archivo Maven se actualizó a la versión 16.
* La versión de Maven se actualizó a la versión 3.6.0.

## Corrección de errores {#bug-fixes}

* En algunas circunstancias, las canalizaciones no se ejecutarían cuando el entorno de destino estaba alojado en Azure.
* El orden de los entornos era incoherente.
* Las pruebas de rendimiento podrían fallar cuando se descubren rutas de página que contienen un carácter de coma.
* Cuando se iniciaba una ejecución de canalización desde la interfaz de usuario web, el botón Atrás del explorador no funcionaba correctamente.
* Los vínculos Más información de la página Información general no abrían una pestaña nueva.
* Al cargar una miniatura de programa, es posible que no esté visible inmediatamente.
* En algunos casos, el análisis de código falló debido a la configuración específica del proyecto.
* El vínculo Más información de la tarjeta Canalizaciones que no son de producción iba a la ubicación incorrecta.
* Cuando se anulaba una puerta de calidad, el estado se mostraba de forma incoherente.
* Los clientes que utilizan topologías en espera fría recibieron resultados incorrectos en las pruebas de seguridad.
* Al crear un nuevo proyecto con el asistente, no se podía crear una rama que contuviera el carácter de guión.

## Problemas conocidos {#known-issues}

* Cuando se actualizan los datos de monitorización, cualquier serie oculta se muestra.
* Los clientes que deseen ver sus informes de SLA existentes deberán navegar manualmente hasta la próxima versión.

   Para formular esta dirección URL, siga el patrón (`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html`), por ejemplo, si la dirección URL del Experience Cloud es (`https://weretailprod.experiencecloud.adobe.com`), entonces la dirección URL de los informes de SLA es (`https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`).

   Se espera que esto se resuelva en la próxima versión con la disponibilidad de informes de SLA dentro de [!UICONTROL Cloud Manager].
