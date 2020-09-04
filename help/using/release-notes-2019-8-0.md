---
title: Notas de la versión 2019.8.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.8.0
description: Siga esta página para obtener información sobre la versión 2019.8.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.8.0 de AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 2ada697ca21acd0c73dbce2bce3e9481ac50272c
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 7%

---

# Notas de la versión 2019.8.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.8.0 añade compatibilidad con paquetes de contenido creados selectivamente, mejora el rendimiento de la compilación y corrige una serie de errores menores.

## Fecha de la versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2019.8.0 es el 19 de agosto de 2019.

## Novedades {#whats-new}

* Nueva interfaz de línea de comandos para la API de Cloud Manager, con tecnología de la CLI [de E/S de](https://github.com/adobe/aio-cli-plugin-cloudmanager)Adobe.
* Los paquetes de contenido específicos producidos por la compilación pueden declararse como omitidos y no se implementarán. Consulte [Omisión de paquetes](/help/using/setting-up-project.md#skipping-content-packages) de contenido para obtener más información.
* El conjunto de dependencias precargadas en el contenedor de compilación se ha reprocesado para evitar algunas solicitudes de red innecesarias.
* Se ha mejorado el mensaje en la página de información general de ciertos programas incorrectamente configurados.

## Corrección de errores {#bug-fixes}

* Al acceder a los informes SLA, el año predeterminado fue 2018, no 2019.
* Para los nombres de entornos largos, el selector de entornos de la pantalla Informes no aumentaba correctamente el tamaño.
* La regla de calidad del código ***ConfigAndInstallMustOnlyContainOsgiNodes*** producía falsos positivos cuando se utilizaba el componente Sling Rewriter.
* La regla de calidad del código ***ConfigAndInstallMustOnlyContainOsgiNodes*** produjo falsos positivos para ciertas estructuras de ruta poco comunes.
* Es posible que los clientes que solo utilizan recursos no hayan podido navegar de forma consistente hasta sus entornos de AEM.
* El cuadro de diálogo Crear una rama y un proyecto se representaba de forma diferente en los distintos navegadores.
