---
title: Notas de la versión 2026.1.0 de Cloud Manager
description: Obtenga información sobre la versión de Cloud Manager 2026.1.0 en Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 28841719e820e47577b411a4034ebc7a8e1bb556
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 51%

---

# Notas de la versión de Cloud Manager 2026.1.0 en Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Obtenga información sobre la versión de [!UICONTROL Cloud Manager] 2026.1.0 en Adobe Managed Services.

Consulte también las [notas de la versión actual de Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/release-notes/home).

## Fechas de lanzamiento {#release-date}

La fecha de lanzamiento de la versión 2026.1.0 de [!UICONTROL Cloud Manager] es el viernes, 22 de enero de 2026.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La próxima versión planificada es el viernes, 05 de febrero de 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Novedades {#what-is-new}

* **Las canalizaciones de configuración ahora admiten secretos administrados**

  Los usuarios ahora pueden agregar y administrar secretos directamente en las canalizaciones de configuración de Cloud Manager. Estos secretos anulan de forma segura los valores de las especificaciones de configuración de la canalización y admiten implementaciones flexibles y específicas del entorno.

  ![Opción Ver/Editar variables en el menú desplegable de una canalización seleccionada](/help/release-notes/assets/view-edit-variables-option.png)
  *Opción Ver/Editar variables en el menú desplegable de una canalización seleccionada.*

  ![Cuadro de diálogo Configuración de variables &#x200B;](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*Cuadro de diálogo Configuración de variables.*

* **Mayor estabilidad, rendimiento y confiabilidad**

  Esta versión incluye actualizaciones de optimización y mantenimiento que mejoraron la estabilidad, el rendimiento y la fiabilidad de Cloud Manager.


## Programas Beta {#beta-program}

Participe en los programas de Beta de Cloud Manager para obtener acceso exclusivo a las próximas funciones antes de su lanzamiento general.

Actualmente están disponibles las siguientes oportunidades:

### Extensibilidad y personalización de Experience Hub {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) sirve como punto de entrada a AEM, personalizado para las necesidades de la organización. Informe a Adobe sobre las extensiones de la interfaz de usuario de AEM existentes para que puedan ayudarle a habilitarlas en Experience Hub con el mínimo esfuerzo.

![Diagrama del flujo de trabajo de extensibilidad y personalización de Experience Hub](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Incruste experiencias personalizadas en Experience Hub para ampliar y personalizar el tablero de su organización. Además de los widgets integrados de Adobe, añada los suyos propios mediante el marco de trabajo [Extensibilidad de la interfaz de usuario](https://developer.adobe.com/uix/docs/). Cree aplicaciones de interfaz de usuario basadas en JavaScript y envíelas a sus usuarios para que cumplan con los requisitos y flujos de trabajo específicos de la empresa.

¿Le interesa la versión Beta? Envíe un correo electrónico a [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) con su identificador de organización de Adobe y una breve descripción de la personalización que desea crear.

### Compilaciones más rápidas con almacenamiento en caché de módulos {#quick-build-cm-pipelines}

Un nuevo modelo de compilación solo compila los módulos modificados (en lugar de todo el repositorio) mediante el almacenamiento en caché a nivel de módulo para acortar los tiempos de compilación. Se aplica a las canalizaciones de calidad de código, de pila completa y de solo ensayo.

![Editar canalización que no sea de producción en el cuadro de diálogo que muestra las dos opciones de Estrategia de compilación que son Versión completa y Versión inteligente](/help/release-notes/assets/non-production-pipeline-edit.png)
*Editar canalización que no sea de producción en el cuadro de diálogo que muestra las dos opciones de estrategia de compilación, compilación completa y compilación inteligente.*

En el cuadro de diálogo **Agregar o editar canalización**, en la ficha **Código Source**, una nueva sección de **Estrategia de compilación** le permite elegir una de las siguientes opciones de compilación:

* **Compilación completa**: genera todos los módulos del repositorio en cada ejecución.
* **Compilación inteligente**: genera solo módulos que han cambiado desde la última confirmación, lo que acorta el tiempo de compilación general.

Usted controla qué canalizaciones utilizan **Smart Build**. Durante la versión beta, esta opción solo aparece para las canalizaciones **Calidad del código** y **Implementación de desarrolladores**.

¿Le interesa? Envíe un correo electrónico a [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) con su identificador de organización de Adobe y el identificador de programa.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## Correcciones de errores {#bug-fixes}

No hay correcciones de errores significativas en la versión de enero de 2026 de Cloud Manager en AMS.

<!--
Known Issues {#known-issues}

* A -->
