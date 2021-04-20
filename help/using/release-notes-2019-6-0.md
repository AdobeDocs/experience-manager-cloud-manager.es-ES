---
title: Notas de la versión 2019.6.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.6.0
description: Siga esta página para obtener información sobre la versión 2019.6.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.6.0 de AEM Cloud Manager.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 9%

---

# Notas de la versión 2019.6.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.6.0 agrega nuevas reglas de calidad de código y un nuevo asistente de actualización de producto. Siga las secciones a continuación para obtener más información.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2019.6.0 de [!UICONTROL Cloud Manager] es el 20 de junio de 2019 .

## Novedades {#whats-new}

* Nuevo asistente de actualización de producto para ayudar a los clientes a ejecutar correctamente una actualización de AEM. Consulte [Asistente para la actualización de productos](overview-productupdate-wizard.md) para obtener más información.
* Reglas de calidad de código que examinan estructuras de contenido. Consulte [Reglas de calidad de código personalizadas](custom-code-quality-rules.md) para obtener más información.
* El tamaño máximo de una notificación push de git se ha aumentado a 1 GB.

## Corrección de errores {#bug-fixes}

* En algunos casos, las tuberías no pudieron iniciarse debido a un fallo previo.

## Problemas conocidos {#known-issues}

* La descarga de CSV de calidad de código no siempre se ordena según la gravedad.
* La regla *ConfigAndInstallShouldOnlyContainOsgiNodes* puede notificar los falsos positivos si las configuraciones de OSGi se colocan en una carpeta anidada bajo una carpeta *config*.