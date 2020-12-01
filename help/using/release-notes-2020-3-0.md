---
title: Notas de la versión 2020.3.0
seo-title: Notas de la versión de AEM Cloud Manager para 2020.3.0
description: Siga esta página para obtener información sobre la versión 2020.3.0 de Cloud Manager
seo-description: Siga esta página para obtener información sobre la versión 2020.3.0 de AEM Cloud Manager
translation-type: tm+mt
source-git-commit: e7da473a22bec1d3d9b3d39bf654af0c596fe86d
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 51%

---

# Notas de la versión 2020.3.0 {#release-notes-for}

La siguiente sección describe las Notas de revisión generales de la [!UICONTROL Cloud Manager] versión 2020.3.0.

## Fecha de la versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] versión 2020.3.0 es el 05 de marzo de 2020.

## Novedades {#whats-new}

* El registro del paso de compilación ya está disponible mientras este se ejecuta.
* Algunos mensajes de la página de detalles de ejecución de la canalización se han editado para mayor claridad.

## Corrección de errores {#bug-fixes}

* Ciertas configuraciones de implementación podrían hacer que los registros de los pasos de implementación no estuvieran disponibles si la implementación fallaba.
* Los errores específicos dentro de los pasos de implementación para programas de Managed Services podrían provocar que las ejecuciones subsiguientes no se inicio.
* La instancia efímera de SonarQube utilizada en el paso de compilación, en algunas ocasiones no se iniciaba dentro del tiempo de espera configurado.
* En determinados proyectos, los objetos *ResourceResolver siempre se deben cerrar* produciría una Null Pointer Exception; sin embargo, esto no afectó a la ejecución de la canalización.