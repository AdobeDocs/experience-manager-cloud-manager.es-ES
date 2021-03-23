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
feature: Información de la versión
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 8%

---


# Notas de la versión 2018.5.0 {#release-notes-for}

La siguiente sección describe las notas de la versión generales de la versión [!UICONTROL Cloud Manager] 2018.5.0.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2018.5.0 de [!UICONTROL Cloud Manager] es el 12 de julio de 2018.

## Novedades {#what-s-new}

* **Notificaciones de canalización de CI/CD** : los usuarios ahora verán  [!UICONTROL Experience Cloud] notificaciones para eventos de canalización. Consulte [Notifications](notifications.md) para obtener más información.

* **Implementaciones de producción programadas** : ahora los usuarios pueden programar una fecha u hora para las implementaciones de producción. Consulte [Implementar el código](deploying-code.md) para obtener más información.

* **** Página de estado retirada a  **Actividad**.

* Se muestra información más específica en la página principal para los problemas que se han encontrado durante la ejecución de la canalización.
* Mejoras en la infraestructura de pruebas de rendimiento.

## Corrección de errores {#bug-fixes}

* En algunas condiciones se utilizaba el perfil SonarQube incorrecto, lo que producía métricas de calidad de código incorrectas.
* La comprobación de SonarQube CQBP-75 ignoró ciertas anotaciones OSGi.
* Cuando se canceló la canalización de CI/CD, el estado no se mostraba de forma coherente.

## Problemas conocidos {#known-issues}

* Los vínculos a **AEM** y **Monitoring** desde la pantalla Lista de programas reemplazan la pestaña actual del explorador y se abren a una nueva pestaña.

