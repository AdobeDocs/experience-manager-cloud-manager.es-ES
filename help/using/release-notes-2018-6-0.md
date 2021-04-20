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
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 4%

---


# Notas de la versión 2018.6.0 {#release-notes-for}

En la siguiente sección se describen las notas de la versión generales de [!UICONTROL Cloud Manager] versión 2018.6.0 y se añade compatibilidad con la invalidación de Dispatcher durante las implementaciones, las notificaciones adicionales y las mejoras de uso.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2018.6.0 de [!UICONTROL Cloud Manager] es el 9 de agosto de 2018.

## Novedades {#what-s-new}

* **Canalización CI/CD** : Invalidación de Dispatcher configurable y vaciado de caché tanto en fase como en producción durante la ejecución de la canalización CI/CD. Para obtener más información, consulte [Configuración de la canalización de CI/CD](configuring-pipeline.md) .

* **Canalización CI/CD** : durante la configuración de la canalización, ahora es posible definir cómo se comportará la canalización cuando detecte un fallo importante en una de las puertas de calidad. Para obtener más información, consulte [Configuración de la canalización de CI/CD](configuring-pipeline.md) .

* **Canalización de CI/CD** : durante la configuración de la canalización, ahora es posible seleccionar si desea que la supervisión de la CSE la realice su CSE o cualquier CSE disponible. Para obtener más información, consulte [Configuración de la canalización de CI/CD](configuring-pipeline.md) .

* **Canalización de CI/CD** : cuando la canalización de CI/CD llega al paso de aprobación empresarial, se envía una notificación a los usuarios autorizados para aprobar la implementación. Consulte [Notifications](notifications.md) para obtener más información.

* **Canalización de CI/CD** : cuando la canalización de CI/CD llega al conjunto de programaciones, se envía una notificación a los usuarios autorizados para establecer la programación. Consulte [Notifications](notifications.md) para obtener más información.

* **Análisis de calidad del código** : nuevas reglas para identificar solicitudes HTTP/HTTPS salientes configuradas incorrectamente. Consulte [Reglas de calidad de código personalizadas](custom-code-quality-rules.md) para obtener más información.

## Corrección de errores {#bug-fixes}

* En algunos casos, la prueba de rendimiento no se distribuyó completamente entre varias instancias de Dispatcher y de publicación.
* La navegación de encabezado desapareció en ventanas de navegador estrechas.
* Algunos ajustes de la canalización no estaban deshabilitados mientras se ejecutaba.
* Vínculos a AEM y monitorización desde la pantalla de lista de programas reemplazó la pestaña actual del explorador y abrió una nueva pestaña.
* En determinadas circunstancias, un período de aprobación de larga duración podría provocar un error en la implementación.
