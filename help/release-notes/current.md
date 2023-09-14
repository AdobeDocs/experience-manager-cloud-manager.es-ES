---
title: Notas de la versión 2023.9.0
description: Estas son las notas de la versión 2023.9.0 de Cloud Manager.
feature: Release Information
source-git-commit: a3e926fa13d54da1322f3a5219519fae07ddb273
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 52%

---


# Notas de la versión 2023.9.0 de Cloud Manager {#release-notes}

Esta página documenta las notas de la versión 2023.9.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Para las notas de la última versión de Cloud Manager en AEM as a Cloud Service, consulte [Cloud Manager en las notas de la versión actuales de AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=es)

## Fecha de la versión {#release-date}

La fecha de lanzamiento de la versión 2023.9.0 de [!UICONTROL Cloud Manager] es el 14 de septiembre de 2023. El próximo lanzamiento está programado para el 5 de octubre de 2023.

## Novedades {#what-is-new}

* Esta versión consiste en la corrección de errores únicamente para Cloud Manager.

## Correcciones de errores {#bug-fixes}

* Cuando se elimina un programa, también se elimina cualquier canalización asociada en ejecución, lo que garantiza que la canalización no se designe incorrectamente como estado de error.
* En ocasiones, cuando se &#39;completan&#39; todos los pasos de la ejecución de una canalización, el estado de la canalización se ve como &quot;en ejecución&quot;, lo que hace que parezca que está en un estado atascado. Ahora se ve como &#39;Completo&#39;.
* Para las ramas de repositorio generadas mediante el tipo de archivo del generador de código, la canalización CI/CD falla.
