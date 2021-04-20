---
title: Notas de la versión 2020.3.0
seo-title: Notas de la versión de AEM Cloud Manager para 2020.3.0
description: Siga esta página para obtener información sobre la versión 2020.3.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2020.3.0 de AEM Cloud Manager
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 51%

---

# Notas de la versión 2020.3.0 {#release-notes-for}

La siguiente sección describe las notas de la versión generales de la versión [!UICONTROL Cloud Manager] 2020.3.0.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2020.3.0 de [!UICONTROL Cloud Manager] es el 5 de marzo de 2020.

## Novedades {#whats-new}

* El registro del paso de compilación ya está disponible mientras este se ejecuta.
* Algunos mensajes de la página de detalles de ejecución de la canalización se han editado para mayor claridad.

## Corrección de errores {#bug-fixes}

* Ciertas configuraciones de implementación podrían hacer que los registros de los pasos de implementación no estén disponibles si la implementación falla.
* Los errores específicos dentro de los pasos de implementación para programas de Managed Services podrían causar que las ejecuciones posteriores no se inicien.
* La instancia efímera de SonarQube utilizada en el paso de compilación, en algunas ocasiones no se iniciaba dentro del tiempo de espera configurado.
* En determinados proyectos, los objetos *ResourceResolver siempre se deben cerrar* produciría una Null Pointer Exception; sin embargo, esto no afectó a la ejecución de la canalización.