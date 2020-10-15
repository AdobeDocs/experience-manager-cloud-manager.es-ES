---
title: Introducción a Cloud Manager
seo-title: Introducción a Cloud Manager
description: 'Esta página sirve como punto de partida para obtener información sobre Cloud Manager. '
seo-description: 'Esta página sirve como punto de partida para obtener información sobre Adobe AEM Cloud Manager, y en ella se destacan sus ventajas y características clave. '
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
translation-type: tm+mt
source-git-commit: 4838de3d6c78884333d8088eb38f388fbcd0e707
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 89%

---


# Introducción a [!UICONTROL Cloud Manager]{#introduction-to-cloud-manager}

## Introducción {#introduction}

[!UICONTROL Cloud Manager], que forma parte de los servicios gestionados de Adobe, permite a las organizaciones administrar su propio Experience Manager en la nube. Incluye un marco de integración y entrega continuas (CI/CD) que permite a los equipo de TI y a los asociados de la implementación acelerar la entrega de las personalizaciones o actualizaciones sin poner en riesgo el rendimiento o la seguridad.

Gracias al portal de autoservicio para clientes [!UICONTROL Cloud Manager], las **organizaciones** pueden realizar y aprovechar al máximo las siguientes opciones:

* **Integración y entrega continuas** del código para reducir el tiempo de salida al mercado de meses o semanas a días u horas.
* **Inspección del código, pruebas de rendimiento y validación de seguridad** basadas en procedimientos recomendados antes de pasar a producción, para minimizar las interrupciones en la misma.
* **Implementación automática, programada o manual** incluso fuera del horario laboral, para obtener la máxima flexibilidad y control.
* La característica de **escalado automático** detecta de forma inteligente la necesidad de aumentar la capacidad, y pone en línea automáticamente segmentos adicionales de Dispatcher o segmentos que hayan sido publicados.

En la siguiente imagen se ilustra el flujo de proceso CI/CD que se usa en [!UICONTROL Cloud Manager]:

![](assets/screen_shot_2018-05-12at73843pm.png)

## Características principales de [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Las organizaciones pueden aprovechar las siguientes características con [!UICONTROL Cloud Manager]:

### Interfaz de autoservicio {#self-service-interface}

La interfaz de usuario (IU) para [!UICONTROL Cloud Manager] permite a los clientes acceder y administrar fácilmente el entorno de la nube y la canalización de CI/CD para sus aplicaciones de Experience Manager.

Los clientes definen los Indicadores clave de rendimiento (KPI) específicos de la aplicación: visitas máximas por minuto de páginas y tiempo de respuesta esperado al cargar una página; en última instancia, estos datos constituyen la base para medir una implementación exitosa. Las funciones y los permisos de los distintos integrantes del equipo se pueden definir fácilmente. Aunque la nueva interfaz de autoservicio le permite controlarlo todo con facilidad, también le ofrece vínculos a procedimientos recomendados y le da la oportunidad de contactar con expertos de Adobe que pueden proporcionarle la orientación necesaria.

To explore and get started with [!UICONTROL Cloud Manager]&#39;s UI, see [First Time Login](https://helpx.adobe.com/experience-manager/cloud-manager/using/first-time-login.html).

### Canalización de CI/CD {#ci-cd-pipeline}

Una de las funciones clave de [!UICONTROL Cloud Manager] es la capacidad de utilizar una canalización de CD/CI optimizada para acelerar la entrega de código personalizado o las actualizaciones, como la adición de nuevos componentes en el sitio web.

A través de la interfaz de usuario de [!UICONTROL Cloud Manager], los clientes pueden configurar y poner en marcha su canalización de CD/CI. Durante esta canalización, se realiza un análisis exhaustivo del código para garantizar que solo las aplicaciones de alta calidad pasen al entorno de producción.

To learn more about configuring pipeline from [!UICONTROL Cloud Manager]&#39;s UI, see [Configure your CI/CD Pipeline](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html).

### Modos de implementación flexibles {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] ofrece a los clientes modos de implementación flexibles y configurables para que puedan ofrecer experiencias en función de las cambiantes exigencias comerciales.

Gracias a su modo de activación automático, el código se implementa automáticamente en un entorno basado en eventos específicos como la confirmación de código. También puede programar implementaciones de código durante intervalos de tiempo especificados, incluso fuera del horario laboral.

Independientemente del activador de implementación, siempre se realizan comprobaciones de calidad como parte de la ejecución de la canalización de CI/CD, cada vez que se activa una implementación. Las comprobaciones de calidad incluyen la inspección del código, las pruebas de seguridad y las pruebas de rendimiento ofrecidas de forma inmediata, sin que los clientes o sus socios deban realizar ningún esfuerzo.

Para obtener más información sobre la implementación del código y las pruebas de calidad, consulte [Implementación del código](deploying-code.md)

### Escalado automático {#autoscaling}

[!UICONTROL Cloud Manager] detecta la necesidad de aplicar capacidades adicionales cuando el entrono de producción está sujeto a cargas altas e inusuales, y lleva esas capacidades adicionales en línea de manera automática mediante la función de escalado automático.

En un evento de escalado automático, [!UICONTROL Cloud Manager] activa automáticamente el proceso de aprovisionamiento de escalado automático, envía una notificación del evento de escalado automático y, en pocos minutos, lleva las capacidades adicionales en línea. Las capacidades adicionales se aprovisionarán en el entorno de producción, en las mismas zonas y coincidirán con el mismo sistema de especificaciones que ejecuta Dispatcher o los nodos publicados.

La función escalado automático se aplicará solo a Dispatcher o a las capas publicadas y se ejecutará siempre mediante un método de escalado horizontal, con un segmento adicional de Dispatcher o del par publicado como mínimo y un máximo de diez segmentos. Se escalará manualmente cualquier capacidad adicional aprovisionada en un periodo de diez días laborables, tal como determine el CSE (ingeniero de administración del éxito del cliente). Los clientes interesados en explorar si la escala automática es adecuada o no para su aplicación deben ponerse en contacto con su representante de CSE o Adobe.
