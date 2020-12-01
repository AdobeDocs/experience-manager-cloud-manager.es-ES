---
title: Notas de la versión 2019.1.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.1.0
description: Siga esta página para obtener información sobre la versión 2019.1.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.1.0 de AEM Cloud Manager.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
translation-type: tm+mt
source-git-commit: c35398110e9d8311bf58f217efdd082cf0cfd90a
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 4%

---


# Notas de la versión 2019.1.0 {#release-notes-for}

La [!UICONTROL Cloud Manager] versión 2018.9.0 incorpora compatibilidad con la prueba de programas de AEM Assets, así como tipos de canalización adicionales que ejecutan los pasos de generación y calidad del código, y se implementa de manera opcional en un entorno que no es de producción.

## Fecha de la versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] versión 2019.1.0 es el 17 de enero de 2019.

## Novedades {#whats-new}

* Compatibilidad añadida para pruebas de rendimiento de AEM Assets. Consulte Configurar su [Canalización de CD/CI](configuring-pipeline.md)para obtener más detalles.
* Compatibilidad añadida para tuberías que ejecutan solo pasos de creación y de calidad de código y tuberías que se implementan en entornos que no son de producción. Consulte la sección **Tuberías solo de calidad de código y sin producción** en [Configurar la canalización de CD/CI](configuring-pipeline.md) para obtener más detalles.
* Se añadió la compatibilidad con variables de entorno personalizadas en el entorno de compilación.
* Para los clientes con múltiples etapas o entornos de producción, la selección de a qué entorno se implementará como parte de la canalización de producción está disponible en la página [Configurar su canalización de CI/CD](configuring-pipeline.md).
* httxt2dbm se ha agregado para generar contenedor.
* Todos los elementos del menú de ayuda abren una nueva ficha.

## Corrección de errores {#bug-fixes}

* Durante la edición de un programa, era posible anular la selección de todos los conjuntos de páginas.
* El paso de aprobación tenía un título incorrecto.
* En algunas situaciones, el logotipo de programa tenía un formato incorrecto.
* Si solo se generara el paquete de configuración del despachante, el paso de implementación fallaría.
* Los entornos que contenían instancias de espera en frío no se gestionaban correctamente.
* Algunos programas terminados aparecieron en el mezclador de programas.
* Si se agregó una nueva rama al repositorio de Git mientras se estaba editando la canalización, es posible que no se haya podido seleccionar inmediatamente.
* En algunas pantallas, el icono de Developer Connection del menú Ayuda no estaba visible.
* La tecla de tabulación no se gestionaba correctamente en el cuadro de diálogo de configuración de vaciado del despachante.

## Problemas conocidos {#known-issues}

* Al abrir un programa que tiene KPI de sitios pero no de recursos, todos los usuarios ven una tarjeta de llamada a acción con un botón **Configurar Programa**. Sin embargo, solo los usuarios en la función Propietario de la empresa pueden hacer clic en el botón **Configurar Programa**.