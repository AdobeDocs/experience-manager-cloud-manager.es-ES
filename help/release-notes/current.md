---
title: Notas de la versión de Cloud Manager 2026.3.0
description: Obtenga información acerca de la versión de Cloud Manager 2026.3.0 en Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: b7e651b72d1943aef69c1c69915d4752a6163931
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 16%

---

# Notas de la versión de Cloud Manager 2026.3.0 en Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Obtenga información acerca de la versión de [!UICONTROL Cloud Manager] 2026.3.0 en Adobe Managed Services.

Consulte también las [notas de la versión actual de Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/release-notes/home).

## Fechas de lanzamiento {#release-date}

La fecha de la versión de [!UICONTROL Cloud Manager] 2026.3.0 es el jueves, 5 de marzo de 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La próxima versión planificada es el jueves, 2 de abril de 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Novedades {#what-is-new}

* **Compatibilidad con la extensibilidad de la IU en AEM Experience Hub**
Ya está habilitada la compatibilidad con las extensiones de IU en [AEM Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub), lo que permite a los desarrolladores ampliar la interfaz con funcionalidad y widgets personalizados creados con Adobe App Builder.

  Para obtener más información, consulta [AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/).

* **Las canalizaciones de configuración ahora admiten secretos administrados**

  Los usuarios ahora pueden agregar y administrar secretos directamente en las canalizaciones de configuración de Cloud Manager. Estos secretos anulan de forma segura los valores de las especificaciones de configuración de la canalización y admiten implementaciones flexibles y específicas del entorno.

  ![Opción Ver/Editar variables en el menú desplegable de una canalización seleccionada](/help/release-notes/assets/view-edit-variables-option.png)
  *Opción Ver/Editar variables en el menú desplegable de una canalización seleccionada.*

  ![Cuadro de diálogo Configuración de variables ](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*Cuadro de diálogo Configuración de variables.*

* **Mayor estabilidad, rendimiento y confiabilidad**

  Esta versión incluye actualizaciones de optimización y mantenimiento que mejoraron la estabilidad, el rendimiento y la fiabilidad de Cloud Manager.


## Programas Beta {#beta-program}

Participe en los programas de Beta de Cloud Manager para obtener acceso exclusivo a las próximas funciones antes de su lanzamiento general.

Actualmente están disponibles las siguientes oportunidades:

<!--
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

### Compilaciones más rápidas con almacenamiento en caché de módulos {#quick-build-cm-pipelines}

Un nuevo modelo de compilación solo compila los módulos modificados (en lugar de todo el repositorio) mediante el almacenamiento en caché a nivel de módulo para acortar los tiempos de compilación. Se aplica a las canalizaciones Calidad del código y Pila completa.

![Editar canalización que no sea de producción en el cuadro de diálogo que muestra las dos opciones de Estrategia de compilación que son Versión completa y Versión inteligente](/help/release-notes/assets/non-production-pipeline-edit.png)
*Editar canalización que no sea de producción en el cuadro de diálogo que muestra las dos opciones de estrategia de compilación, compilación completa y compilación inteligente.*

En el cuadro de diálogo **Agregar o editar canalización**, en la ficha **Código Source**, una nueva sección de **Estrategia de compilación** le permite elegir una de las siguientes opciones de compilación:

* **Compilación completa**: genera todos los módulos del repositorio en cada ejecución.
* **Compilación inteligente**: genera solo módulos que han cambiado desde la última confirmación, lo que acorta el tiempo de compilación general.

Vea [Agregar una canalización que no es de producción](/help/using/non-production-pipelines.md#add-non-production-pipeline) y [Acerca del uso de Smart Build en una canalización que no es de producción](/help/using/non-production-pipelines.md#about-smart-build).

Usted controla qué canalizaciones utilizan **Smart Build**. Durante la versión beta, esta opción solo aparece para las canalizaciones **Calidad del código** y **Implementación de código de pila completa de desarrolladores**.

¿Le interesa? Envíe un correo electrónico a [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) con su identificador de organización de Adobe y el identificador de programa.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## Correcciones de errores {#bug-fixes}

No hay correcciones de errores significativas en la versión de marzo de 2026 de Cloud Manager en AMS.

<!--
Known Issues {#known-issues}

* A 
-->
