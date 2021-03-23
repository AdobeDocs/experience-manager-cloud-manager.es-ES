---
title: Notas de la versión 2018.8.0
seo-title: Notas de la versión de AEM Cloud Manager para 2018.8.0
description: Siga esta página para obtener información sobre la versión 2018.8.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2018.8.0 de AEM Cloud Manager.
uuid: e8aaba32-89b4-4bc5-b295-09b753252612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 9222ac3b-525e-47c1-b481-ac9d22e3d559
feature: Información de la versión
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 4%

---


# Notas de la versión 2018.8.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2018.8.0 añade compatibilidad para activar automáticamente la canalización CI/CD tras las confirmaciones de Git y un nuevo asistente para crear proyectos de aplicación en Git basado en el tipo de archivo del proyecto AEM.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2018.8.0 de [!UICONTROL Cloud Manager] es el 4 de octubre de 2018.

## Novedades {#what-s-new}

* **Configuración del programa** : nuevo asistente para crear un proyecto de aplicación en Git mediante el tipo de archivo del proyecto AEM

* **Canalización de CI/CD** : se añaden los cambios siguientes a la canalización de CI/CD. Para obtener más información, consulte [Configuración de la canalización de CI/CD](configuring-pipeline.md) .

   * En el déclencheur Cambios de Git, que inicia la canalización CI/CD cada vez que se agregan confirmaciones a la rama git configurada.
   * Las tarjetas de la pantalla principal ahora se vinculan en profundidad a secciones específicas de la página de ejecución de la canalización.
   * La página Actividad ahora enumera la rama específica utilizada para cada ejecución.
   * La página Actividad ahora indica la duración en horas y minutos.
   * La página de ejecución de la canalización ahora muestra la versión o el nombre de la etiqueta creados para la ejecución.
   * La versión de Apache Maven se ha actualizado a 3.5.3.

* **Navegación** : se añaden los cambios siguientes al  [!UICONTROL Cloud Manager].

   * El vínculo Recursos en la navegación global navegará hasta Runbook en Sharepoint.
   * El menú Ayuda se ha reorganizado para incluir más contenido específico de [!UICONTROL Cloud Manager].

## Corrección de errores {#bug-fixes}

* Algunos detalles del cuadro de diálogo Pruebas de rendimiento no estaban visibles en Firefox.
* Los tiempos de espera entre sistemas internos ocasionalmente causaban que se informara de errores de implementación.
* El color del icono en la página Actividad no era correcto para algunas ejecuciones de canalización correctas.
* En algunos casos, el cuadro de diálogo Pruebas de rendimiento mostraba la misma métrica varias veces.
* Si se agregaba una nueva instancia después de que se iniciara la canalización de CD/CI, la implementación no se ejecutaría en la instancia recién creada.

## Problemas conocidos {#known-issues}

* Las ramas creadas mediante el Asistente para proyectos de aplicación no pueden contener guiones.
* Es posible que la barra lateral de notificación [!UICONTROL Experience Cloud] no cargue las notificaciones de forma coherente. Sin embargo, las notificaciones son visibles en [!UICONTROL Experience Cloud] y, si se configuran, se envían por correo electrónico.

