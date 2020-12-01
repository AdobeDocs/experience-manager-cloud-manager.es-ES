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
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 5%

---


# Notas de la versión 2018.9.0 {#release-notes-for}

La [!UICONTROL Cloud Manager] versión 2018.9.0 añade compatibilidad con una API basada en Adobe I/O, incluidos Eventos, para integrar el flujo de CD/CI de [!UICONTROL Cloud Manager] con otros sistemas. También comienza la reescritura de la capa UI en React.

## Fecha de la versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] versión 2018.9.0 es el 1 de noviembre de 2018.

## Novedades {#whats-new}

* **Canalización**  CI/CD: nueva API y sistema de Evento para integrar la canalización de CI/CD  [!UICONTROL Cloud Manager]de la empresa con otros sistemas. Consulte la [!UICONTROL Cloud Manager] Documentación de API (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) para obtener más información.

* **UI** : introducción de una nueva capa de interfaz de usuario que ofrece una mayor capacidad de respuesta.

## Corrección de errores {#bug-fixes}

* En [!UICONTROL Cloud Manager] 2018.8.0, las duraciones de las páginas de Actividad se enumeraban en minutos y horas, pero esa información no se reflejaba en el encabezado de la tabla.
* En raras ocasiones, los clientes no podían realizar el inicio del nuevo asistente del proyecto de la aplicación.
* La etiqueta del botón en el cuadro de diálogo del asistente del proyecto de la aplicación nuevo podía resultar confusa.
* En algunas circunstancias, si se hace clic en el botón Detalles de la página Actividad, se redirige a la página Información general.
* Algunas circunstancias excepcionales e inesperadas hicieron que faltara una tarjeta en la página Información general.
* El icono Recursos se mostraba en la página de Lista de Programas para todos los clientes.
* Cuando se producían errores en el back-end, a veces parecía que una ejecución de canalización permanecía en el paso *Validar*.
* En determinadas circunstancias, la longitud de la descripción del programa se calculó erróneamente.

## Problemas conocidos {#known-issues}

* Las ramas creadas con el Asistente para proyectos de aplicación no pueden contener guiones.
* Es posible que la barra lateral de notificaciones de Adobe [!UICONTROL Experience Cloud] no cargue las notificaciones de forma coherente. Sin embargo, las notificaciones son visibles en el Adobe [!UICONTROL Experience Cloud] y, si están configuradas, se seguirán enviando por correo electrónico.

