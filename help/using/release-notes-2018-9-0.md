---
title: Notas de la versión 2018.9.0
seo-title: Notas de la versión de AEM Cloud Manager para 2018.9.0
description: Siga esta página para obtener información sobre la versión 2018.9.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2018.9.0 de AEM Cloud Manager.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
feature: Release Information
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 9%

---


# Notas de la versión 2018.9.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2018.9.0 añade compatibilidad con una API basada en Adobe I/O, incluidos los eventos, para integrar la canalización de CD/CI de [!UICONTROL Cloud Manager] con otros sistemas. También comienza la reescritura de la capa UI en React.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2018.9.0 de [!UICONTROL Cloud Manager] es el 1 de noviembre de 2018.

## Novedades {#whats-new}

* **Canalización de CI/CD** : nuevo sistema de API y evento para integrar la canalización de CI/CD de  [!UICONTROL Cloud Manager]la integración con otros sistemas. Consulte la documentación de la API [!UICONTROL Cloud Manager] (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) para obtener más información.

* **IU** : Introducción a la nueva capa de IU que es más interactiva.

## Corrección de errores {#bug-fixes}

* En [!UICONTROL Cloud Manager] 2018.8.0, las duraciones de la página Actividad se enumeraban en minutos y horas, pero esa información no se reflejaba en el encabezado de la tabla.
* En raras ocasiones, los clientes no podían iniciar el nuevo asistente de proyecto de aplicación.
* La etiqueta de botón del nuevo cuadro de diálogo del asistente del proyecto de la aplicación era engañosa.
* En algunas circunstancias, si se hace clic en el botón Detalles de la página Actividad , se redirigirá a la página Información general .
* Algunas circunstancias excepcionales e inesperadas provocaban que faltara una tarjeta en la página Información general .
* El icono Recursos se muestra en la página Lista de programas para todos los clientes.
* Cuando había errores en el back-end, a veces parecía que una ejecución de canalización permanecía en el paso *Validar*.
* En determinadas circunstancias, se calculó incorrectamente la duración de la descripción del programa.

## Problemas conocidos {#known-issues}

* Las ramas creadas mediante el Asistente para proyectos de aplicación no pueden contener guiones.
* Es posible que la barra lateral de notificaciones del Adobe [!UICONTROL Experience Cloud] no cargue las notificaciones de forma coherente. Sin embargo, las notificaciones son visibles en el Adobe [!UICONTROL Experience Cloud] y, si se configuran, se envían por correo electrónico.

