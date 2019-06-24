---
title: Notas de la versión de 2019.6.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.6.0
description: Siga esta página para obtener información sobre la versión 2019.6.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.6.0 de AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 9a1af88238a232c64d9f0229059c5001f314c736

---

# Release Notes for 2019.6.0 {#release-notes-for}

The [!UICONTROL Cloud Manager] 2019.6.0 Release does not contain significant functional changes. Siga las secciones siguientes para obtener más detalles.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.6.0 is June 20, 2019 .

## Novedades {#whats-new}

* Nuevo asistente de actualización de producto para ayudar a los clientes a ejecutar correctamente una actualización de AEM. Refer to [Product Update Wizard](overview-productupdate-wizard.md) to learn more.
* Reglas de calidad de código que examinan estructuras de contenido. Refer to [Custom Code Quality Rules](custom-code-quality-rules.md)for more information.
* El tamaño máximo de una inserción de git ha aumentado a 1 GB.

## Bug Fixes {#bug-fixes}

* En algunos casos, no se pudieron iniciar los pipeline debido a un fallo previo.

## Problemas conocidos {#known-issues}

* La descarga de CSV de calidad del código no siempre se ordena según la gravedad.
* False positives may be reported by the *ConfigAndInstallShouldOnlyContainOsgiNodes* rule if OSGi configurations are placed in a nested folder under a config folder.
