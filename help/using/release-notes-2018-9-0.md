---
title: Notas de la versión de 2018.9.0
seo-title: Notas de la versión de AEM Cloud Manager para 2018.9.0
description: Siga esta página para obtener información sobre la versión 2018.9.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2018.9.0 de AEM Cloud Manager.
uuid: 3 af 5808 f -828 f -4846-bee 4-1 e 62194 b 48 ad
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas de la versión
discoiquuid: 85 a 1 dcf 3-2 eef -4 ba 8-b 4 d 1-09 e 4 a 88 c 7 bd 0
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notas de la versión de 2018.9.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2018.9.0 incorpora compatibilidad con una API basada en Adobe I/O, incluidos Eventos, para integrar [!UICONTROL Cloud Manager]la canalización CI/CD con otros sistemas. También comienza el reescritura de la capa UI en React.

## Fecha de versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2018.9.0 es el 01 de noviembre de 2018.

## Novedades {#whats-new}

* **Pipeline CI/CD** - Nueva API y sistema de eventos para integrar [!UICONTROL Cloud Manager]la canalización CI/CD con otros sistemas. Consulte Documentación [!UICONTROL Cloud Manager] de API (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) para obtener más información.

* **UI** - Introducción a la nueva capa de interfaz de usuario que ofrece mayor capacidad de respuesta y rendimiento.

## Corrección de errores {#bug-fixes}

* En [!UICONTROL Cloud Manager] la versión 2018.8.0, las duraciones de la página Actividad se enumeraban en minutos y horas, pero dicha información no se reflejaba en el encabezado de la tabla.
* En casos excepcionales, los clientes no podían iniciar el nuevo asistente para proyectos de aplicación.
* La etiqueta de botón en el cuadro de diálogo del asistente para proyectos de aplicación nueva era confuso.
* En algunas circunstancias, al hacer clic en el botón Detalles de la página Actividad se redirigiría a la página Información general.
* Algunas circunstancias excepcionales e inesperadas dieron como resultado una tarjeta que falta en la página Información general.
* El icono Recursos se mostraba en la página Lista de programas para todos los clientes.
* Cuando había errores de servidor, a veces aparecía una ejecución de flujo en el *paso Validar* .
* En determinadas circunstancias, la longitud de la descripción del programa no se calculaba correctamente.

## Problemas conocidos {#known-issues}

* Las ramas creadas con el Asistente para proyectos de aplicación no pueden contener guiones.
* Es posible que la barra lateral [!UICONTROL Experience Cloud] de notificación de Adobe no cargue notificaciones de forma coherente. Las notificaciones, sin embargo, son visibles en Adobe [!UICONTROL Experience Cloud] y, si se configuran, se seguirán enviando por correo electrónico.

