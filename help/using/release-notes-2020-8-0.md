---
title: Notas de la versión 2020.8.0
seo-title: Notas de la versión de AEM Cloud Manager para 2020.8.0
description: Siga esta página para obtener información sobre la versión 2020.8.0 de Cloud Manager
seo-description: Siga esta página para obtener información sobre la versión 2020.8.0 de AEM Cloud Manager
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 7%

---

# Notas de la versión 2020.8.0 {#release-notes-for}

La siguiente sección describe las notas de la versión generales de la versión [!UICONTROL Cloud Manager] 2020.8.0.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2020.8.0 de [!UICONTROL Cloud Manager] es el 6 de agosto de 2020.

## Novedades {#whats-new}

Ahora se admiten repositorios Maven privados enlazados a autenticación.

## Corrección de errores {#bug-fixes}

* Algunos complementos innecesarios y no deseados de SonarQube se estaban ejecutando como parte del análisis de calidad del código.

* En la página de ejecución de la canalización, el nombre de la rama tenía un formato incorrecto.

* Al implementar en topologías con una sola publicación, un único despachante y un autor en espera en frío, el despachante se eliminaba erróneamente del equilibrador de carga.

* En algunos casos, no se registró con éxito la finalización de las ejecuciones de canalización, lo que impidió nuevas ejecuciones de la canalización.

* Las ejecuciones de canalización ocasionalmente se *atascaran* debido a problemas de comunicación interna.

* La información sobre herramientas de las tarjetas de programa no era coherente.

* Había una discordancia de color en la página **Información general**.

* La prueba de rendimiento de sitios ahora admite el uso opcional de autenticación.

* Las cachés de Dispatcher para instancias de autor se vacian automáticamente cuando las configuraciones de Dispatcher se implementan a través de Cloud Manager.

