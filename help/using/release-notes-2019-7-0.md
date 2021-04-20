---
title: Notas de la versión 2019.7.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.7.0
description: Siga esta página para obtener información sobre la versión 2019.7.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.7.0 de AEM Cloud Manager.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 8%

---

# Notas de la versión 2019.7.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2019.7.0 añade actualizaciones a las notificaciones y mejoras del Experience Cloud como correcciones de errores. Siga las secciones a continuación para obtener más información.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2019.7.0 de [!UICONTROL Cloud Manager] es el 18 de julio de 2019.

## Novedades {#whats-new}

Ahora hay una notificación de Experience Cloud enviada al inicio de una implementación de producción.

## Corrección de errores {#bug-fixes}

* En algunos casos, Cloud Manager realizaría análisis de código estático en archivos Python y PHP.
* Los paquetes que contenían FileVault InstallHooks no se ejecutaban de manera consistente a través del paso de calidad del código.
* En algunas combinaciones, los problemas de calidad del código no se ordenaban de forma consistente.
* Hubo algunos problemas visuales en la página de ejecución de la canalización.
* El paso de prueba de rendimiento podría fallar aleatoriamente a veces debido a las restricciones de recursos de la infraestructura de nube subyacente.
* Algunas compilaciones de clientes fallarían debido a problemas de red.