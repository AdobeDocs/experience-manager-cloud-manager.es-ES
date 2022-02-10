---
title: Introducción a Cloud Manager
seo-title: Introduction to Cloud Manager
description: 'Esta página sirve como punto de partida para obtener información sobre Cloud Manager. '
seo-description: This page serves as a starting point for learning about Adobe AEM Cloud Manager and highlights the benefits and key features.
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
feature: Getting Started
level: Beginner
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 71d44c7e3673ca62fcd2203ecc0bc4ed9fa22002
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 66%

---

# Introducción a [!UICONTROL Cloud Manager]{#introduction-to-cloud-manager}

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Introducción a Cloud Manager"
>abstract="Permite a las organizaciones administrar su Experience Manager en la nube. Incluye un marco de trabajo de integración y entrega continuas (CI/CD) que permite a los equipo de TI y a los asociados de la implementación acelerar la entrega de las personalizaciones o actualizaciones sin poner en riesgo el rendimiento o la seguridad."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en#cloud-manager" text="Crear programas"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en#cloud-manager" text="Crear entornos"

## Introducción {#introduction}

[!UICONTROL Cloud Manager] para Adobe Experience Manager ofrece a los desarrolladores la capacidad de crear experiencias de clientes impactantes mediante flujos de trabajo optimizados basados en las prácticas recomendadas de Adobe Experience Manager. Las canalizaciones CI/CD optimizadas para Adobe Experience Manager le permiten combinar fácilmente los flujos de trabajo de desarrollo con solo comprobar el código y desplazarse hasta estar listos para la producción. Durante la fase de compilación, las actualizaciones de código personalizado se prueban exhaustivamente mediante prácticas recomendadas comprobadas y aprendidas para ofrecer experiencias digitales impactantes a sus clientes. Cloud Manager utiliza un enfoque de API abierta y le permite integrarse con sus sistemas sin interrumpir los procesos y herramientas existentes.

Este sitio de documentación describe específicamente las funciones y características de Cloud Manager para los clientes de Adobe Managed Services (AMS). La documentación equivalente para AEM clientes as a Cloud Service se encuentra en la [Implementación de solicitudes para AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/home.html?lang=en).

Con Cloud Manager, su equipo de desarrollo puede aprovechar lo siguiente:

* Integración y entrega continuas del código para reducir el tiempo de salida al mercado de meses o semanas a días u horas.

* Inspección del código, pruebas de rendimiento y validación de seguridad basadas en las prácticas recomendadas antes de pasar a producción para minimizar las interrupciones en la misma.

* Conectividad de API para complementar los procesos de DevOps existentes.

* La característica de escalado automático detecta de forma inteligente la necesidad de aumentar la capacidad, y pone en línea automáticamente segmentos adicionales de Dispatcher o segmentos que hayan sido publicados.

En la siguiente imagen se ilustra el flujo de proceso CI/CD que se usa en [!UICONTROL Cloud Manager]:

![](assets/screen_shot_2018-05-12at73843pm.png)

## Características principales de [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Las organizaciones pueden aprovechar las siguientes características con [!UICONTROL Cloud Manager]:

### Interfaz de autoservicio {#self-service-interface}

La interfaz de usuario (IU) para [!UICONTROL Cloud Manager] permite a los clientes acceder y administrar fácilmente el entorno de la nube y la canalización de CI/CD para sus aplicaciones de Experience Manager.

Los clientes definen los Indicadores clave de rendimiento (KPI) específicos de la aplicación: visitas máximas por minuto de páginas y tiempo de respuesta esperado al cargar una página; en última instancia, estos datos constituyen la base para medir una implementación exitosa. Las funciones y los permisos de los distintos integrantes del equipo se pueden definir fácilmente. Aunque la nueva interfaz de autoservicio le permite controlarlo todo con facilidad, también le ofrece vínculos a procedimientos recomendados y le da la oportunidad de contactar con expertos de Adobe que pueden proporcionarle la orientación necesaria.

Para explorar y empezar con [!UICONTROL Cloud Manager]La interfaz de usuario de , consulte [Primer inicio de sesión](https://helpx.adobe.com/experience-manager/cloud-manager/using/first-time-login.html).

### Canalización de CI/CD {#ci-cd-pipeline}

Una de las funciones clave de [!UICONTROL Cloud Manager] es la capacidad de utilizar una canalización de CD/CI optimizada para acelerar la entrega de código personalizado o las actualizaciones, como la adición de nuevos componentes en el sitio web.

A través de la interfaz de usuario de [!UICONTROL Cloud Manager], los clientes pueden configurar y poner en marcha su canalización de CD/CI. Durante esta canalización, se realiza un análisis exhaustivo del código para garantizar que solo las aplicaciones de alta calidad pasen al entorno de producción.

Para obtener más información sobre la configuración de la canalización desde [!UICONTROL Cloud Manager]La interfaz de usuario de , consulte los documentos [Configuración de canalizaciones de producción](configuring-production-pipelines.md) y [Configuración de canalizaciones que no sean de producción.](configuring-non-production-pipelines.md)

### Modos de implementación flexibles {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] ofrece a los clientes modos de implementación flexibles y configurables para que puedan ofrecer experiencias en función de las cambiantes exigencias comerciales.

Gracias a su modo de activación automático, el código se implementa automáticamente en un entorno basado en eventos específicos como la confirmación de código. También puede programar implementaciones de código durante intervalos de tiempo especificados, incluso fuera del horario laboral.

Independientemente del activador de implementación, siempre se realizan comprobaciones de calidad como parte de la ejecución de la canalización de CI/CD, cada vez que se activa una implementación. Las comprobaciones de calidad incluyen la inspección del código, las pruebas de seguridad y las pruebas de rendimiento ofrecidas de forma inmediata, sin que los clientes o sus socios deban realizar ningún esfuerzo.

Para obtener más información sobre la implementación del código y las pruebas de calidad, consulte [Implementación del código](deploying-code.md)

### Escalado automático {#autoscaling}

[!UICONTROL Cloud Manager] detecta la necesidad de aplicar capacidades adicionales cuando el entrono de producción está sujeto a cargas altas e inusuales, y lleva esas capacidades adicionales en línea de manera automática mediante la función de escalado automático.

En un evento de escalado automático, [!UICONTROL Cloud Manager] activa automáticamente el proceso de aprovisionamiento de escalado automático, envía una notificación del evento de escalado automático y, en pocos minutos, lleva las capacidades adicionales en línea. Las capacidades adicionales se aprovisionarán en el entorno de producción, en las mismas zonas y coincidirán con el mismo sistema de especificaciones que ejecuta Dispatcher o los nodos publicados.

La función escalado automático se aplicará solo a Dispatcher o a las capas publicadas y se ejecutará siempre mediante un método de escalado horizontal, con un segmento adicional de Dispatcher o del par publicado como mínimo y un máximo de diez segmentos. Se escalará manualmente cualquier capacidad adicional aprovisionada en un periodo de diez días laborables, tal como determine el CSE (ingeniero de administración del éxito del cliente).

>[!NOTE]
>Los clientes interesados en explorar si el escalado automático es apropiado o no para su aplicación deben ponerse en contacto con su CSE o representante de Adobe.
