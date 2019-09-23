---
title: Notas de la versión de 2019.1.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.1.0
description: Siga esta página para obtener información sobre la versión 2019.1.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.1.0 de AEM Cloud Manager.
uuid: 3af5808f-828f-4846-abeja4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas de la versión
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
translation-type: tm+mt
source-git-commit: 12d787ef2f9b2dd229b8ed0f8c602fbf5c06aa80

---


# Notas de la versión de 2019.1.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2018.9.0 incorpora la compatibilidad con la prueba de los programas de AEM Assets, así como otros tipos de canalizaciones que ejecutan los pasos de creación y calidad del código, y se implementa de forma opcional en un entorno que no es de producción.

## Fecha de lanzamiento {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2019.1.0 es el 17 de enero de 2019.

## Novedades {#whats-new}

* Se ha añadido la compatibilidad con las pruebas de rendimiento de Recursos AEM. Para obtener más información, consulte Configurar [CI/CD](configuring-pipeline.md)Pipelineos.
* Se agregó compatibilidad con tuberías que ejecutan solo pasos de creación y de calidad de código y tuberías que se implementan en entornos que no son de producción. Consulte la sección **de tuberías** de calidad de código y no producción en [Configurar la canalización](configuring-pipeline.md) de CI/CD para obtener más detalles.
* Se agregó compatibilidad con variables de entorno personalizadas en el entorno de compilación. Consulte [Crear un proyecto](create-an-application-project.md) de aplicación de AEM para obtener más información.
* Para los clientes con entornos de producción o etapas múltiples, la selección del entorno al que se implementará como parte de la canalización de producción está disponible en la página [Configurar la canalización](configuring-pipeline.md) de CD/CI.
* httxt2dbm se ha agregado al contenedor de compilación.
* Todos los elementos del menú de ayuda abren una nueva ficha.

## Corrección de errores {#bug-fixes}

* Durante la edición de un programa, era posible anular la selección de todos los conjuntos de páginas.
* El paso de aprobación tenía un título incorrecto.
* En algunas situaciones, el logotipo del programa estaba incorrectamente acoplado.
* Si solo se generara el paquete de configuración del despachante, el paso de implementación fallaría.
* Los entornos que contenían instancias de espera en frío no se gestionaban correctamente.
* Algunos programas terminados aparecieron en el conmutador de programas.
* Si se agregó una nueva rama al repositorio de Git mientras se estaba editando la canalización, es posible que no se haya podido seleccionar inmediatamente.
* En algunas pantallas, el icono de Developer Connection del menú Ayuda no estaba visible.
* La tecla de tabulación no se gestionaba correctamente en el cuadro de diálogo de configuración de vaciado del despachante.

## Problemas conocidos {#known-issues}

* Al abrir un programa que tiene KPI de sitios pero no de recursos, todos los usuarios ven una tarjeta de llamada a acción con un botón **Configurar programa** . Sin embargo, solo los usuarios en la función Propietario de la empresa pueden hacer clic en el botón **Configurar programa** .