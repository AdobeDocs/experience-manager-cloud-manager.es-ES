---
title: Notas de la versión 2019.7.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.7.0
description: Siga esta página para obtener información sobre la versión 2019.7.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.7.0 de AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 365cd6dfe65059c0c529f774bbcda946d47b0db5
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 7%

---

# Notas de la versión 2019.7.0 {#release-notes-for}

La [!UICONTROL Cloud Manager] versión 2019.7.0 añade actualizaciones a las notificaciones del Experience Cloud y mejoras como correcciones de errores. Siga las secciones a continuación para obtener más detalles.

## Fecha de la versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] versión 2019.7.0 es el 18 de julio de 2019.

## Novedades {#whats-new}

Ahora se envía una notificación de Experience Cloud en el inicio de una implementación de producción.

## Corrección de errores {#bug-fixes}

* En algunos casos, Cloud Manager realizaría la análisis de código estático en archivos Python y PHP.
* Los paquetes que contenían FileVault InstallHooks no se ejecutaban de manera consistente a través del paso de calidad del código.
* En determinadas combinaciones, los problemas de calidad del código no se ordenaban de forma consistente.
* Hubo algunos problemas visuales en la página de ejecución de la canalización.
* El paso de la prueba de rendimiento podría fallar aleatoriamente a veces debido a las limitaciones de recursos de la infraestructura de nube subyacente.
* Algunas compilaciones de clientes fallarían debido a problemas de red.