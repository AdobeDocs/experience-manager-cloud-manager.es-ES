---
title: Notas de la versión 2019.6.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.6.0
description: Siga esta página para obtener información sobre la versión 2019.6.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.6.0 de AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 7cfa0cf66efd5891263bfcc83a5149daec5c8b67
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 8%

---

# Notas de la versión 2019.6.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.6.0 agrega nuevas reglas de calidad de código y un nuevo asistente para la actualización del producto. Siga las secciones a continuación para obtener más detalles.

## Fecha de la versión {#release-date}

La fecha de versión de la [!UICONTROL Cloud Manager] versión 2019.6.0 es el 20 de junio de 2019.

## Novedades {#whats-new}

* Nuevo asistente de actualización de producto para ayudar a los clientes a ejecutar correctamente una actualización de AEM. Consulte [Asistente para actualización de productos](overview-productupdate-wizard.md) para obtener más información.
* Reglas de calidad de código que examinan las estructuras de contenido. Consulte [Reglas de calidad de código personalizado](custom-code-quality-rules.md) para obtener más información.
* El tamaño máximo de una inserción de git se ha aumentado a 1 GB.

## Corrección de errores {#bug-fixes}

* En algunos casos, los oleoductos no pudieron iniciarse debido a un fallo previo.

## Problemas conocidos {#known-issues}

* La descarga de CSV de calidad de código no siempre se ordena según la gravedad.
* La regla *ConfigAndInstallMustOnlyContainOsgiNodes* puede informar de falsos positivos si las configuraciones de OSGi se colocan en una carpeta anidada bajo una carpeta *config*.