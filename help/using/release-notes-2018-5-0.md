---
title: Notas de la versión 2018.5.0
seo-title: Notas de la versión de AEM Cloud Manager para 2018.5.0
description: Siga esta página para obtener información sobre la versión 2018.5.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2018.5.0 de AEM Cloud Manager.
uuid: 37f8b155-6984-454d-83a8-3f5fb081be97
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 6d1e7098-b56e-4172-8373-486f186f3d53
translation-type: tm+mt
source-git-commit: 15f75ca67c3d52ae511357c5b564daaa3d9def6b
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 7%

---


# Notas de la versión 2018.5.0 {#release-notes-for}

La siguiente sección describe las Notas de revisión generales de la [!UICONTROL Cloud Manager] versión 2018.5.0.

## Fecha de la versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] versión 2018.5.0 es el 12 de julio de 2018.

## Novedades {#what-s-new}

* **Notificaciones**  de canalización de CD/CD: los usuarios ahora verán  [!UICONTROL Experience Cloud] notificaciones de eventos de canalización. Consulte las [Notificaciones](notifications.md) para obtener más información.

* **Implementaciones**  de producción programadas: ahora los usuarios pueden programar una fecha u hora para las implementaciones de producción. Consulte [Implementar el código](deploying-code.md) para obtener más información.

* **** Statuspage se retira a la  **Actividad**.

* Se muestra información más específica sobre la página de inicio de los problemas que se han producido durante la ejecución de la canalización.
* Mejoras en la infraestructura de pruebas de rendimiento.

## Corrección de errores {#bug-fixes}

* En algunas condiciones, se utilizó el perfil SonarQube incorrecto, lo que dio lugar a métricas de calidad de código incorrectas.
* La comprobación de SonarQube CQBP-75 ignoró ciertas anotaciones OSGi.
* Cuando se canceló la canalización CI/CD, el estado no se mostraba de forma coherente.

## Problemas conocidos {#known-issues}

* Los vínculos a **AEM** y **Monitoreo** desde la pantalla de Lista de Programa reemplazan la ficha actual del explorador y se abren a una nueva ficha.

