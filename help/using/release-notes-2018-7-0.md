---
title: Notas de la versión 2018.7.0
seo-title: Notas de la versión 2018.7.0
description: Obtenga información sobre la versión 2018.7.0 de Cloud Manager
seo-description: Siga esta página para obtener información sobre la versión 2018.7.0 de Cloud Manager.
uuid: d7b49e32-01dc-48ce-b744-e6a806fbdd8a
contentOwner: jsyal
topic-tags: release-notes
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: b64bf9ab-27ed-4f33-adc8-d73d34094f1b
feature: Información de la versión
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 12%

---


# Notas de la versión 2018.7.0 {#release-notes-for}

En la siguiente sección se describe la versión [!UICONTROL Cloud Manager] 2018.7.0 que ofrece la función *escalado automático*.

**La escala automática se habilita mediante la escala horizontal de segmentos de en el entorno de producción para admitir un aumento repentino de la carga, el volumen, el acceso y otras métricas controladas definidas.**`Dispatcher/Publish`

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2018.7.0 de [!UICONTROL Cloud Manager] es el 10 de septiembre de 2018.

## Novedades {#what-s-new}

* **Aprovisionamiento** : ahora  [!UICONTROL Cloud Manager] tendrá la capacidad de escalar automáticamente el entorno de producción en el programa del cliente mediante la ampliación horizontal con segmentos de Dispatcher/Publish. Una novedad en la interfaz de usuario es la sección Provisioning de Configuración de programa que se muestra si el escalado automático está habilitado en el programa del cliente. Consulte [Configuración del programa](setting-up-program.md) para obtener más información.

* **Entornos** : ahora es posible ver una vista detallada de los entornos de producción y ensayo junto con el tamaño, el almacenamiento, la región y el estado de los nodos asociados a cada entorno. Consulte [Administrar los entornos](manage-your-environment.md) para obtener más información.

* **Análisis de calidad del código** : Nueva regla para identificar un uso incorrecto de la API. Consulte [Reglas de calidad de código personalizadas](custom-code-quality-rules.md) para obtener más información.

* **Pruebas de rendimiento** : mientras se ven los resultados de las pruebas de rendimiento, están disponibles gráficos para la utilización de la CPU, el tiempo de espera de E/S de disco, la tasa de errores de la página, la utilización del ancho de banda del disco, la utilización del ancho de banda de la red, el tiempo de respuesta de la página máximo y el tiempo de respuesta de la página del 95 %. Consulte la sección *Pruebas de rendimiento* en la página [Comprender los resultados de la prueba](understand-your-test-results.md).

* **Pruebas de rendimiento** : Al ver los resultados de la prueba de rendimiento, se puede descargar la lista de errores de página y solicitudes lentas. Consulte la sección *Pruebas de rendimiento* en la página [Comprender los resultados de la prueba](understand-your-test-results.md).

## Corrección de errores {#bug-fixes}

* En determinadas circunstancias, la sincronización interna del sistema fallaba de forma inadecuada, lo que producía vistas incoherentes de los datos.
* En algunos casos, el déclencheur de canalización manual no se seleccionó automáticamente, lo que provocó problemas de validación del formulario.
* Los scripts de compilación específicos del cliente podrían provocar errores durante el paso de compilación en función de las incompatibilidades del complemento.

## Problemas conocidos {#known-issues}

* Aunque los clientes pueden seleccionar el déclencheur de confirmación, es posible que la canalización no se inicie en función de nuevas confirmaciones.
* Es posible que la barra lateral de notificación [!UICONTROL Experience Cloud] no cargue las notificaciones de forma coherente. Sin embargo, las notificaciones son visibles en [!UICONTROL Experience Cloud] y, si se configuran, se envían por correo electrónico.

