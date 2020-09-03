---
title: Notas de la versión 2020.8.0
seo-title: Notas de la versión de AEM Cloud Manager para 2020.8.0
description: Siga esta página para obtener información sobre la versión 2020.8.0 de Cloud Manager
seo-description: Siga esta página para obtener información sobre la versión 2020.8.0 de AEM Cloud Manager
translation-type: tm+mt
source-git-commit: c1d07c95088a279376ef495001a5165c7e459642
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 6%

---

# Notas de la versión 2020.8.0 {#release-notes-for}

La siguiente sección describe las Notas de revisión generales de la versión 2020.8.0 [!UICONTROL Cloud Manager] .

## Fecha de la versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2020.8.0 es el 06 de agosto de 2020.

## Novedades {#whats-new}

Ahora se admiten repositorios privados de Maven enlazados a autenticación.

## Corrección de errores {#bug-fixes}

* Algunos complementos innecesarios y no deseados de SonarQube se estaban ejecutando como parte de la exploración de calidad del código.

* En la página de ejecución de la canalización, el nombre de la ramificación tenía un formato incorrecto.

* Al implementar en topologías con una sola publicación, un único despachante y un autor en espera en frío, el despachante se eliminaba erróneamente del equilibrador de carga.

* En algunos casos, las ejecuciones de los trámites terminados no se registraban correctamente por haberse completado, lo que impedía la ejecución de los nuevos trámites.

* Ocasionalmente, las ejecuciones por tuberías se *quedaban atascadas* debido a problemas de comunicación interna.

* La información sobre herramientas de las tarjetas de programa no era coherente.

* Había una discordancia de color en la página **Información general** .

* La prueba de rendimiento de sitios ahora admite el uso opcional de la autenticación.

* Las memorias caché de despachante para instancias de autor se vacian automáticamente cuando las configuraciones de despachante se implementan a través de Cloud Manager.

