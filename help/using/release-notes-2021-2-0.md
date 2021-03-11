---
title: Notas de la versión 2021.2.0
seo-title: Notas de la versión de AEM Cloud Manager para 2021.2.0
description: Siga esta página para obtener información sobre la versión 2021.2.0 de Cloud Manager
seo-description: Siga esta página para obtener información sobre la versión 2021.2.0 de AEM Cloud Manager
translation-type: tm+mt
source-git-commit: b5233e1932888b515d8dc26a6493cbd26686bc3c
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 4%

---

# Notas de la versión 2021.2.0 {#release-notes-for}

En la siguiente sección se describen las notas de la versión generales de [!UICONTROL Cloud Manager] versión 2021.2.0.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2021.2.0 de [!UICONTROL Cloud Manager] es el 11 de febrero de 2021.

## Novedades {#whats-new}

* El tipo de archivo del proyecto AEM utilizado en la creación de proyectos y entornos limitados se ha actualizado a la versión 25.

* La lista de API obsoletas identificadas durante la digitalización del código se ha refinado para incluir clases y métodos adicionales que ya no se utilizan en las últimas versiones del SDK de Cloud Service.

* Las implementaciones de producción ahora se implementan en paralelo en las instancias de publicación y Dispatcher emparejadas.

* El perfil de SonarQube para Cloud Manager se ha actualizado para eliminar la regla Sonar `squid:S2142`. Esto ya no entrará en conflicto con las comprobaciones de interrupción de subprocesos.

* Las propiedades configuradas en los archivos `pom.xml` del cliente con el prefijo sonar ahora se eliminarán dinámicamente para evitar errores de análisis de calidad y compilación.

* Se han agregado reglas de calidad de código adicionales para cubrir los problemas de compatibilidad con el Cloud Service.

## Corrección de errores {#bug-fixes}

* En ocasiones, la canalización CI/CD (implementación) falló durante un paso de prueba de rendimiento debido a un contenedor que ejecuta la prueba de carga y que encontró un error.

* En ocasiones, el contenedor de prueba de carga puede notificar que la ejecución ha fallado aunque solo se produzca una excepción. El error solo se notificará si no se puede restaurar el proceso de prueba.

* Ciertas discrepancias de mayúsculas y minúsculas entre la forma en que se almacenan los nombres de entornos podrían provocar errores en las pruebas de rendimiento.

* Algunos errores de canalización se notificaron incorrectamente como errores de canalización.