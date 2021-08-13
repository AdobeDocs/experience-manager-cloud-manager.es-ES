---
title: Notas de la versión 2021.8.0
description: Siga esta página para obtener información sobre la versión 2021.8.0 de Cloud Manager
feature: Información de la versión
source-git-commit: c4deb06615652736ff7584566507a2b42a88bfb1
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 8%

---

# Notas de la versión 2021.8.0 {#release-notes-for}

La siguiente sección describe las notas de la versión generales de la versión [!UICONTROL Cloud Manager] 2021.8.0.

>[!NOTE]
>Consulte las [Notas de la versión actuales](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) para ver las últimas notas de la versión de Cloud Manager en AEM as a Cloud Service.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2021.8.0 de [!UICONTROL Cloud Manager] es el 12 de agosto de 2021.
La próxima versión está planificada para el 9 de septiembre de 2021.

## Novedades {#whats-new}

* Capacidad de autoservicio para permitir a los usuarios crear y administrar varios repositorios a través de la interfaz de usuario de Cloud Manager.

* SonarQube leía innecesariamente los datos del historial de Git. En bases de código grandes, esto podría provocar una penalización innecesaria del rendimiento de la compilación.

* Ahora hay una API disponible para invalidar la caché de dependencias de Maven por canalización.

* La versión del tipo de archivo del proyecto AEM utilizado por Cloud Manager se ha actualizado a la versión 29.

## Corrección de errores {#bug-fixes}

* En ocasiones, cuando una canalización se activa dos veces por algún motivo, el resultado es que una de las ejecuciones falla con el error *no puede actualizar el estado de ejecución de la canalización*.
