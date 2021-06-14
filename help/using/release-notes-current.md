---
title: Notas de la versión 2021.6.0
description: Siga esta página para obtener información sobre la versión 2021.6.0 de Cloud Manager
feature: Información de la versión
source-git-commit: 5ddbf718ad01b11dcba5dc2c5d1ab5d3cff2e9a9
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 4%

---

# Notas de la versión 2021.6.0 {#release-notes-for}

La siguiente sección describe las notas de la versión generales de la versión [!UICONTROL Cloud Manager] 2021.6.0.

>[!NOTE]
>Consulte las [Notas de la versión actuales](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) para ver las últimas notas de la versión de Cloud Manager en AEM as a Cloud Service.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2021.6.0 de [!UICONTROL Cloud Manager] es el 10 de junio de 2021.
La próxima versión está planificada para el 15 de julio de 2021.

## Novedades {#whats-new}

* Las pruebas de recursos y sitios ahora se ejecutarán en paralelo (cuando corresponda), lo que reducirá el tiempo total de ejecución de la canalización. Esta función se habilitará para los clientes en las próximas semanas.

* Las dependencias de Maven descargadas durante el paso de compilación ahora se almacenan en caché entre ejecuciones de canalización. Esta función se habilitará para los clientes en las próximas semanas.

* El nombre de rama predeterminado utilizado durante la creación del proyecto y en el comando push predeterminado mediante la administración de flujos de trabajo de Git se ha cambiado a `main`.

* Se ha actualizado la edición de la experiencia del programa en la interfaz de usuario. Consulte [Edición de un programa](/help/using/setting-up-program.md#editing-program) para obtener más información.

* La regla de calidad `ImmutableMutableMixCheck` se ha actualizado para clasificar los nodos `/oak:index` como inmutables.

* Las reglas de calidad `CQBP-84` y `CQBP-84--dependencies` se han consolidado en una sola regla. Como parte de esta consolidación, el análisis de dependencias identifica con mayor precisión los problemas en dependencias de terceros que se están implementando en el tiempo de ejecución de AEM.

* En algunas situaciones, un error al calcular la métrica Pruebas omitidas causaría errores en las ejecuciones de la canalización.

## Corrección de errores {#bug-fixes}

* Las definiciones de nodo JCR que contenían una nueva línea después del nombre del elemento raíz no se analizaron correctamente.

* La API de repositorios de lista no filtraba los repositorios eliminados.

* Se mostraba un mensaje de error incorrecto cuando se proporcionaba un valor no válido para el paso de programación.

* En algunos casos, cuando la ejecución de la canalización llegó al paso de implementación a producción y el usuario detuvo la ejecución, el mensaje de estado de implementación en la interfaz de usuario no reflejaba correctamente lo que estaba sucediendo.
