---
title: Notas de la versión 2020.4.0
seo-title: Notas de la versión de AEM Cloud Manager para 2020.4.0
description: Siga esta página para obtener información sobre la versión 2020.4.0 de Cloud Manager
seo-description: Siga esta página para obtener información sobre la versión 2020.4.0 de AEM Cloud Manager
translation-type: tm+mt
source-git-commit: ee7fc8a23dd0719eda84638c810842c2dc1772bb

---

# Notas de la versión 2020.4.0 {#release-notes-for}

La siguiente sección describe las Notas de revisión generales de la versión 2020.4.0 [!UICONTROL Cloud Manager] .

## Release Date {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2020.4.0 es el 9 de abril de 2020.

## Novedades {#whats-new}

* Cambios en la página de información general del Administrador de la nube de navegación para permitir al usuario editar o cambiar de programa.
* Cambios que permiten al usuario editar programas desde la tarjeta de programa en la página de aterrizaje de Cloud Manager.
* Nuevo estado de canalización **La ejecución** de canalización se muestra en el entorno con el que está asociada.
* Mejoras en la comprensión de la página de ejecución de la canalización. Esto incluye la visualización del nombre de la canalización (solo para la canalización que no es de producción) y del tipo, y un distintivo para indicar si el estado de la canalización está en curso/cancelado/fallido.
* El proceso utilizado para generar contraseñas de git se ha vuelto más resistente a los problemas en la capa de servicio subyacente.

## Corrección de errores {#bug-fixes}

* Los datos de supervisión pueden mostrarse a veces de manera incorrecta o no basarse en ninguna variación menor de los valores técnicos.
* La configuración Maven utilizada en el contenedor de compilación se actualizó para evitar interbloqueos al descargar metadatos de artefactos.
* En ocasiones, el proceso de prueba de rendimiento de Recursos no pudo descifrar la contraseña de AEM, lo que provocó errores en la prueba.
* Algunas topologías con instancias de espera podrían tener falsos negativos en las pruebas de seguridad.
* Si el entorno del escenario contenía una instancia detenida, el paso de la prueba de seguridad a veces fallaba.
* Las notificaciones de Experience Cloud no se recibían de forma coherente.

