---
title: Notas de la versión 2021.3.0
seo-title: Notas de la versión de AEM Cloud Manager para 2021.3.0
description: Siga esta página para obtener información sobre la versión 2021.3.0 de Cloud Manager
seo-description: Siga esta página para obtener información sobre la versión 2021.3.0 de AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 090505e737b8cb224d87f117a9b5e786a4f99851
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 3%

---

# Notas de la versión 2021.3.0 {#release-notes-for}

En la siguiente sección se describen las notas de la versión generales de [!UICONTROL Cloud Manager] versión 2021.3.0.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2021.3.0 de [!UICONTROL Cloud Manager] es el 11 de marzo de 2021.

## Novedades {#whats-new}

* Los usuarios con los permisos necesarios ahora pueden editar el programa, lo que les permite hacer lo siguiente de forma autoservicio:

   * Agregar la solución Sitios a un programa existente con Assets (o viceversa).
   * Elimine Sitios (o Recursos) de un programa existente con Sitios y Recursos.
   * Añadir (atrás) una solución se puede realizar en el programa existente o como un nuevo programa.

* Se ha introducido una nueva herramienta de calidad de código [Dispatcher Optimization Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules) para validar la configuración de Dispatcher del cliente.

* Los usuarios ahora pueden ver sus funciones de Cloud Manager seleccionando la opción **View Cloud Manager Role(s)** después de navegar al icono User Profile (parte superior derecha) del shell unificado.

* La etiqueta **Application for Approval** se ha vuelto a etiquetar como **Production Approval** para una buena claridad.

* La etiqueta **Version** se ha vuelto a etiquetar como **Git Tag** en la pantalla de ejecución de la canalización de producción.

* Las etiquetas que definen el comportamiento cuando métricas importantes no alcanzan el umbral definido se han vuelto a etiquetar para reflejar su verdadero comportamiento: **Cancelar inmediatamente** y **Aprobar inmediatamente**. Consulte [Configuración de la canalización desde Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager) para obtener más información.

* Las listas de deprecación de clases y métodos se han actualizado en función de la versión `2021.3.4997.20210303T022849Z-210225` del SDK del Cloud Service de AEM.

## Corrección de errores {#bug-fixes}

* Algunos problemas de calidad no se descubrieron correctamente cuando los paquetes estaban incrustados en otros paquetes.

* En ocasiones, si el usuario sale de la página de ejecución de la canalización inmediatamente después de iniciar una canalización, aparece un mensaje de error que indica que la acción ha fallado, aunque la ejecución realmente se inicia.