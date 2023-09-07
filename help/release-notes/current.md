---
title: Notas de la versión 2023.8.0
description: Estas son las notas de la versión 2023.8.0 de Cloud Manager.
feature: Release Information
source-git-commit: 26c4c945e18f21b812f65dbabc14a4e8ab9f6b43
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 100%

---


# Notas de la versión 2023.8.0 de Cloud Manager {#release-notes}

Esta página documenta las notas de la versión 2023.8.0 de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Para las notas de la última versión de Cloud Manager en AEM as a Cloud Service, consulte [Cloud Manager en las notas de la versión actuales de AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=es)

## Fecha de la versión {#release-date}

La fecha de lanzamiento de la versión 2023.8.0 de [!UICONTROL Cloud Manager] es el 10 de agosto de 2023. El próximo lanzamiento está programado para el 14 de septiembre de 2023.

## Novedades {#what-is-new}

* Se han realizado mejoras para la comprensión y la aparición de mensajes de error en la IU de Cloud Manager.

## Correcciones de errores {#bug-fixes}

* Se han solucionado los casos poco frecuentes de atasco de los procesos de [copia de contenido](/help/using/content-copy.md).
* Se ha resuelto un problema temporal de prueba para los clientes que no utilizan New Relic One.
* [Las reglas de calidad de código personalizadas](/help/using/custom-code-quality-rules.md) `SupportedRunmode` y `ImmutableMutableMixedPackage` se han eliminado de SonarQube, ya que solo son aplicables a AEM as a Cloud Service.
* Los usuarios ya no se encontrarán con canalizaciones atascadas que parecen estar en estado de ejecución.
* El menú **Entornos** ahora se cierra después de activar **[Copiar contenido](/help/using/content-copy.md)** modal.
* [La nueva ejecución de una canalización](/help/using/code-deployment.md#reexecute-deployment) ya no se permite si la ejecución anterior no tiene un `commitId` establecido en el estado de fase de compilación.
* Ahora se muestra un mensaje más comprensible para los errores poco frecuentes cuando un usuario hace clic en una canalización en las pantallas **Actividad** o **Canalización**.
