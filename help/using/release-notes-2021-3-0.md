---
title: Notas de la versión 2021.3.0
description: Siga esta página para obtener información sobre la versión 2021.3.0 de Cloud Manager
feature: Release Information
source-git-commit: 09dd8fe608d95cd9dbc95129cf86b9693c2839b5
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 5%

---

# Notas de la versión 2021.3.0 {#release-notes-for}

En la siguiente sección se describen las notas de la versión generales de [!UICONTROL Cloud Manager] Versión 2021.3.0.

## Fecha de la versión {#release-date}

La fecha de lanzamiento de [!UICONTROL Cloud Manager] La versión 2021.3.0 es el 11 de marzo de 2021.
La próxima versión está planificada para el 08 de abril de 2021.

## Novedades {#whats-new}

* Una nueva herramienta de calidad de código [Herramienta de optimización de Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules) se ha introducido para validar la configuración de Dispatcher del cliente.

* Los usuarios ahora pueden ver sus funciones de Cloud Manager seleccionando la **Ver funciones de Cloud Manager** después de navegar al icono Perfil de usuario (parte superior derecha) del Shell unificado.

* La etiqueta **Solicitud de aprobación** se ha vuelto a etiquetar como **Aprobación de producción** para una buena claridad.

* La variable **Versión** se ha vuelto a etiquetar como **Etiqueta de Git** en la pantalla de ejecución de la canalización de producción.

* Las etiquetas que definen el comportamiento cuando métricas importantes no alcanzan el umbral definido se han vuelto a etiquetar para reflejar su verdadero comportamiento: **Cancelar inmediatamente** y **Aprobar inmediatamente**. Consulte [Configuración de la canalización](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager) para obtener más información.

* Las listas de desaprobación de clases y métodos se han actualizado en función de la versión `2021.3.4997.20210303T022849Z-210225` del SDK de AEM Cloud Service.

## Corrección de errores {#bug-fixes}

* Algunos problemas de calidad no se descubrieron correctamente cuando los paquetes estaban incrustados en otros paquetes.

* En ocasiones, si el usuario sale de la página de ejecución de la canalización inmediatamente después de iniciar una canalización, aparece un mensaje de error que indica que la acción ha fallado, aunque la ejecución realmente se inicia.
