---
title: Introducción a Cloud Manager
seo-title: Introducción a Cloud Manager
description: 'Esta página sirve como punto de partida para aprender sobre Cloud Manager. '
seo-description: 'Esta página sirve como punto de partida para conocer Adobe AEM Cloud Manager y destaca las ventajas y las funciones clave. '
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introducción
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
translation-type: tm+mt
source-git-commit: d7c9ab3795fb3df02ab7dffd1328760ccd914a18

---


# Introducción a [!UICONTROL Cloud Manager]{#introduction-to-cloud-manager}

## Introducción {#introduction}

[!UICONTROL Cloud Manager], que forma parte de los servicios de nube administrados de Adobe, permite a las organizaciones administrar Experience Manager de forma automática en la nube. Incluye un marco de integración continua y entrega continua (CI/CD) que permite a los equipos de TI y a los socios de implementación acelerar la entrega de personalizaciones o actualizaciones sin comprometer el rendimiento o la seguridad.

Mediante el uso del portal para clientes de autoservicio [!UICONTROL Cloud Manager] , **las organizaciones** pueden realizar o aprovechar lo siguiente:

* **Integración continua / Entrega** continua del código para reducir el tiempo de salida al mercado de meses/semanas a días/horas.
* **Inspección del código, pruebas de rendimiento y validación** de seguridad basadas en las prácticas recomendadas antes de pasar a la producción para minimizar las interrupciones de producción.
* **Implementación** automática, programada o manual, incluso fuera del horario laboral, para obtener la máxima flexibilidad y control.
* **La función de escalado** automático detecta de forma inteligente la necesidad de aumentar la capacidad y automáticamente pone en línea segmentos adicionales de Dispatcher/Publish.

La siguiente imagen ilustra el flujo de proceso CI/CD utilizado en [!UICONTROL Cloud Manager]:

![](assets/screen_shot_2018-05-12at73843pm.png)

## Características principales de [!UICONTROL Cloud Manager]{#key-features-in-cloud-manager}

Las organizaciones pueden aprovechar las siguientes funciones con [!UICONTROL Cloud Manager]:

### Interfaz de autoservicio {#self-service-interface}

La interfaz de usuario (IU) [!UICONTROL Cloud Manager] permite a los clientes acceder y administrar fácilmente el entorno de nube y la canalización de CI/CD para sus aplicaciones de Experience Manager.

Los clientes definen los Indicadores de rendimiento clave (KPI) específicos de la aplicación: vistas de páginas de mayor actividad por minuto y tiempo de respuesta esperado para una carga de página, que en última instancia constituyen la base para medir una implementación exitosa. Las funciones y los permisos de los distintos integrantes del equipo se pueden definir fácilmente. Aunque la nueva interfaz de autoservicio pone el control en sus manos, también ofrece vínculos a prácticas recomendadas y acceso a expertos de Adobe que pueden proporcionar la orientación necesaria según sea necesario.

Para explorar y comenzar con la IU [!UICONTROL Cloud Manager]de Adobe, consulte Inicio de sesión [por](https://helpx.adobe.com/experience-manager/cloud-manager/using/first-time-login.html)primera vez.

### Canalización CI/CD {#ci-cd-pipeline}

Una de las funciones clave de [!UICONTROL Cloud Manager] es la capacidad de utilizar una canalización de CD/CI optimizada para acelerar la entrega de código personalizado o actualizaciones, como la adición de nuevos componentes en el sitio web.

A través de la interfaz de usuario, los clientes pueden configurar y poner en marcha su canalización de CD/CI. [!UICONTROL Cloud Manager] Durante esta canalización, se realiza un análisis exhaustivo del código para garantizar que solo las aplicaciones de alta calidad pasan al entorno de producción.

Para obtener más información sobre la configuración de canalización desde [!UICONTROL Cloud Manager]la interfaz de usuario de Adobe, consulte [Configurar la canalización de CI/CD](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html).

### Modos de implementación flexibles {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] ofrece a los clientes modos de implementación flexibles y configurables para que puedan ofrecer experiencias según las cambiantes exigencias comerciales.

Con un modo de activación automático, el código se implementa automáticamente en un entorno basado en eventos específicos como la confirmación de código. También puede programar implementaciones de código durante intervalos de tiempo especificados, incluso fuera del horario laboral.

Independientemente del activador de implementación, siempre se realizan comprobaciones de calidad como parte de la ejecución de la canalización CI/CD, cada vez que se activa una implementación. Las comprobaciones de calidad incluyen, la inspección de código, las pruebas de seguridad y las pruebas de rendimiento ofrecidas de forma inmediata, sin que sea necesario ningún esfuerzo por parte de los clientes o sus socios.

Para obtener más información sobre la implementación de códigos y comprobaciones de calidad, consulte [Implementación del código](deploying-code.md)

### Escala automática {#autoscaling}

[!UICONTROL Cloud Manager] detecta la necesidad de capacidad adicional cuando el entorno de producción está sujeto a una carga inusualmente alta y automáticamente trae capacidad adicional en línea mediante la función de escalado automático.

Durante un evento de escalado automático, [!UICONTROL Cloud Manager] activa automáticamente el proceso de aprovisionamiento de escalado automático, envía una notificación del evento de escalado automático y pone en línea la capacidad adicional en cuestión de minutos. La capacidad adicional se aprovisionará en el entorno de producción, en las mismas regiones y coincidiendo con las mismas especificaciones del sistema que los nodos Dispatcher/Publish en ejecución.

La función de escalado automático solo se aplicará al nivel Dispatcher/Publish y siempre se ejecutará mediante un método de escalado horizontal, con un mínimo de un segmento adicional de un par Dispatcher/Publish y un máximo de diez segmentos. Cualquier capacidad adicional aprovisionada se escalará manualmente en un período de diez días laborables, según lo determina el CSE (Ingeniero de Éxito del Cliente).
