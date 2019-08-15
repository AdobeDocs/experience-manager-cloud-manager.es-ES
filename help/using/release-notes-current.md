---
title: Notas de la versión de 2019.8.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.8.0
description: Siga esta página para obtener información sobre la versión 2019.8.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.8.0 de AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 365cd6dfe65059c0c529f774bbcda946d47b0db5

---

# Notas de la versión de 2019.8.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.8.0 añade compatibilidad con paquetes de contenido creados selectiva, mejora el rendimiento de la compilación y corrige diversos errores menores.

## Fecha de versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2019.8.0 es el 19 de agosto de 2019.

## Novedades {#whats-new}

* Nueva interfaz de línea de comandos a la API de Cloud Manager, con tecnología de [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* Los paquetes de contenido específicos generados por la compilación pueden declararse como skippable y no se implementarán. Consulte ***Omitir la sección de paquetes*** de contenido en [Crear un proyecto de aplicación AEM](create-an-application-project.md) para obtener más detalles.
* El conjunto de dependencias precargadas en el contenedor de compilación se ha modificado para evitar algunas solicitudes de red innecesarias.
* Se ha mejorado el mensaje de la página de información general de ciertos programas configurados incorrectamente.

## Corrección de errores {#bug-fixes}

* Al acceder a los informes SLA, el año predeterminado era 2018, no 2019.
* Para los nombres de entorno largos, el selector de entorno de la pantalla Informes no se incrementaba correctamente.
* La ***regla de calidad del código configandinstallshouldonlycontainosginodes*** generaba falsos positivos cuando se utilizaba el componente Sling Rewriter.
* La ***regla de calidad del código configandinstallshouldonlycontainosginodes*** produjo falsos positivos para ciertas estructuras de ruta poco comunes.
* Es posible que los clientes de solo recursos no hayan sido capaces de navegar a sus entornos AEM de forma consistente.
* [!UICONTROL Create a Branch and Project] El cuadro de diálogo procesado de forma distinta a los distintos exploradores.
