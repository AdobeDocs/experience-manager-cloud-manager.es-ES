---
title: Notas de la versión de 2018.7.0
seo-title: Notas de la versión de 2018.7.0
description: nulo
seo-description: Siga esta página para obtener información sobre la versión 2018.7.0 de Cloud Manager.
uuid: d 7 b 49 e 32-01 dc -48 ce-b 744-e 6 a 806 fbdd 8 a
contentOwner: jsyal
topic-tags: notas de la versión
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: b 64 bf 9 ab -27 ed -4 f 33-adc 8-d 73 d 34094 f 1 b
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notas de la versión de 2018.7.0 {#release-notes-for}

La siguiente sección describe la versión [!UICONTROL Cloud Manager] 2018.7.0 que ofrece la función *de escalado automático* .

**El escalado automático** está habilitado a través de la reducción horizontal de `Dispatcher/Publish` segmentos en el entorno de producción para admitir un aumento repentino de carga, volumen, acceso y otras métricas monitoreadas definidas.

## Fecha de versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2018.7.0 es el 10 de septiembre de 2018.

## Novedades {#what-s-new}

* **Aprovisionamiento** : [!UICONTROL Cloud Manager] ahora tendrá la capacidad de escalar automáticamente el entorno de producción en el programa del cliente reduciendo horizontalmente con segmentos de Dispatcher/Publish. Nuevo en la interfaz de usuario es la sección Aprovisionamiento de la configuración del programa que se mostrará si el escalado automático está habilitado en el programa del cliente. Consulte [Configuración del programa](setting-up-program.md) para obtener más información.

* **Entornos** : Ahora es posible ver una vista detallada de los entornos Producción y Etapa junto con el tamaño, almacenamiento, región y estado de los nodos asociados a cada entorno. Consulte [Administrar los entornos](manage-your-environment.md) para obtener más información.

* **Análisis** de calidad de código: Nueva regla para identificar el uso de API incorrecto. Consulte Reglas de calidad de código [personalizado](custom-code-quality-rules.md) para obtener más información.

* **Prueba** de rendimiento: Al visualizar resultados de la prueba de rendimiento, se encuentran disponibles los gráficos de uso de CPU, tiempo de espera de disco I/O, tasa de error de página, uso de ancho de banda de disco, uso de ancho de banda de red, tiempo máximo de respuesta a página y tiempo de respuesta de página de percentil 95. Consulte * Prueba de rendimiento * en la sección [Comprender resultados](understand-your-test-results.md) de la prueba.

* **Prueba** de rendimiento: Al ver los resultados de la prueba del rendimiento, se puede descargar la lista de errores de página y solicitudes lentas. Consulte * Prueba de rendimiento * en la sección [Comprender resultados](understand-your-test-results.md) de la prueba.

## Corrección de errores {#bug-fixes}

* En determinadas circunstancias, la sincronización de sistema interno fallaba incorrectamente, lo que provocaba vistas incoherentes de datos.
* En algunos casos, el activador manual de la canalización no se seleccionaba automáticamente en los problemas de validación del formulario.
* Las secuencias de comandos específicas de generación de clientes podrían provocar errores durante el paso de compilación según incompatibilidades de complemento.

## Problemas conocidos {#known-issues}

* Aunque los clientes pueden seleccionar el activador de transferencia, es posible que la canalización no se inicie en función de los nuevos compromisos.
* La barra lateral [!UICONTROL Experience Cloud] de notificación puede no cargar notificaciones de forma coherente. Las notificaciones, sin embargo, son visibles en [!UICONTROL Experience Cloud] el y, si se configuran, se envían por correo electrónico.

