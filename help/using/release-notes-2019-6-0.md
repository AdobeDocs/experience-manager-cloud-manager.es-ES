---
title: Notas de la versión de 2019.6.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.6.0
description: Siga esta página para obtener información sobre la versión 2019.6.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.6.0 de AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 7cfa0cf66efd5891263bfcc83a5149daec5c8b67

---

# Notas de la versión de 2019.6.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.6.0 añade nuevas reglas de calidad de código y un nuevo asistente para la actualización de productos. Siga las secciones a continuación para obtener más detalles.

## Fecha de lanzamiento {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2019.6.0 es el 20 de junio de 2019.

## Novedades {#whats-new}

* Nuevo asistente de actualización de producto para ayudar a los clientes a ejecutar correctamente una actualización de AEM. Para obtener más información, consulte [el Asistente](overview-productupdate-wizard.md) de actualización del producto.
* Reglas de calidad de código que examinan las estructuras de contenido. Consulte Reglas [de calidad de código](custom-code-quality-rules.md) personalizado para obtener más información.
* El tamaño máximo de una inserción de git se ha aumentado a 1 GB.

## Corrección de errores {#bug-fixes}

* En algunos casos, los oleoductos no pudieron iniciarse debido a un fallo previo.

## Problemas conocidos {#known-issues}

* La descarga de CSV de calidad de código no siempre se ordena según la gravedad.
* La regla *ConfigAndInstallMustOnlyContainOsgiNodes* puede informar de falsos positivos si las configuraciones de OSGi se colocan en una carpeta anidada bajo una carpeta *config* .