---
title: Notas de la versión 2019.12.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.12.0
description: Siga esta página para obtener información sobre la versión 2019.12.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.12.0 de AEM Cloud Manager.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 6%

---


# Notas de la versión 2019.12.0 {#release-notes-for}

En la siguiente sección se describen las notas de la versión generales de la versión [!UICONTROL Cloud Manager] 2019.12.0, y se añaden actualizaciones a la ejecución de la canalización y mejoras a los análisis de calidad del código.
Siga las secciones a continuación para obtener más información.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2019.12.0 de [!UICONTROL Cloud Manager] es el 12 de diciembre de 2019.

## Novedades {#whats-new}

* Los pasos en la ejecución de la canalización ahora muestran la marca de tiempo de finalización para cada paso.
* Los análisis de calidad del código para proyectos que no contienen código Java ahora informan de una tasa de cobertura del 100%.
* Se ha eliminado la comprobación de estado de la configuración de CQ Dispatcher.

## Corrección de errores {#bug-fixes}

* Las fechas no se mostraban correctamente en determinados navegadores.
* En casos excepcionales, la canalización de producción pasaría al paso de aprobación mientras la prueba de rendimiento aún se estaba ejecutando.
* En algunos estados, los botones del área superior de la página de información general no se alinearon correctamente.
* En determinadas circunstancias, los usuarios no autorizados veían un botón para iniciar la canalización, aunque no se podía hacer clic en el botón en sí.
* Los botones de acción para las canalizaciones que no son de producción a veces se mostraban en la ubicación incorrecta.
* Los paquetes con el tipo de nodo granite:Ranking no pudieron analizarse para detectar ciertas violaciones de reglas de calidad.
* Ciertos errores en el proceso de calidad del código se contaban incorrectamente como errores.
* No se pudieron cargar los datos de monitorización para ciertas topologías.
