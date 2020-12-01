---
title: Notas de la versión 2018.6.0
seo-title: Notas de la versión de AEM Cloud Manager para 2018.6.0
description: Siga esta página para obtener información sobre la versión 2018.6.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2018.6.0 de AEM Cloud Manager.
uuid: 211b6e1b-10fb-46b0-b591-44d5e44abd77
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 8584f467-3e61-41ea-98e4-f79e68c86469
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 3%

---


# Notas de la versión 2018.6.0 {#release-notes-for}

La siguiente sección describe las Notas de revisión generales de la [!UICONTROL Cloud Manager] versión 2018.6.0 y agrega compatibilidad para la invalidación de despachantes durante implementaciones, notificaciones adicionales y mejoras de uso.

## Fecha de la versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] versión 2018.6.0 es el 9 de agosto de 2018.

## Novedades {#what-s-new}

* **Canalización**  CI/CD: Invalidación del despachante configurable y vaciado de caché tanto en fase como en producción durante la ejecución de la canalización CI/CD. Consulte [Configuración de la canalización CI/CD](configuring-pipeline.md) para obtener más información.

* **Canalización**  CI/CD: durante la configuración de la canalización, ahora es posible definir cómo se comportará la canalización cuando detecte una falla importante en una de las compuertas de calidad. Consulte [Configuración de la canalización CI/CD](configuring-pipeline.md) para obtener más información.

* **Canalización**  CI/CD: durante la configuración del canalizador, ahora es posible seleccionar si desea que la supervisión de CSE la realice el CSE o cualquier CSE disponible. Consulte [Configuración de la canalización CI/CD](configuring-pipeline.md) para obtener más información.

* **Canalización**  CI/CD: cuando la canalización CI/CD alcanza el paso de aprobación comercial, se enviará una notificación a los usuarios autorizados para aprobar la implementación. Consulte [Notificaciones](notifications.md) para obtener más información.

* **Canalización**  CI/CD: cuando la canalización CI/CD alcanza el programa establecido, se enviará una notificación a los usuarios autorizados para establecer la programación. Consulte [Notificaciones](notifications.md) para obtener más información.

* **Análisis**  de calidad del código: Nuevas reglas para identificar solicitudes HTTP/HTTPS salientes incorrectamente configuradas. Consulte [Reglas de calidad de código personalizado](custom-code-quality-rules.md) para obtener más información.

## Corrección de errores {#bug-fixes}

* En algunos casos, la prueba de rendimiento no se distribuyó completamente entre varias instancias de despachante y publicación.
* La navegación por el encabezado desapareció en ventanas estrechas del explorador.
* Algunos ajustes de la canalización no estaban deshabilitados mientras la canalización se estaba ejecutando.
* Los vínculos a AEM y supervisión desde la pantalla de lista de Programa reemplazaron a la ficha actual del explorador y abrieron una nueva ficha.
* En determinadas circunstancias, un período de aprobación de larga duración podría provocar un error en la implementación.
