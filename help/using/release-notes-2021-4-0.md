---
title: Notas de la versión 2021.4.0
description: Siga esta página para obtener información sobre la versión 2021.4.0 de Cloud Manager
feature: Release Information
source-git-commit: 09dd8fe608d95cd9dbc95129cf86b9693c2839b5
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 6%

---

# Notas de la versión 2021.4.0 {#release-notes-for}

En la siguiente sección se describen las notas de la versión generales de [!UICONTROL Cloud Manager] Versión 2021.4.0.

## Fecha de la versión {#release-date}

La fecha de lanzamiento de [!UICONTROL Cloud Manager] La versión 2021.4.0 es el 8 de abril de 2021.

## Novedades {#whats-new}

* El tiempo de espera de la solicitud para los usuarios virtuales de prueba de rendimiento se ha aumentado de 20 segundos a 60 segundos.

* El botón Administrar Git se muestra en la tarjeta Canalizaciones aunque no se hayan configurado canalizaciones.

* Durante el paso de implementación de la página Ejecución de la canalización , el usuario podrá ver los pasos de implementación completados y futuros, además del paso actual en la interfaz de usuario para *En curso* estado.

* La versión del arquetipo de proyecto AEM utilizado por Cloud Manager se ha actualizado a la versión 27.

* Se ha aclarado el mensaje de error al iniciar una canalización cuando se eliminaba un entorno.

* Los paquetes OSGi proporcionados por los proyectos de Eclipse ahora se excluyen de la regla `CQBP-84--dependencies`.

## Corrección de errores {#bug-fixes}

* Errores transitorios raros que pueden ocurrir en *Prueba de recursos* en la canalización de producción.

* Una barra diagonal en la prueba de carga de la canalización de producción estaba causando un error 404.

* La variable `Runmode` la comprobación estaba produciendo falsos positivos en nodos que no son de carpeta.