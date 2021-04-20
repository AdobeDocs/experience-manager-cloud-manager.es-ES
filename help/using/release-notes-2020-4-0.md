---
title: Notas de la versión 2020.4.0
seo-title: Notas de la versión de AEM Cloud Manager para 2020.4.0
description: Siga esta página para obtener información sobre la versión 2020.4.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2020.4.0 de AEM Cloud Manager
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 38%

---

# Notas de la versión 2020.4.0 {#release-notes-for}

La siguiente sección describe las notas de la versión generales de la versión [!UICONTROL Cloud Manager] 2020.4.0.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2020.4.0 de [!UICONTROL Cloud Manager] es el 9 de abril de 2020.

## Novedades {#whats-new}

* Cambios en la página de información general de navegación de Cloud Manager para permitir que el usuario edite o cambie de programa.
* Cambios que permiten al usuario editar programas desde la tarjeta de programa en la página de aterrizaje de Cloud Manager.
* Se muestra el nuevo estado de **Canalización ejecutándose** en el entorno con el que está asociada.
* Mejoras en la comprensión de la página de ejecución de la canalización. Esto incluye la visualización del nombre de la canalización (solo para la canalización que no es de producción) y el tipo, y un distintivo para indicar si el estado de la canalización está en curso/cancelada/fallida.
* El proceso utilizado para generar contraseñas de git se ha vuelto más resistente a los problemas en la capa de servicio subyacente.

## Corrección de errores {#bug-fixes}

* Los datos de monitorización a veces se podían mostrar de forma incorrecta o no se mostraban en absoluto en función de variaciones menores en los valores técnicos.
* La configuración Maven utilizada en el contenedor de compilación se actualizó para evitar interbloqueos al descargar metadatos de artefactos.
* El proceso de prueba de rendimiento de Assets ocasionalmente no podía descifrar la contraseña de AEM, lo que provocaba errores en la prueba.
* Algunas topologías con instancias en espera podrían tener falsos negativos en las pruebas de seguridad.
* Si el entorno de ensayo contenía una instancia detenida, el paso de prueba de seguridad a veces fallaba.
* Las notificaciones de Experience Cloud no se recibían de forma coherente.

