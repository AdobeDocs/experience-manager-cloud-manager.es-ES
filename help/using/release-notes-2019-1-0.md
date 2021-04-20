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
feature: Release Information
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 4%

---


# Notas de la versión 2019.1.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2018.9.0 agrega compatibilidad con los programas de prueba de AEM Assets, así como tipos de canalización adicionales que ejecutan los pasos de compilación y calidad del código, y que opcionalmente se implementan en un entorno que no es de producción.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2019.1.0 de [!UICONTROL Cloud Manager] es el 17 de enero de 2019.

## Novedades {#whats-new}

* Se ha agregado compatibilidad con las pruebas de rendimiento de AEM Assets. Consulte Configurar la [Canalización de CI/CD](configuring-pipeline.md)para obtener más información.
* Se ha agregado compatibilidad con canalizaciones que ejecutan solo pasos de compilación y código de calidad y canalizaciones que se implementan en entornos que no son de producción. Consulte la sección **No producción y solo calidad de código** en [Configurar la canalización de CI/CD](configuring-pipeline.md) para obtener más información.
* Se ha agregado compatibilidad con variables de entorno personalizadas en el entorno de compilación.
* Para los clientes con varios entornos de producción o de fase, la selección de a qué entorno se implementará como parte de la canalización de producción está disponible en la página [Configure your CI/CD Pipeline](configuring-pipeline.md) .
* se ha añadido httxt2dbm al contenedor de compilación.
* Todos los elementos del menú de ayuda abren una nueva ficha.

## Corrección de errores {#bug-fixes}

* Durante la edición de un programa, era posible anular la selección de todos los conjuntos de páginas.
* El paso de aprobación tenía un título incorrecto.
* En algunas situaciones, el logotipo del programa estaba incorrectamente emparejado.
* Si solo se creó el paquete de configuración de Dispatcher, el paso de implementación fallaría.
* Los entornos que contenían instancias en espera en frío no se gestionaban correctamente.
* Algunos programas terminados aparecieron en el conmutador de programas.
* Si se agregó una nueva rama al repositorio de Git mientras se editaba la canalización, es posible que no se haya podido seleccionar inmediatamente.
* En algunas pantallas, el icono Developer Connection del menú Ayuda no estaba visible.
* La clave de tabulación no se gestionaba correctamente en el cuadro de diálogo de configuración de vaciado de Dispatcher.

## Problemas conocidos {#known-issues}

* Al abrir un programa que tiene establecidos los KPI de Sites, pero no de Assets, todos los usuarios ven una tarjeta de llamada a la acción con un botón **Programa de instalación**. Sin embargo, solo los usuarios con la función Propietario empresarial pueden hacer clic en el botón **Programa de instalación**.