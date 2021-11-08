---
title: Notas de la versión 2021.11.0
description: Siga esta página para obtener información sobre la versión 2021.11.0 de Cloud Manager
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: e6e5a17c16c42e0b0ed5aedd2f9a6360fd81d8cd
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Notas de la versión 2021.10.0 {#release-notes-for}

En la siguiente sección se describen las notas de la versión generales de [!UICONTROL Cloud Manager] Versión 2021.11.0.

>[!NOTE]
>Consulte [Notas de la versión actual](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) para ver las notas de la última versión de Cloud Manager en AEM as a Cloud Service.

## Fecha de la versión {#release-date}

La fecha de lanzamiento de [!UICONTROL Cloud Manager] La versión 2021.11.0 es el 4 de noviembre de 2021.
La próxima versión está planificada para el 9 de diciembre de 2021.

## Novedades {#whats-new}

* El ID de confirmación de Git ahora se mostrará en los detalles de ejecución de la canalización, lo que facilita el seguimiento del código creado.

* La variable `x-request-id` el encabezado de respuesta ahora está visible en API Playground en [www.adobe.io](https://www.adobe.io/). Este encabezado es útil cuando se envían problemas de atención al cliente para la resolución de problemas.

* Como usuario, veo que la tarjeta de canalización con cero canalizaciones me proporciona la guía adecuada.

* Ya está disponible una nueva página de actividad donde se pueden ver actividades como las ejecuciones de canalización y código junto con los detalles asociados. Con el tiempo, las actividades enumeradas en esta página se ampliarán en alcance junto con los detalles proporcionados.

* Ya está disponible una nueva página de canalizaciones con una ventana emergente de estado al pasar el ratón por encima para facilitar la vista del resumen de detalles. Las ejecuciones de canalización se pueden ver junto con los detalles asociados.

* La API de edición de canalización ahora admite la configuración de las rutas de descarga e invalidación de Dispatcher.

* La API Editar canalización ahora admite el cambio del entorno utilizado en las fases de implementación.

* Se ha introducido una optimización en el proceso de digitalización de OakPal para paquetes grandes.

* El archivo CSV del problema de calidad ahora contendrá la marca de tiempo para cada problema de calidad.

* El botón Administrar de la página Entornos ya no estará visible en la interfaz de usuario.

## Corrección de errores {#bug-fixes}

* Algunas configuraciones de compilación no ortodoxas tuvieron como resultado que se almacenaran archivos innecesarios en la caché de artefactos Maven de la canalización, lo que resultó en E/S de red superfluas al iniciar y detener el contenedor de compilación.

* La API del PATCH de canalización falla si la fase de implementación no existe.

* La variable `ClientlibProxyResourceCheck` la regla de calidad producía problemas falsos positivos cuando había bibliotecas cliente con rutas base comunes.

* El mensaje de error cuando se ha alcanzado el número máximo de repositorios no especificaba el motivo del error.

* En casos excepcionales, las canalizaciones fallaban debido a la gestión inadecuada de reintentos de ciertos códigos de respuesta.
