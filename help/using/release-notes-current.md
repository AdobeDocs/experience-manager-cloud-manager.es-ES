---
title: Notas de la versión 2020.11.0
seo-title: Notas de la versión de AEM Cloud Manager para 2020.11.0
description: Siga esta página para obtener información sobre la versión 2020.11.0 de Cloud Manager
seo-description: Siga esta página para obtener información sobre la versión 2020.11.0 de AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 30d782f5a095b1b07ec4f2039def9ba30a559325
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 7%

---

# Notas de la versión 2020.11.0 {#release-notes-for}

La siguiente sección describe las Notas de revisión generales de la versión 2020.11.0 [!UICONTROL Cloud Manager] .

## Fecha de la versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2020.11.0 es el 12 de noviembre de 2020.

## Novedades {#whats-new}

* La ficha **Aprender** de Cloud Manager se actualiza con nuevas imágenes en la interfaz de usuario.

## Corrección de errores {#bug-fixes}

* Determinados errores de implementación causados por el cliente aparecerán ahora explícitamente en los registros de implementación.

* La carga de dependencias realizada antes de la ejecución de la compilación requería la descarga de un complemento de Maven.

* El vínculo del pie de página del Administrador de nubes para seleccionar un idioma ahora se desplazará a la ubicación correcta.

* A veces, durante la digitalización del código, el proceso SonarQube no se inicio. Esto se detectará automáticamente y se intentará reiniciar.

* Durante el proceso de rastreo del sitio que se utiliza en las pruebas de rendimiento, las solicitudes cuyo tiempo de espera en los tres primeros niveles de inversión de profundidad se reintentarán automáticamente.