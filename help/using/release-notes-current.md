---
title: Notas de la versión de 2019.9.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.9.0
description: Siga esta página para obtener información sobre la versión 2019.9.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.9.0 de AEM Manager.
translation-type: tm+mt
source-git-commit: 548d18f251cf8c4c827d2208fec04cde235ce731

---

# Notas de la versión de 2019.9.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.9.0 añade actualizaciones a la comprobación de estado del filtro Sling Referrer y a los gráficos de monitoreo.

## Fecha de versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2019.9.0 es el 11 de septiembre de 2019.

## Novedades {#whats-new}

* La categorización de la comprobación de estado del Filtro Sling Referrer se ha cambiado de Crítica a Importante.
* La categorización de la comprobación de estado de configuración del Administrador de biblioteca HTML se ha cambiado de Crítica a Importante.
* Ahora se pueden descargar gráficos de monitoreo. Consulte [Monitorear los entornos](monitor-your-environments.md) para obtener más detalles.
* Si un programa no tiene un entorno de AEM de producción, al hacer clic en la tarjeta de programa desde la página de aterrizaje se navega a la página de información general de Cloud Manager, no se producirá un cuadro de diálogo de error.
* La tarjeta de configuración Pipeline de la página Información general se ha retirado a **la Configuración de producción de producción**.
* Los botones de opción de Comportamiento de error importante se han eliminado de los canales de solo calidad del código.
* La página de actividad muestra ahora el nombre del canal para cada ejecución.
* La página de ejecución ahora muestra el nombre del canal.
* El cuadro de diálogo de resumen Calidad del código ahora muestra una descripción para cada clasificación.

## Corrección de errores {#bug-fixes}

* Algunos usuarios no podían ver los detalles de ejecución cuando estaba esperando aprobación.
* En la página Información general, el margen derecho no era coherente.
* El contenedor de compilación podría quedarse sin memoria en proyectos grandes.
* En determinadas circunstancias, la regla bannedpaths oakpal no identificó el contenido instalado en /libs.
* Cuando se rechazaba una puerta de calidad, el encabezado de cuadro de diálogo seguía mostrando "Parcialmente pasado".

## Problemas conocidos {#known-issues}

La descarga de gráficos de monitoreo no está disponible en Safari.
