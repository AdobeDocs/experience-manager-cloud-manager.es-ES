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
translation-type: tm+mt
source-git-commit: c35398110e9d8311bf58f217efdd082cf0cfd90a
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 4%

---


# Notas de la versión 2018.8.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2018.8.0 añade compatibilidad para activar automáticamente el canalizador de CI/CD tras comprometer git y un nuevo asistente para crear proyectos de aplicación en git según el arquetipo de proyecto AEM.

## Fecha de la versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2018.8.0 es el 04 de octubre de 2018.

## Novedades {#what-s-new}

* **Configuración** de programa: nuevo asistente para crear un proyecto de aplicación en Git mediante el arquetipo de proyecto de AEM

* **Canalización** CI/CD: se añaden los siguientes cambios a la canalización CI/CD. Consulte [Configurar la canalización](configuring-pipeline.md) de CD/CI para obtener más información.

   * Al activar Cambios en Git, que inicio la canalización CI/CD cada vez que hay confirmaciones agregadas a la rama git configurada.
   * Las tarjetas en la pantalla principal ahora se vinculan en profundidad a secciones específicas de la página de ejecución de la canalización.
   * La página de actividad ahora lista la rama específica utilizada para cada ejecución.
   * La página de actividad ahora indica la duración en horas y minutos.
   * La página de ejecución de canalización ahora muestra el nombre de la versión o etiqueta creada para la ejecución.
   * La versión de Apache Maven se ha actualizado a 3.5.3.

* **Navegación** : se añaden los siguientes cambios a la [!UICONTROL Cloud Manager].

   * El vínculo Recursos en la navegación global navegará al Runbook en Sharepoint.
   * El menú Ayuda se ha reorganizado para incluir contenido más [!UICONTROL Cloud Manager]específico.

## Corrección de errores {#bug-fixes}

* Algunos detalles del cuadro de diálogo Prueba de rendimiento no estaban visibles en Firefox.
* Los tiempos de espera entre sistemas internos ocasionalmente ocasionan que se informen errores de implementación.
* El color del icono en la página de Actividad no era correcto para algunas ejecuciones de canalización correctas.
* En algunos casos, el cuadro de diálogo Prueba de rendimiento enumeraba la misma métrica varias veces.
* Si se agregaba una nueva instancia después de que se hubiera iniciado la canalización CI/CD, la implementación no se ejecutaría en la instancia recién creada.

## Problemas conocidos {#known-issues}

* Las ramas creadas con el Asistente para proyectos de aplicación no pueden contener guiones.
* Es posible que la barra lateral de [!UICONTROL Experience Cloud] notificaciones no cargue las notificaciones de forma coherente. Sin embargo, las notificaciones son visibles en el [!UICONTROL Experience Cloud] y, si están configuradas, se enviarán por correo electrónico.

