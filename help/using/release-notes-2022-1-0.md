---
title: Notas de la versión 2022.01.0
description: Estas son las notas de la versión de Cloud Manager 2022.01.0.
feature: Release Information
source-git-commit: 099a4490e3a8578b9f3485fd1514d1e97db977ab
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 6%

---

# Notas de la versión de Cloud Manager 2021.12.0 {#release-notes}

En la siguiente sección se describen las notas de la versión generales de [!UICONTROL Cloud Manager] versión 2022.01.0.

>[!NOTE]
>
>Para las notas de la última versión de Cloud Manager en AEM as a Cloud Service, consulte [Cloud Manager en las notas de la versión actuales de AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Fecha de la versión {#release-date}

La fecha de la versión de [!UICONTROL Cloud Manager] la versión 2022.01.0 es el 20 de enero de 2022. La próxima versión está prevista para el 10 de febrero de 2022.

## Novedades {#whats-new}

* Cloud Manager [evite la reconstrucción del código base cuando detecte que se utiliza la misma confirmación git](/help/using/setting-up-project.md#build-artifact-reuse) en varias ejecuciones de canalización de pila completa.
* Al generar una contraseña de git, se muestra la fecha de caducidad.

## Corrección de errores {#bug-fixes}

* Se han corregido casos poco frecuentes de errores de canalización de falsos positivos.
* Para los programas con un solo repositorio, la pantalla de ejecución de la canalización ahora mostrará el nombre del repositorio.
