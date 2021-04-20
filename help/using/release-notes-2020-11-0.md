---
title: Notas de la versión 2020.11.0
seo-title: Notas de la versión de AEM Cloud Manager para 2020.11.0
description: Siga esta página para obtener información sobre la versión 2020.11.0 de Cloud Manager
seo-description: Siga esta página para obtener información sobre la versión 2020.11.0 de AEM Cloud Manager
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 8%

---

# Notas de la versión 2020.11.0 {#release-notes-for}

La siguiente sección describe las notas de la versión generales de la versión [!UICONTROL Cloud Manager] 2020.11.0.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2020.11.0 de [!UICONTROL Cloud Manager] es el 12 de noviembre de 2020.

## Novedades {#whats-new}

* La pestaña **Learn** en Cloud Manager se actualiza con nuevas imágenes en la interfaz de usuario.

## Corrección de errores {#bug-fixes}

* Ciertos errores de implementación causados por el cliente ahora aparecerán explícitamente en los registros de implementación.

* La carga de dependencias realizada antes de la ejecución de la compilación requería la descarga de un complemento de Maven.

* El vínculo del pie de página de Cloud Manager para seleccionar un idioma ahora se desplaza a la ubicación correcta.

* A veces, durante la digitalización del código, el proceso SonarQube no se iniciaba. Esto se detectará automáticamente y se intentará reiniciar.

* Durante el proceso de rastreo del sitio utilizado en las pruebas de rendimiento, las solicitudes que agoten el tiempo de espera en los tres primeros niveles de profundidad se reintentarán automáticamente.