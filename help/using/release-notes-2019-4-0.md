---
title: Notas de la versión 2019.4.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.4.0
description: Siga esta página para obtener información sobre la versión 2019.4.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.4.0 de AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: b368c46c2a9f40d0c3867db6eb2a333bd71fe22a
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 6%

---


# Notas de la versión 2019.4.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.4.0 no contiene cambios funcionales significativos. Siga las secciones a continuación para obtener más detalles.

## Fecha de la versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] versión 2019.4.0 es el 18 de abril de 2019.

## Novedades {#whats-new}

* La interfaz de usuario de Cloud Manager ya está disponible en inglés, francés, alemán y japonés.
* Los pasos de implementación ahora contienen el proceso que se está ejecutando, es decir, cuando se está ejecutando una copia de seguridad, se están instalando paquetes y se están reconfigurando los equilibradores de carga

## Corrección de errores {#bug-fixes}

* Se ha mejorado el método de implementación utilizado para los cambios de Dispatcher a fin de administrar casos de uso adicionales.
* Algunos tipos de tamaño de instancia no se mostraban correctamente en la página Entornos.
* Las reglas de calidad de código CQBP-84-dependencias producían falsos positivos para las bibliotecas de Adobe incrustadas, como Componentes principales de WCM y Uso compartido de recursos Commons.
* El botón de detalles del paso de análisis de código se activó cuando los detalles no estaban disponibles.
* El mensaje de error al especificar un valor no válido para el KPI de vistas de página por minuto tenía el límite inferior incorrecto.
* La categoría de implementación en un canal que no es de producción se capitalizó incorrectamente.
* La tarjeta de llamada a acción de la página **Información general** tenía un texto incorrecto cuando el repositorio git no estaba configurado correctamente.

## Problemas conocidos {#known-issues}

* Los valores de SLA pueden redondearse incorrectamente.
