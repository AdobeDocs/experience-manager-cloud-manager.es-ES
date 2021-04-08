---
title: Notas de la versión 2021.4.0
description: Siga esta página para obtener información sobre la versión 2021.4.0 de Cloud Manager
feature: Información de la versión
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
translation-type: tm+mt
source-git-commit: 0c33fd9f1af4c98564c9fd14a468fc3bf27744ee
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 7%

---

# Notas de la versión 2021.4.0 {#release-notes-for}

En la siguiente sección se describen las notas de la versión generales de [!UICONTROL Cloud Manager] versión 2021.4.0.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2021.4.0 de [!UICONTROL Cloud Manager] es el 8 de abril de 2021.
La próxima versión está planificada para el 06 de mayo de 2021.

## Novedades {#whats-new}

* El tiempo de espera de la solicitud para los usuarios virtuales de prueba de rendimiento se ha aumentado de 20 segundos a 60 segundos.

* El botón Administrar Git se muestra en la tarjeta Canalizaciones aunque no se hayan configurado canalizaciones.

* Durante el paso de implementación de la página Ejecución de la canalización , el usuario podrá ver los pasos de implementación completados y futuros, además del paso actual en la interfaz de usuario para el estado *In Progress* .

* La versión del arquetipo de proyecto AEM utilizado por Cloud Manager se ha actualizado a la versión 27.

* Se ha aclarado el mensaje de error al iniciar una canalización cuando se eliminaba un entorno.

* Los paquetes OSGi proporcionados por los proyectos de Eclipse ahora se excluyen de la regla.

## Corrección de errores {#bug-fixes}

* Errores poco frecuentes y transitorios que pueden producirse en el paso Prueba de recursos de la canalización de producción.

* Una barra diagonal en la prueba de carga de la canalización de producción estaba causando un error 404.

* La comprobación `Runmode` estaba produciendo falsos positivos en nodos que no son de carpeta.