---
title: Notas de la versión de 2018.7.0
seo-title: Notas de la versión de 2018.7.0
description: nulo
seo-description: Siga esta página para obtener información sobre la versión 2018.7.0 de Cloud Manager.
uuid: d7b49e32-01dc-48ce-b744-e6a806fbdd8a
contentOwner: jsyal
topic-tags: notas de la versión
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: b64bf9ab-27ed-4f33-adc8-d73d34094f1b
translation-type: tm+mt
source-git-commit: b78c29520414726ad2bbf86e5b7f8e65710c7f75

---


# Notas de la versión de 2018.7.0 {#release-notes-for}

La siguiente sección describe la versión [!UICONTROL Cloud Manager] 2018.7.0 que ofrece la función de *escalado* automático.

**La escala** automática se habilita mediante la escala horizontal de `Dispatcher/Publish` segmentos en el entorno de producción para admitir un aumento repentino de la carga, el volumen, el acceso y otras métricas controladas definidas.

## Fecha de lanzamiento {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2018.7.0 es el 10 de septiembre de 2018.

## Novedades {#what-s-new}

* **Aprovisionamiento** : [!UICONTROL Cloud Manager] ahora tendrá la capacidad de escalar automáticamente el entorno de producción en el programa del cliente mediante la ampliación horizontal con segmentos de Dispatcher/Publish. Una novedad en la interfaz de usuario es la sección Provisioning de Program Setup (Aprovisionamiento) que se muestra si la escalación automática está habilitada en el programa para clientes. Consulte [Configuración del programa](setting-up-program.md) para obtener más información.

* **Entornos** : ahora es posible ver una vista detallada de los entornos de producción y etapa junto con el tamaño, almacenamiento, región y estado de los nodos asociados con cada entorno. Consulte [Administrar entornos](manage-your-environment.md) para obtener más información.

* **Análisis** de calidad del código: nueva regla para identificar el uso incorrecto de la API. Consulte Reglas [de calidad de código](custom-code-quality-rules.md) personalizado para obtener más información.

* **Prueba** de rendimiento: mientras visualiza los resultados de la prueba de rendimiento, están disponibles gráficos para la utilización de CPU, el tiempo de espera de E/S de disco, la tasa de error de la página, la utilización del ancho de banda de disco, la utilización del ancho de banda de la red, el tiempo máximo de respuesta de la página y el tiempo de respuesta de la página del porcentaje 95. Consulte la sección *Prueba de rendimiento *en [Comprender la página Resultados](understand-your-test-results.md) de la prueba.

* **Prueba** de rendimiento: al ver los resultados de la prueba de rendimiento, se puede descargar la lista de errores de página y solicitudes lentas. Consulte la sección *Prueba de rendimiento *en [Comprender la página Resultados](understand-your-test-results.md) de la prueba.

## Corrección de errores {#bug-fixes}

* En determinadas circunstancias, la sincronización interna del sistema falló incorrectamente, lo que dio lugar a vistas incoherentes de los datos.
* En algunos casos, el activador de canalización manual no se seleccionaba automáticamente, lo que provocaba problemas de validación del formulario.
* Las secuencias de comandos de compilación específicas del cliente podrían provocar errores durante el paso de compilación en función de las incompatibilidades del complemento.

## Problemas conocidos {#known-issues}

* Aunque los clientes pueden seleccionar el activador de confirmación, es posible que la canalización no se inicie en función de nuevos compromisos.
* Es posible que la barra lateral de [!UICONTROL Experience Cloud] notificaciones no cargue las notificaciones de forma coherente. Notifications, however, are visible in the [!UICONTROL Experience Cloud] and, if configured, will still be sent via email.

