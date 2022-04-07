---
title: Notas de la versión 2022.4.0
description: Estas son las notas de la versión de Cloud Manager 2022.4.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 3d4eea13c0f2e9c4030bbfd3b7c5c25336548498
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 2%

---


# Notas de la versión para Cloud Manager versión 2022.4.0 {#release-notes}

Esta página documenta las notas de la versión de [!UICONTROL Cloud Manager] versión 2022.4.0.

>[!NOTE]
>
>Para las notas de la última versión de Cloud Manager en AEM as a Cloud Service, consulte [Cloud Manager en las notas de la versión actuales de AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Fecha de la versión {#release-date}

La fecha de la versión de [!UICONTROL Cloud Manager] la versión 2022.4.0 es 7 de abril de 2022. La próxima versión está prevista para el 5 de mayo de 2022.

## Novedades {#what-is-new}

* Se han implementado mejoras en la duración y la tasa de éxito de los pasos de compilación de la canalización, que se implementarán gradualmente para todos los clientes durante el mes de abril.
* Ahora puede encontrar fácilmente una rama de Git escribiendo los primeros caracteres del nombre en el campo de entrada en el asistente de añadir y editar canalización y seleccionando entre coincidencias sugeridas.
* La variable **Canalizaciones** ahora tiene paginación para mejorar la capacidad de uso de los programas con un gran número de canalizaciones.
   * 50 filas por página se muestran en la tabla.
* La versión de [Tipo de archivo del proyecto AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) utilizado por Cloud Manager se ha actualizado a la versión 36.
* Oracle JDK es ahora el JDK predeterminado para el desarrollo y funcionamiento de aplicaciones AEM. El proceso de creación de Cloud Manager cambiará automáticamente al uso de JDK de Oracle, aunque se haya seleccionado explícitamente una opción alternativa en la cadena de herramientas de Maven.
   * Para obtener más información sobre cómo cambiar a Oracle JDK, consulte [la documentación Entorno de compilación .](/help/using/build-environment-details.md#using-java-support)
   * Consulte [Preguntas frecuentes sobre la política de asistencia de Java para Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-65/assets/Java_Policy_for_Adobe_Experience_Manager.pdf) para abordar preguntas comunes sobre este cambio.
