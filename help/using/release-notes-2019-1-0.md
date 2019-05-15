---
title: Notas de la versión de 2019.1.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.1.0
description: Siga esta página para obtener información sobre la versión 2019.1.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.1.0 de AEM Cloud Manager.
uuid: 3 af 5808 f -828 f -4846-bee 4-1 e 62194 b 48 ad
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas de la versión
discoiquuid: 85 a 1 dcf 3-2 eef -4 ba 8-b 4 d 1-09 e 4 a 88 c 7 bd 0
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notas de la versión de 2019.1.0 {#release-notes-for}

La versión [!UICONTROL Cloud Manager] 2018.9.0 permite probar los programas AEM Assets, así como otros tipos de canales que ejecutan los pasos de la calidad del código y la compilación, lo que opcionalmente se implementa en un entorno que no es de producción.

## Fecha de versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2019.1.0 es el 17 de enero de 2019.

## Novedades {#whats-new}

* Se agregó compatibilidad con la prueba de rendimiento de Recursos AEM. Consulte Configurar su [caña de CD/CD para](configuring-pipeline.md)obtener más detalles.
* Se agregó compatibilidad con los pipeline que ejecutan solo los pasos de compilación y código y los pipeline que implementan en entornos que no son de producción. Consulte **la** sección No solo de producción y de calidad de código en [Configurar su flujo de PC/CD](configuring-pipeline.md) para obtener más detalles.
* Se agregó compatibilidad con variables de entorno personalizadas en entornos de compilación. Consulte [Crear un proyecto de aplicación AEM](create-an-application-project.md) para obtener más detalles.
* Para los clientes con entornos de producción o etapa múltiples, la selección de qué entorno se implementará como parte del canalizador de producción está disponible en [Configurar su página de flujo](configuring-pipeline.md) de CD/CD.
* httxt 2 dbm has been added to build container.
* Todos los elementos de menú Ayuda abren una nueva ficha.

## Corrección de errores {#bug-fixes}

* Al editar un programa, era posible anular la selección de todos los conjuntos de páginas.
* El paso de aprobación no se tituló correctamente.
* En algunas situaciones, el logotipo del programa no se reflejaba correctamente.
* Si solo se creó el paquete de configuración de dispatcher, el paso de implementación podía fallar.
* Los entornos que contenían instancias de emergencia paralelas no se gestionaban correctamente.
* Algunos programas terminados aparecían en el conmutador de programa.
* Si se agregó una nueva rama al repositorio de git mientras se edita el canal, es posible que no se haya podido seleccionar inmediatamente.
* En algunas pantallas, el icono Developer Connection del menú Ayuda no era visible.
* La tecla de tabulación no se manejó correctamente en el cuadro de diálogo de configuración de vaciado del despachante.

## Problemas conocidos {#known-issues}

* Al abrir un programa que tiene sitios, pero no Recursos, KPI, todos los usuarios ven una llamada a la tarjeta de acción con un botón **de programa** de configuración. Sin embargo, solo los usuarios de la función Propietario comercial pueden hacer clic en el botón **Programa** de configuración.