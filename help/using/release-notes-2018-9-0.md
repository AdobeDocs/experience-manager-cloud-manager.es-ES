---
title: Notas de la versión de 2018.9.0
seo-title: Notas de la versión de AEM Cloud Manager para 2018.8.0
description: Siga esta página para obtener información sobre la versión 2018.9.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2018.9.0 de AEM Cloud Manager.
uuid: 3af5808f-828f-4846-abeja4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas de la versión
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
translation-type: tm+mt
source-git-commit: 949d3cf0239a02875ba4ad1888e081f104dec2e2

---


# Notas de la versión de 2018.9.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2018.9.0 añade compatibilidad con una API basada en Adobe I/O, incluidos eventos, para integrar el flujo de CD/CI [!UICONTROL Cloud Manager]de Adobe con otros sistemas. También comienza la reescritura de la capa UI en React.

## Fecha de lanzamiento {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2018.9.0 es el 1 de noviembre de 2018.

## Novedades {#whats-new}

* **Canalización** de CI/CD - Nueva API y sistema de eventos para la integración [!UICONTROL Cloud Manager]de la canalización de CI/CD con otros sistemas. Consulte la documentación de [!UICONTROL Cloud Manager] la API (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) para obtener más información.

* **UI** : introducción de una nueva capa de interfaz de usuario que ofrece una mayor capacidad de respuesta y rendimiento.

## Corrección de errores {#bug-fixes}

* En [!UICONTROL Cloud Manager] 2018.8.0, las duraciones de la página Actividad se enumeraban en minutos y horas, pero esa información no se reflejaba en el encabezado de la tabla.
* En raras ocasiones, los clientes no podían iniciar el nuevo asistente del proyecto de la aplicación.
* La etiqueta del botón en el cuadro de diálogo del asistente del proyecto de la aplicación nuevo podía resultar confusa.
* En algunas circunstancias, hacer clic en el botón Detalles de la página Actividad se redirigiría a la página Información general.
* Algunas circunstancias excepcionales e inesperadas hicieron que faltara una tarjeta en la página Información general.
* El icono Recursos se muestra en la página Lista de programas para todos los clientes.
* Cuando se producían errores en el back-end, a veces parecía que la ejecución de una canalización permanecía en el paso *Validar* .
* En determinadas circunstancias, se calculó incorrectamente la duración de la descripción del programa.

## Problemas conocidos {#known-issues}

* Las ramas creadas con el Asistente para proyectos de aplicación no pueden contener guiones.
* Es posible que la barra lateral de notificaciones de Adobe [!UICONTROL Experience Cloud] no cargue las notificaciones de forma coherente. Sin embargo, las notificaciones son visibles en Adobe [!UICONTROL Experience Cloud] y, si están configuradas, se enviarán por correo electrónico.

