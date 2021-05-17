---
title: Notas de la versión 2021.5.0
description: Siga esta página para obtener información sobre la versión 2021.5.0 de Cloud Manager
feature: Información de la versión
source-git-commit: 83fcc49c7e3e3742930a7179b27f899bff3c4ae1
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 5%

---

# Notas de la versión 2021.5.0 {#release-notes-for}

La siguiente sección describe las notas de la versión generales de la versión [!UICONTROL Cloud Manager] 2021.5.0.

>[!NOTE]
>Consulte las [Notas de la versión actuales](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) para ver las últimas notas de la versión de Cloud Manager en AEM as a Cloud Service.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2021.5.0 de [!UICONTROL Cloud Manager] es el 6 de mayo de 2021.
La próxima versión está planificada para el 3 de junio de 2021.

## Novedades {#whats-new}

* La regla de calidad PackageOverlaps ahora detecta casos en los que el mismo paquete se implementó varias veces, es decir, en varias ubicaciones incrustadas, en el mismo conjunto de paquetes implementado.

* El extremo del repositorio en la API pública ahora incluye la URL de Git.

* En el flujo de trabajo Editar programa, el usuario solo podrá establecer valores de KPI no decimales.

* Se han resuelto errores intermitentes encontrados al insertar el código en el Adobe Git.

* Se ha actualizado la experiencia Editar programa.

## Corrección de errores {#bug-fixes}

* En lugar de eliminar las variables &quot;eliminadas&quot;, la API de variables de canalización solo las marcaría con el estado &quot;ELIMINADO&quot;.

* Algunos problemas de calidad del tipo de hueso de código impactaban incorrectamente en la clasificación de fiabilidad.

* Cuando se inició la ejecución de una canalización entre la medianoche y la 01:00 UTC, la versión del artefacto generada por Cloud Manager no estaba buena a la versión creada el día anterior.

* Algunos clientes de Adobe Managed Services (AMS) no podían crear nuevos proyectos en Adobe I/O Developer Console mediante la API de Cloud Manager.
