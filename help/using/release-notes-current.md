---
title: Notas de la versión 2021.2.0
seo-title: Notas de la versión de AEM Cloud Manager para 2021.2.0
description: Siga esta página para obtener información sobre la versión 2021.2.0 de Cloud Manager
seo-description: Siga esta página para obtener información sobre la versión 2021.2.0 de AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 88b17f05a577b5c46b5b352d7340228353b49a38
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 5%

---

# Notas de la versión 2020.12.0 {#release-notes-for}

La siguiente sección describe las Notas de revisión generales de la versión 2021.2.0 de [!UICONTROL Cloud Manager].

## Fecha de la versión {#release-date}

La fecha de versión de la [!UICONTROL Cloud Manager] versión 2021.2.0 es el 11 de febrero de 2021.

## Novedades {#whats-new}

* El arquetipo del proyecto AEM utilizado en la creación de proyectos y Simuladores para pruebas se ha actualizado a la versión 25.

* La lista de las API obsoletas identificadas durante el análisis de código se ha refinado para incluir clases y métodos adicionales que ya no se utilizan en las últimas versiones del SDK de Cloud Service.

* Las implementaciones de producción ahora se implementan en paralelo en las instancias de publicación y envío emparejadas.

* SonarQube perfil para Cloud Manager actualizado para eliminar Sonar rule squid:S2142. Esto ya no entrará en conflicto con las comprobaciones de interrupción del subproceso

* Las propiedades establecidas en los archivos pom.xml del cliente con el prefijo sonar y ahora se eliminarán dinámicamente para evitar errores de compilación y de análisis de calidad.

## Corrección de errores {#bug-fixes}

* En ocasiones, la canalización CI/CD (implementación) falló durante un paso de prueba de rendimiento debido a un contenedor que ejecutaba la prueba de carga y que encontró un error.

* En ocasiones, el contenedor de la prueba de carga puede informar de que la ejecución ha fallado aunque solo se produzca una excepción. El error solo se notificará si no se puede restaurar el proceso de prueba.

* Determinadas discrepancias de mayúsculas y minúsculas entre la forma en que se almacenan los nombres de entornos podrían provocar errores de prueba de rendimiento.

* Algunos errores de canalización se notificaron incorrectamente como errores de canalización.