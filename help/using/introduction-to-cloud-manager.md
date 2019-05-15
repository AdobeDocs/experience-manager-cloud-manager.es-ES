---
title: Introducción al Administrador de nube
seo-title: Introducción al Administrador de nube
description: 'Esta página sirve como punto de partida para aprender sobre Cloud Manager. '
seo-description: 'Esta página sirve como punto de partida para aprender sobre Adobe AEM Cloud Manager y resalta los beneficios y las funciones clave. '
uuid: 62 d 68 e 79-c 2 ba -4 d 8 b-ba 7 d -33709014 d 5 b 6
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introducción
discoiquuid: ebcc 91 a 5-be 9 e -4684-8146-d 88 f 4013 d 4 d 1
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Introducción a [!UICONTROL Cloud Manager]{#introduction-to-cloud-manager}

## Introducción {#introduction}

[!UICONTROL Cloud Manager], parte de Adobe Managed Cloud Services, permite a las organizaciones administrar de forma automática Experience Manager en la nube. Incluye un marco de integración continua y de entrega continua (CI/CD) que permite a los equipos de TI y a los socios de implementación acelerar la entrega de personalizaciones o actualizaciones sin comprometer el rendimiento o la seguridad.

Mediante el uso del [!UICONTROL Cloud Manager] portal de cliente de autoservicio, **las organizaciones** pueden realizar o aprovechar lo siguiente:

* **Integración continua/Entrega** continua de código para reducir el tiempo de comercialización de meses/semanas a días/horas.
* **Inspección de código, pruebas de rendimiento y validación de seguridad** basadas en prácticas recomendadas antes de impulsar la producción para minimizar las interrupciones de producción.
* **Implementación automática, programada o manual** incluso fuera de horario laboral para lograr la máxima flexibilidad y control.
* **La función de escala automática** detecta de forma inteligente la necesidad de aumentar la capacidad y coloca automáticamente segmentos de publicador/Publish adicionales en línea.

La siguiente imagen ilustra el flujo de procesos CI/CD utilizado en [!UICONTROL Cloud Manager]:

![](assets/screen_shot_2018-05-12at73843pm.png)

## Funciones principales en [!UICONTROL Cloud Manager]{#key-features-in-cloud-manager}

Las organizaciones pueden aprovechar las siguientes funciones, con [!UICONTROL Cloud Manager]:

### Interfaz de autoservicio {#self-service-interface}

La interfaz de usuario (interfaz de usuario) permite [!UICONTROL Cloud Manager] a los clientes acceder y administrar fácilmente el entorno de nube y la canalización CI/CD para sus aplicaciones de Experience Manager.

Los clientes definen indicadores de rendimiento clave (KPI) específicos de la aplicación: vistas de página pico por minuto y tiempo de respuesta esperado para una carga de página, que finalmente constituye la base para medir una implementación exitosa. Las funciones y los permisos para los distintos integrantes del equipo pueden definirse fácilmente. Aunque la nueva interfaz de autoservicio pone el control en sus manos, también ofrece vínculos a las prácticas recomendadas y a los expertos de Adobe que pueden proporcionar las directrices necesarias según sea necesario.

Para explorar y comenzar con [!UICONTROL Cloud Manager]la interfaz de usuario, consulte [Inicio de sesión por primera vez](https://helpx.adobe.com/experience-manager/cloud-manager/using/first-time-login.html).

### Pipeline CI/CD {#ci-cd-pipeline}

Una de las capacidades clave de [!UICONTROL Cloud Manager] es la capacidad de ejecutar una portada optimizada de CI/CD para acelerar la entrega de código personalizado o actualizaciones, como agregar nuevos componentes en el sitio web.

A través de [!UICONTROL Cloud Manager] la interfaz de usuario, los clientes pueden configurar y desactivar su flujo de CI/CD. Durante este flujo, se ejecuta un exhaustivo análisis de código para garantizar que solo las aplicaciones de alta calidad pasan al entorno de producción.

Para obtener más información sobre la configuración del canal desde [!UICONTROL Cloud Manager]la interfaz de usuario, consulte [Configuración de la cartera de CD/CD](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html).

### Modos de implementación flexibles {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] ofrece a los clientes flexibles y configurables modos de implementación para que puedan entregar experiencias según las cambiantes demandas comerciales.

Con un modo desencadenador automático, el código se implementa automáticamente en un entorno basado en eventos específicos como la transferencia de código. También puede programar implementaciones de código durante los intervalos de tiempo especificados, incluso fuera de los horarios comerciales.

Independientemente del activador de implementación, las comprobaciones de calidad siempre se realizan como parte de la ejecución de la canalización CI/CD, cada vez que se activa una implementación. Las comprobaciones de calidad incluyen, entre otras, la inspección de código, las pruebas de seguridad y la prueba de rendimiento que se entrega, sin que los clientes o sus socios tengan que realizar ningún esfuerzo.

Para obtener más información sobre la implementación de las comprobaciones de código y calidad, consulte [Implementación del código](deploying-code.md)

### Escalado automático {#autoscaling}

[!UICONTROL Cloud Manager] detecta la necesidad de tener capacidad adicional cuando el entorno de producción está sujeto a una carga inusualmente alta y ofrece automáticamente capacidad adicional en línea mediante la función de escalado automático.

Durante un evento de escalado automático, activa [!UICONTROL Cloud Manager] automáticamente el proceso de aprovisionamiento automático, envía una notificación del evento de escala automática y trae la capacidad adicional en cuestión de minutos. La capacidad adicional se aprovisionará en el entorno de producción, en las mismas regiones y coincidirá con las mismas especificaciones del sistema que los nodos Dispatcher/Publish.

La función de escalado automático solo se aplicará al nivel Despachante/Publicar y siempre se ejecutará con un método de escala horizontal, con un mínimo de un segmento adicional de un par Despachante/Publicar y hasta un máximo de diez segmentos. Cualquier capacidad adicional aprovisionada se aplicará manualmente dentro de un período de diez días hábiles, según lo determina CSE (Ingeniero de éxito del cliente).
