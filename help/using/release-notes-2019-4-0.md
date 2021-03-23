---
title: Notas de la versión 2019.4.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.4.0
description: Siga esta página para obtener información sobre la versión 2019.4.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.4.0 de AEM Cloud Manager.
feature: Información de la versión
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 7%

---


# Notas de la versión 2019.4.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.4.0 no contiene cambios funcionales significativos. Siga las secciones a continuación para obtener más información.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2019.4.0 de [!UICONTROL Cloud Manager] es el 18 de abril de 2019.

## Novedades {#whats-new}

* La interfaz de usuario de Cloud Manager ya está disponible en inglés, francés, alemán y japonés.
* Los pasos de implementación ahora contienen el proceso que se está ejecutando, es decir, cuando se está ejecutando una copia de seguridad, los paquetes se están instalando y los equilibradores de carga se están reconfigurando

## Corrección de errores {#bug-fixes}

* Se ha mejorado el método de implementación utilizado para los cambios de Dispatcher para administrar casos de uso adicionales.
* Algunos tipos de tamaño de instancia no se mostraban correctamente en la página Entornos .
* Las reglas de calidad de código CQBP-84-dependencias produjeron falsos positivos para bibliotecas de Adobe incrustadas, como los componentes principales de WCM y Asset Share Commons.
* El botón de detalles del paso de análisis de código se activó cuando los detalles no estaban disponibles.
* El mensaje de error al especificar un valor no válido para el KPI de vistas de página por minuto tenía el límite inferior incorrecto.
* La categoría de implementación de una canalización que no es de producción se capitalizó incorrectamente.
* La tarjeta de llamada a la acción de la página **Información general** tenía un texto incorrecto cuando el repositorio de Git no estaba configurado correctamente.

## Problemas conocidos {#known-issues}

* Los valores de SLA pueden redondearse incorrectamente.
