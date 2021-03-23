---
title: Notas de la versión 2019.9.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.9.0
description: Siga esta página para obtener información sobre la versión 2019.9.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.9.0 de AEM Cloud Manager.
feature: Información de la versión
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 5%

---

# Notas de la versión 2019.9.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.9.0 actualiza los criterios de prueba de seguridad, agrega gráficos de monitorización descargables y corrige algunos problemas de uso notificados por los clientes.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2019.9.0 de [!UICONTROL Cloud Manager] es el 12 de septiembre de 2019.

## Novedades {#whats-new}

* La categorización de la comprobación de estado del filtro de referente de Sling se ha cambiado de Crítico a Importante.
* La categorización de la comprobación de estado de configuración del Administrador de biblioteca HTML se ha cambiado de Crítico a Importante.
* Ahora se pueden descargar los gráficos de monitorización. Consulte [Supervisar los entornos](monitor-your-environments.md) para obtener más información.
* Si un programa no tiene un entorno de AEM de producción, al hacer clic en la tarjeta de programa de la página de aterrizaje, accederá a la página de información general de Cloud Manager y no se generará un cuadro de diálogo de error.
* La tarjeta **Configuración de canalización** de la página **Información general** se ha cambiado a **Configuración de canalización de producción**.
* Los botones de opción Comportamiento de error importante se han eliminado de las canalizaciones de solo calidad de código.
* La página **Activity** ahora muestra el nombre de la canalización para cada ejecución.
* La página de ejecución ahora muestra el nombre de la canalización.
* El cuadro de diálogo Resumen de calidad del código ahora muestra una descripción para cada clasificación.

## Corrección de errores {#bug-fixes}

* Algunos usuarios no podían ver los detalles de una ejecución mientras esperaban la aprobación.
* En la página **Información general**, el margen derecho no era coherente.
* El contenedor de compilación podría quedarse sin memoria en proyectos grandes.
* En determinadas circunstancias, la regla OakPAL de BannedPaths no identificó el contenido instalado en /libs.
* Cuando se rechazó una puerta de calidad, el encabezado del cuadro de diálogo seguía mostrando *Parally Passed*.

## Problemas conocidos {#known-issues}

* La descarga de gráficos de monitorización no está disponible en Safari.
