---
title: Notas de la versión 2021.7.0
description: Siga esta página para obtener información sobre la versión 2021.7.0 de Cloud Manager
feature: Información de la versión
source-git-commit: fec742eb023e9811ee80951bd25fc2023df52d66
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 6%

---

# Notas de la versión 2021.7.0 {#release-notes-for}

La siguiente sección describe las notas de la versión generales de la versión [!UICONTROL Cloud Manager] 2021.7.0.

>[!NOTE]
>Consulte las [Notas de la versión actuales](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) para ver las últimas notas de la versión de Cloud Manager en AEM as a Cloud Service.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2021.7.0 de [!UICONTROL Cloud Manager] es el 15 de julio de 2021.
La próxima versión está planificada para el 12 de agosto de 2021.

## Novedades {#whats-new}

* Los clientes ahora pueden utilizar Azul 8 y 11 JDK para sus procesos de compilación de Cloud Manager y pueden seleccionar usar uno de estos JDK para complementos Maven compatibles con las cadenas de herramientas *o* para toda la ejecución del proceso Maven.

* La dirección IP de salida saliente ahora se registrará en el archivo de registro de paso de compilación.

* Los botones **Administrar Git** se han cambiado a **Información de Git de acceso** y el cuadro de diálogo se ha actualizado visualmente.

* La versión del tipo de archivo del proyecto AEM utilizado por Cloud Manager se ha actualizado a la versión 28.

* Algunas reconfiguraciones de topología inesperadas podrían provocar que los informes de prueba detallados ya no estén disponibles en la página de detalles de ejecución de la canalización.

## Corrección de errores {#bug-fixes}

* La navegación manual a la página de detalles de ejecución para una ejecución no existente no mostraba un error, solo una pantalla de carga interminable.

* En algunos casos, el reintento automático de contenedores con errores que se utiliza en el rendimiento de Sites no tendría efecto durante 2 horas, lo que provocaba un error de prueba.

## Problemas conocidos {#known-issues}

Los clientes que cambien a utilizar Azul JDKs deben tener en cuenta que no todas las aplicaciones existentes se compilarán sin error en Azul JDK. Se recomienda realizar pruebas locales antes de cambiar.