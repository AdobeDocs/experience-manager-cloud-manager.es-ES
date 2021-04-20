---
title: Notas de la versión 2019.8.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.8.0
description: Siga esta página para obtener información sobre la versión 2019.8.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.8.0 de AEM Cloud Manager.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 8%

---

# Notas de la versión 2019.8.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.8.0 añade compatibilidad con paquetes de contenido creados selectivamente, mejora el rendimiento de la compilación y corrige una variedad de errores menores.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2019.8.0 de [!UICONTROL Cloud Manager] es el 19 de agosto de 2019.

## Novedades {#whats-new}

* Nueva interfaz de línea de comandos para la API de Cloud Manager, con tecnología [CLI de Adobe I/O](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* Los paquetes de contenido específicos producidos por la compilación se pueden declarar como omitidos y no se implementarán. Consulte [Omisión de paquetes de contenido](/help/using/setting-up-project.md#skipping-content-packages) para obtener más información.
* El conjunto de dependencias precargadas en el contenedor de compilación se ha modificado para evitar algunas solicitudes de red innecesarias.
* Se ha mejorado el mensaje de la página de información general de ciertos programas mal configurados.

## Corrección de errores {#bug-fixes}

* Al acceder a los informes de SLA, el año predeterminado era 2018, no 2019.
* Para los nombres de entorno largos, el selector de entorno de la pantalla Informes no aumentaba correctamente el tamaño.
* La regla de calidad de código ***ConfigAndInstallShouldOnlyContainOsgiNodes*** producía falsos positivos cuando se utilizaba el componente Sling Rewriter.
* La regla de calidad de código ***ConfigAndInstallShouldOnlyContainOsgiNodes*** produjo falsos positivos para ciertas estructuras de ruta poco comunes.
* Es posible que los clientes solo de activos no hayan podido navegar de forma consistente a sus entornos AEM.
* El cuadro de diálogo Crear una rama y un proyecto se representaba de forma diferente en los distintos navegadores.
