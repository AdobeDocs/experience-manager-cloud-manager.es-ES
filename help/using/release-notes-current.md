---
title: Notas de la versión 2021.3.0
seo-title: Notas de la versión de AEM Cloud Manager para 2021.3.0
description: Siga esta página para obtener información sobre la versión 2021.3.0 de Cloud Manager
seo-description: Siga esta página para obtener información sobre la versión 2021.3.0 de AEM Cloud Manager
translation-type: tm+mt
source-git-commit: b5233e1932888b515d8dc26a6493cbd26686bc3c
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 5%

---

# Notas de la versión 2021.3.0 {#release-notes-for}

En la siguiente sección se describen las notas de la versión generales de [!UICONTROL Cloud Manager] versión 2021.3.0.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2021.3.0 de [!UICONTROL Cloud Manager] es el 11 de marzo de 2021.

## Novedades {#whats-new}

* Se ha introducido una nueva herramienta de calidad de código para validar la configuración de Dispatcher del cliente (Herramienta de optimización de Dispatcher).

* Los usuarios ahora pueden ver sus funciones de Cloud Manager seleccionando la opción **View Cloud Manager Role(s)** después de navegar al icono User Profile (parte superior derecha) del shell unificado.

* La etiqueta **Application for Approval** se ha vuelto a etiquetar como **Production Approval** para una buena claridad.

* La etiqueta **Version** se ha vuelto a etiquetar como **Git Tag** en la pantalla de ejecución de la canalización de producción.

* Las etiquetas que definen el comportamiento cuando métricas importantes no alcanzan el umbral definido se han vuelto a etiquetar para reflejar su verdadero comportamiento: Cancelar inmediatamente y Aprobar inmediatamente.

* Las listas de deprecación de clases y métodos se han actualizado en función de la versión `2021.3.4997.20210303T022849Z-210225` del SDK del Cloud Service de AEM.

## Corrección de errores {#bug-fixes}

* Algunos problemas de calidad no se descubrieron correctamente cuando los paquetes estaban incrustados en otros paquetes.

* En ocasiones, si el usuario sale de la página de ejecución de la canalización inmediatamente después de iniciar una canalización, aparece un mensaje de error que indica que la acción ha fallado, aunque la ejecución realmente se inicia.