---
title: Notas de la versión 2021.12.0
description: Estas son las notas de la versión de Cloud Manager 2021.12.0.
feature: Release Information
source-git-commit: 910def6d82c09e0220a50a3cb34a61f2c7284cb9
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 3%

---

# Notas de la versión de Cloud Manager 2021.12.0 {#release-notes}

En la siguiente sección se describen las notas de la versión generales de [!UICONTROL Cloud Manager] versión 2021.12.0.

>[!NOTE]
>
>Para las notas de la última versión de Cloud Manager en AEM as a Cloud Service, consulte [Cloud Manager en las notas de la versión actuales de AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Fecha de la versión {#release-date}

La fecha de la versión de [!UICONTROL Cloud Manager] la versión 2021.12.0 es el 16 de diciembre de 2021. La próxima versión está planificada para enero de 2022.

## Novedades {#whats-new}

* El hash de confirmación, que ya está visible en la interfaz de usuario, ahora también se proporciona en la API .
* La página Actividad ahora incluye una ventana emergente para la ejecución de canalizaciones que proporciona un resumen de los detalles de la canalización de un vistazo.
* Se agregaron actualizaciones para incluir detalles adicionales presentados en la página Actividades .
* La pestaña Información de Cloud Manager ahora incluye acceso rápido a las guías de API y a los recursos asociados.
* Un usuario con la función Administrador de implementación ahora puede iniciar el asistente de creación de proyectos/ramas para un repositorio sin ramas desde el menú de acción de la página repositorios.
* El administrador de implementación, que se encuentra en el flujo de trabajo de añadir o editar canalización, ahora está informado sobre cómo crear una rama o proyecto si el repositorio seleccionado no tiene ramas.
* En la ventana Editar canalización de producción , cuando hay más de un entorno de etapa para la producción, hay disponible un menú desplegable para la selección de entorno.

## Corrección de errores {#bug-fixes}

* Las canalizaciones de producción de pila completa siguen denominándose &quot;Canalización de producción&quot; incluso cuando el usuario introduce un nombre diferente en el campo de nombre.
