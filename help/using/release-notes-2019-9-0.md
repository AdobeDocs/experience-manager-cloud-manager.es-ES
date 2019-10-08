---
title: Notas de la versión de 2019.9.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.9.0
description: Siga esta página para obtener información sobre la versión 2019.9.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.9.0 de AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: de9d2834ffa6c235e580227bd020fb8a0b94d22c

---

# Notas de la versión de 2019.9.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.9.0 actualiza los criterios de prueba de seguridad, agrega gráficos de supervisión descargables y corrige algunos problemas de uso informados por los clientes.

## Fecha de lanzamiento {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2019.9.0 es el 12 de septiembre de 2019.

## Novedades {#whats-new}

* La categorización de la comprobación de estado del filtro de referente de Sling se ha cambiado de Crítico a Importante.
* La categorización de la comprobación de estado de configuración del Administrador de bibliotecas HTML se ha cambiado de Crítico a Importante.
* Ahora se pueden descargar gráficos de monitoreo. Consulte [Monitoreo de entornos](monitor-your-environments.md) para obtener más detalles.
* Si un programa no tiene un entorno de producción de AEM, al hacer clic en la tarjeta del programa desde la página de aterrizaje se desplazará a la página de información general del Administrador de nube, no se generará un cuadro de diálogo de error.
* La **tarjeta de configuración** de canalización de la página **Información general** se ha cambiado a Configuración **de canalización de** producción.
* Los botones de opción Comportamiento de error importante se han eliminado de las canalizaciones solo de calidad de código.
* La página **Actividad** ahora muestra el nombre de la canalización para cada ejecución.
* La página de ejecución ahora muestra el nombre de la canalización.
* El cuadro de diálogo de resumen Calidad del código ahora muestra una descripción para cada clasificación.

## Corrección de errores {#bug-fixes}

* Algunos usuarios no podían ver los detalles de la ejecución mientras esperaban la aprobación.
* En la página **Información general** , el margen derecho no era coherente.
* El contenedor de compilación podría quedarse sin memoria en proyectos grandes.
* En determinadas circunstancias, la regla OakPAL de BannedPaths no identificaba el contenido instalado en /libs.
* Cuando se rechazó una puerta de calidad, el encabezado del cuadro de diálogo se mostró *parcialmente aprobado*.

## Problemas conocidos {#known-issues}

* La descarga de gráficos de supervisión no está disponible en Safari.
