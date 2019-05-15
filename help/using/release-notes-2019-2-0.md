---
title: Notas de la versión de 2019.2.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.2.0
description: Siga esta página para obtener información sobre la versión 2019.2.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.2.0 de AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notas de la versión de 2019.2.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.2.0 incorpora una nueva función de supervisión del sistema. Esto permite a los clientes ver el estado de los entornos de servicios gestionados de Adobe a nivel de sistema.


## Fecha de versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2019.2.0 es el 21 de febrero de 2019.

## Novedades {#whats-new}

* Nueva función de supervisión del sistema. Consulte [Monitorear los entornos](monitor-your-environments.md) para obtener más información.
* El módulo de Dispatcher en proyectos generados por el asistente ahora contiene un archivo README.
* La ordenación de orden de los problemas de Digitalización de código se ha mejorado para que coincida con la prioridad de la publicación.
* Ahora, las instancias de Stage siempre se restauran al equilibrador de carga incluso en caso de fallo de implementación.
* Hay una nueva función de Desarrollador de API disponible en la Consola de administración que permite a los usuarios concretos conceder permiso para crear integraciones en la consola de Adobe I/O. Consulte [Administrar desarrolladores](https://www.adobe.com/go/aac_api_prod_learn) para obtener más información.
* La versión del archetype Maven se ha actualizado a la versión 16.
* La versión de Maven se ha actualizado a la versión 3.6.0.

## Corrección de errores {#bug-fixes}

* En algunas circunstancias, los pipeline no se ejecutarían cuando el entorno de destino estaba alojado en Azure.
* El orden de los entornos era incoherente.
* La prueba de rendimiento podría fallar cuando se descubrieron rutas de página que contenían un carácter de coma.
* Cuando se empezó una ejecución del canal desde la interfaz de usuario web, el botón Atrás del explorador no funcionaba correctamente.
* Los vínculos Más información de la página Información general no abrieron una nueva pestaña.
* Al cargar una miniatura de programa, es posible que no se haya visible inmediatamente.
* En algunos casos, la digitalización de código falló debido a la configuración específica del proyecto.
* El vínculo Más información de la tarjeta de canales sin producción fue a la ubicación equivocada.
* Cuando se anulaba la marca de calidad, el estado se mostraba de forma inconsistente.
* Los clientes que utilizan topologías de emergencia bajas recibieron resultados incorrectos en las pruebas de seguridad.
* Al crear un proyecto nuevo mediante el asistente, no era posible crear una rama que contenga el carácter de guión.

## Problemas conocidos {#known-issues}

* Cuando se actualizan los datos, cualquier serie oculta se rellena.
* Los clientes que deseen ver sus informes de SLA existentes deberán navegar manualmente hasta la próxima versión.

   Para realizar esta URL, siga el patrón (`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html`), por ejemplo, si la dirección URL de Experience Cloud es (`https://weretailprod.experiencecloud.adobe.com`), su URL de informes SLA es (`https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`).

   Se espera resolver este problema en la próxima versión con la disponibilidad de los informes SLA dentro [!UICONTROL Cloud Manager].
