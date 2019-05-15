---
title: Notas de la versión de 2018.6.0
seo-title: Notas de la versión de AEM Cloud Manager para 2018.6.0
description: ollow this page to get information for Cloud Manager Release 2018.6.0.
seo-description: Siga esta página para obtener información sobre la versión 2018.6.0 de AEM Cloud Manager.
uuid: 211 b 6 e 1 b -10 fb -46 b 0-b 591-44 d 5 e 44 abd 77
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas de la versión
discoiquuid: 8584 f 467-3 e 61-41 ea -98 e 4-f 79 e 68 c 86469
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notas de la versión de 2018.6.0 {#release-notes-for}

La siguiente sección describe las Notas generales de la versión de [!UICONTROL Cloud Manager] la versión 2018.6.0 y añade compatibilidad con la invalidación de Dispatcher durante las implementaciones, las notificaciones adicionales y las mejoras de uso.

## Fecha de versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2018.6.0 es el 9 de agosto de 2018.

## Novedades {#what-s-new}

* **Pipeline** CI/CD: Invalidación de la caché configurable y Vaciado de caché en etapa y producción durante la ejecución de CI/CD de CADUCIDAD. Consulte [Configurar su flujo de PC/CD](configuring-pipeline.md) para obtener más información.

* **Pipeline** CI/CD: durante la configuración del canal, ahora es posible definir cómo se comportará la canalización cuando detecta un fallo importante en una de las puertas de calidad. Consulte [Configurar su flujo de PC/CD](configuring-pipeline.md) para obtener más información.

* **Pipeline** CI/CD: durante la configuración del canal, ahora es posible seleccionar si desea que la supervisión CSE sea llevada a cabo por CSE o cualquier CSE disponible. Consulte [Configurar su flujo de PC/CD](configuring-pipeline.md) para obtener más información.

* **Pipeline** CI/CD: cuando la canalización CI/CD llega al paso de aprobación comercial, se enviará una notificación a los usuarios autorizados para aprobar la implementación. Consulte [Notificaciones](notifications.md) para obtener más información.

* **Pipeline** CI/CD: Cuando la canalización CI/CD llega al conjunto de programación, se enviará una notificación a los usuarios autorizados para establecer la programación. Consulte [Notificaciones](notifications.md) para obtener más información.

* **Análisis** de calidad del código: Nuevas reglas para identificar solicitudes HTTP/HTTPS salientes de manera incorrecta. Consulte Reglas de calidad de código [personalizado](custom-code-quality-rules.md) para obtener más información.

## Corrección de errores {#bug-fixes}

* En algunos casos, la prueba de rendimiento no se distribuyó completamente en varias instancias de despachante y publicación.
* La navegación del encabezado desapareció en ventanas estrechas del explorador.
* Algunas configuraciones del canal no estaban deshabilitadas mientras se estaba ejecutando la cartera.
* Los vínculos a AEM y Monitoreo desde la pantalla de lista del programa sustituyen la ficha actual del explorador y abren una nueva ficha.
* En determinadas circunstancias, un período de aprobación prolongado podría provocar una implementación fallida.
