---
title: Notas de la versión de 2018.8.0
seo-title: Notas de la versión de AEM Cloud Manager para 2018.8.0
description: Siga esta página para obtener información sobre la versión 2018.8.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2018.8.0 de AEM Cloud Manager.
uuid: e 8 aaba 32-89 b 4-4 bc 5-b 295-09 b 753252612
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas de la versión
discoiquuid: 9222 ac 3 b -525 e -47 c 1-b 481-ac 9 d 22 e 3 d 559
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notas de la versión de 2018.8.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2018.8.0 añade compatibilidad para activar la canalización CI/CD automáticamente sobre la git commit y un nuevo asistente para crear proyectos de aplicación en git basadas en el tipo de archetype Project Archetype.

## Fecha de versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2018.8.0 es el 04 de octubre de 2018.

## Novedades {#what-s-new}

* **Configuración** del programa: Asistente nuevo para crear un proyecto de aplicación en git con el tipo de archetype de proyecto AEM Consulte [Crear un proyecto de aplicación AEM](create-an-application-project.md) para obtener más información.

* **Pipeline** CI/CD: Los cambios siguientes se añaden a la cartera CI/CD. Consulte [Configurar su flujo de PC/CD](configuring-pipeline.md) para obtener más información.

   * En Cambios de Git, se inicia la canalización CI/CD siempre que se haya añadido a la ramificación de git configurada.
   * Las tarjetas en la pantalla de inicio ahora se vinculan profundo a secciones específicas de la página de ejecución de pipeline.
   * La página Actividad ahora enumera la rama específica utilizada para cada ejecución.
   * La página de actividad ahora indica la duración en horas y minutos.
   * La página de ejecución de Pipeline ahora muestra el nombre de la versión o etiqueta creada para la ejecución.
   * La versión de Apache Maven se ha actualizado a 3.5.3.

* **Navegación** : Se agregan los siguientes cambios al [!UICONTROL Cloud Manager].

   * El vínculo de recursos en la navegación global navegará al libro de descargas en Sharepoint.
   * Se ha reorganizado el menú Ayuda para incluir más [!UICONTROL Cloud Manager]contenido específico.

## Corrección de errores {#bug-fixes}

* Algunos detalles del cuadro de diálogo Prueba de rendimiento no eran visibles en Firefox.
* En ocasiones, los tiempos de espera entre sistemas internos causaban que se informara de errores de implementación.
* El color del icono de la página Actividad no era correcto para algunas ejecuciones de pipeline exitosas.
* En algunos casos, el cuadro de diálogo Prueba de rendimiento muestra la misma métrica varias veces.
* Si se agregó una nueva instancia después de haber iniciado la canalización CI/CD, la implementación no se ejecutará en la instancia recién creada.

## Problemas conocidos {#known-issues}

* Las ramas creadas con el Asistente para proyectos de aplicación no pueden contener guiones.
* La barra lateral [!UICONTROL Experience Cloud] de notificación puede no cargar notificaciones de forma coherente. Las notificaciones, sin embargo, son visibles en [!UICONTROL Experience Cloud] el y, si se configuran, se envían por correo electrónico.

