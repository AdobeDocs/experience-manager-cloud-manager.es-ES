---
title: Notas de la versión de 2019.4.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.4.0
description: Siga esta página para obtener información sobre la versión 2019.4.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.4.0 de AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 8031df1c1ce9d7fee4ef33de289c6952370b7589

---


# Notas de la versión de 2019.4.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.4.0 no contiene cambios funcionales significativos. Siga las secciones siguientes para obtener más detalles.

## Fecha de versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2019.4.0 es el 18 de abril de 2019.

## Novedades {#whats-new}

* La interfaz de usuario de Cloud Manager ahora está disponible en inglés, francés, alemán y japonés.
* Los pasos de implementación ahora contienen el proceso que se está ejecutando, es decir, cuando se ejecuta una copia de seguridad, los paquetes se instalan y se vuelven a configurar equilibradores de carga.

## Corrección de errores {#bug-fixes}

* Se ha mejorado el método de implementación utilizado para los cambios de Dispatcher para gestionar casos de uso adicionales.
* Algunos tipos de tamaño de instancia no se mostraban correctamente en la página Entornos.
* Las reglas de calidad de código CQBP -84 crearon falsos positivos para bibliotecas de Adobe incrustadas como Componentes Core WCM y Asset Share Commons.
* El botón de detalles del paso de digitalización de código estaba activado cuando los detalles no estaban disponibles.
* El mensaje de error al especificar un valor no válido para las vistas de página por KPI de minuto tenía un límite inferior incorrecto.
* La categoría de implementación de un canalizador no de producción se ha cargado de forma incorrecta.
* La llamada a la tarjeta de acción en la página **Información general** tenía texto incorrecto cuando el repositorio de git no estaba configurado correctamente.

## Problemas conocidos {#known-issues}

* Los valores SLA pueden redondearse incorrectamente.
