---
title: Notas de la versión 2019.12.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.12.0
description: Siga esta página para obtener información sobre la versión 2019.12.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.12.0 de AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 0fa1fedccb013e82c8df5838a612ce26a1efb7e8

---


# Notas de la versión 2019.12.0 {#release-notes-for}

La siguiente sección describe las Notas de revisión generales de la [!UICONTROL Cloud Manager] versión 2019.12.0 y agrega actualizaciones a la ejecución de la canalización y mejoras a los análisis de calidad del código.
Siga las secciones a continuación para obtener más detalles.

## Release Date {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2019.12.0 es el 12 de diciembre de 2019.

## Novedades {#whats-new}

* Los pasos en la ejecución de la canalización ahora muestran la marca de tiempo de finalización para cada paso.
* Los análisis de calidad del código para proyectos que no contienen código Java ahora informan una tasa de cobertura del código del 100%.
* Se ha eliminado la comprobación de estado de Configuración de CQ Dispatcher.

## Corrección de errores {#bug-fixes}

* Las fechas no se mostraban correctamente en determinados exploradores.
* En casos excepcionales, la canalización de producción pasaría al paso de aprobación mientras la prueba de rendimiento aún se estaba ejecutando.
* En determinados estados, los botones del área superior de la página de información general no estaban correctamente alineados.
* En determinadas circunstancias, los usuarios no autorizados vieron un botón para iniciar la canalización, aunque no se pudo hacer clic en el botón mismo.
* Los botones de acción de las tuberías que no son de producción a veces se mostraban en una ubicación incorrecta.
* Los paquetes con el tipo de nodo granite:Ranking no pudieron analizarse para detectar determinadas violaciones de reglas de calidad.
* Ciertos errores en el proceso de calidad del código se contabilizaron incorrectamente como errores.
* No se pudieron cargar los datos de supervisión para ciertas topologías.
