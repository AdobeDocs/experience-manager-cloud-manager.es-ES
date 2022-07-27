---
title: Introducción a Cloud Manager para AMS
description: Empiece aquí para conocer Cloud Manager para Adobe Managed Services (AMS) y cómo permite a las organizaciones administrar Adobe Experience Manager en la nube.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 22d40a1f07f56ee7a7dddb4897e4079f1e346674
workflow-type: tm+mt
source-wordcount: '1292'
ht-degree: 10%

---


# Introducción a [!UICONTROL Cloud Manager] para AMS {#introduction-to-cloud-manager}

Empiece aquí para conocer Cloud Manager para los servicios de administración de Adobe (AMS) y cómo permite a las organizaciones administrar Adobe Experience Manager en la nube.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Introducción a Cloud Manager para AMS"
>abstract="Permite a las organizaciones administrar Adobe Experience Manager en la nube. Incluye un marco de trabajo de integración y entrega continuas (CI/CD) que permite a los equipo de TI y a los asociados de la implementación acelerar la entrega de las personalizaciones o actualizaciones sin poner en riesgo el rendimiento o la seguridad."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en#cloud-manager" text="Crear programas"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en#cloud-manager" text="Crear entornos"

## Introducción {#introduction}

[!UICONTROL Cloud Manager] para Adobe Experience Manager ofrece a los desarrolladores la capacidad de crear experiencias de clientes impactantes mediante flujos de trabajo optimizados basados en las prácticas recomendadas de Adobe Experience Manager. Las canalizaciones CI/CD optimizadas para Adobe Experience Manager le permiten combinar fácilmente los flujos de trabajo de desarrollo con solo marcar el código, que puede moverse hasta llegar a estar listo para la producción. Durante la fase de compilación, las actualizaciones de código personalizado se prueban exhaustivamente comparándolas con las prácticas recomendadas para ofrecer aplicaciones fiables para sus clientes. Cloud Manager utiliza un enfoque de API abierto y le permite integrarse con sus sistemas sin interrumpir los procesos y herramientas existentes.

>[!NOTE]
>
>Esta documentación describe específicamente las funciones y características de Cloud Manager para Adobe Managed Services (AMS).
>
>La documentación equivalente para AEM as a Cloud Service se encuentra en la [AEM documentación as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/home.html)

Con Cloud Manager, su equipo de desarrollo se beneficia de las siguientes funciones:

* Integración continua/entrega continua (CI/CD) del código para reducir el tiempo de salida al mercado de meses/semanas a días/horas

* Inspección del código, pruebas de rendimiento y validación de seguridad basadas en las prácticas recomendadas antes de pasar a producción para minimizar las interrupciones en la misma

* Conectividad de API para complementar los procesos de DevOps existentes

* Escalado automático que detecta de forma inteligente la necesidad de aumentar la capacidad y pone en línea automáticamente segmentos adicionales de Dispatcher/publicaciones

Esta imagen ilustra el flujo de proceso CI/CD utilizado en [!UICONTROL Cloud Manager]:

![Flujo de CI/CD](/help/assets/screen_shot_2018-05-12at73843pm.png)

## Características principales de [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

A continuación se muestra una profundización en algunas funciones clave de Cloud Manager.

### Interfaz de autoservicio {#self-service-interface}

La interfaz de usuario (IU) de [!UICONTROL Cloud Manager] le permite acceder y administrar fácilmente el entorno de la nube y la canalización de CI/CD para sus aplicaciones Adobe Experience Manager.

Los indicadores clave de rendimiento (KPI) específicos de la aplicación (como las vistas de página máximas por minuto y el tiempo de respuesta esperado para una carga de página) constituyen la base para medir una implementación correcta. Las funciones y los permisos de los distintos integrantes del equipo se pueden definir fácilmente. La interfaz de autoservicio pone el control en sus manos, pero también ofrece vínculos a recursos de prácticas recomendadas y acceso a expertos en Adobe que pueden proporcionar la orientación necesaria según sea necesario.

Para explorar y empezar con [!UICONTROL Cloud Manager]La interfaz de usuario de , consulte el documento [Primer inicio de sesión.](/help/getting-started/first-time-login.md)

### Canalización de CI/CD {#ci-cd-pipeline}

Una de las funciones clave de [!UICONTROL Cloud Manager] es la capacidad de utilizar una canalización de CD/CI optimizada para acelerar la entrega de código personalizado o las actualizaciones, como la adición de nuevos componentes en el sitio web.

A través de [!UICONTROL Cloud Manager] La interfaz de usuario de puede configurar y poner en marcha la canalización de CD/CI. Como parte de esta canalización, se realiza un análisis exhaustivo del código para garantizar que solo las aplicaciones de alta calidad pasen al entorno de producción.

Para obtener más información sobre la configuración de la canalización desde [!UICONTROL Cloud Manager]La interfaz de usuario de , consulte los documentos [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) y [Configuración de canalizaciones que no sean de producción.](/help/using/non-production-pipelines.md)

### Modos de implementación flexibles {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] ofrece modos de implementación flexibles y configurables para que pueda ofrecer experiencias según las cambiantes exigencias comerciales.

Con un modo de déclencheur automático, el código se implementa automáticamente en un entorno basado en eventos específicos como la confirmación de código. También puede programar implementaciones de código durante intervalos de tiempo especificados, incluso fuera del horario laboral.

Independientemente del déclencheur de implementación, siempre se realizan comprobaciones de calidad como parte de la ejecución de la canalización CI/CD cada vez que se activa una implementación. Las comprobaciones de calidad incluyen, inspección de código, pruebas de seguridad y pruebas de rendimiento, todo lo cual se entrega de forma predeterminada sin que usted o sus socios deban realizar ningún esfuerzo.

Para obtener más información sobre la implementación del código y las comprobaciones de calidad, consulte el documento [Implementar código.](/help/using/code-deployment.md)

## Funciones opcionales en Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager ofrece funciones avanzadas adicionales que pueden ser beneficiosas para su proyecto según la configuración y las necesidades de su entorno en particular. Si estas funciones le interesan, póngase en contacto con su ingeniero de éxito del cliente (CSE) o su representante de Adobe para discutir más a fondo.

### Escalado automático {#autoscaling}

Cuando el entorno de producción está sujeto a una carga inusualmente alta, [!UICONTROL Cloud Manager] detecta la necesidad de capacidad adicional y pone en línea automáticamente la capacidad adicional mediante su función de escalado automático.

En tal caso, [!UICONTROL Cloud Manager] déclencheur automáticamente el proceso de aprovisionamiento de escalado automático, envía una notificación del evento de escalado automático y pone en línea capacidad adicional en cuestión de minutos. La capacidad adicional se aprovisiona en el entorno de producción, en las mismas regiones y que coinciden con las mismas especificaciones del sistema que ejecuta los nodos Dispatcher/publicación.

La función de escalado automático se aplica solo al nivel de Dispatcher/publicación y se ejecuta mediante un método de escalado horizontal, con un segmento adicional de Dispatcher/grupo de publicación mínimo de diez segmentos. Se escalará manualmente cualquier capacidad adicional aprovisionada en un periodo de diez días laborables, tal como determine el CSE (ingeniero de administración del éxito del cliente).

>[!NOTE]
>
>Si le interesa explorar si el escalado automático es apropiado para su aplicación, póngase en contacto con su CSE o representante de Adobe.

### Implementaciones azules/verdes {#blue-green}

La implementación azul/verde es una técnica que reduce el tiempo de inactividad y el riesgo al ejecutar dos entornos de producción idénticos llamados azul y verde.

En cualquier momento, solo uno de los entornos está activo, y el entorno en directo sirve todo el tráfico de producción. En general, el azul es el entorno activo actual y el verde está inactivo.

* La implementación azul/verde es un complemento de las canalizaciones de CD/CI de Cloud Manager en el que se crea un segundo conjunto de instancias de publicación y Dispatcher (verde) y se utiliza para implementaciones. A continuación, las instancias verdes se adjuntan al equilibrador de carga de producción y las instancias antiguas (azul) se eliminan y finalizan.
* Esta implementación de azul/verde trata las instancias como transitorias y cada iteración de una canalización azul/verde creará un nuevo conjunto de servidores de publicación y Dispatcher.
* Se creará un equilibrador de carga verde como parte de la configuración. Este equilibrador de carga nunca cambiará y es a lo que debería apuntar su URL verde o de &quot;prueba&quot;.
* Durante una implementación azul/verde, se creará una réplica exacta de los niveles existentes de publicación/Dispatcher (tal y como se lee en la TDL).

#### Flujo de implementación azul/verde {#flow}

Cuando la implementación en azul/verde está habilitada, el flujo de implementación difiere del flujo de implementación del Cloud Service estándar.

| Etapa | Implementación azul/verde | Implementación estándar |
|---|---|---|
| 1 | Implementación para autor | Implementación para autor |
| 2 | Pausa para realizar pruebas | - |
| 3 | Se crea una infraestructura verde | - |
| 4 | Implementación en niveles verdes de publicación/Dispatcher | Implementación para editor |
| 5 | Pausar para pruebas (hasta 24 horas) | - |
| 6 | La infraestructura verde se agrega al equilibrador de carga de producción | - |
| 7 | La infraestructura azul se elimina del equilibrador de carga de producción- |
| 8 | La infraestructura azul se cierra automáticamente | - |

#### Implementación de azul/verde {#implementing}

Todos los usuarios de AMS que utilicen Cloud Manager para implementaciones de producción pueden utilizar la implementación en azul/verde. Sin embargo, el uso de la implementación azul/verde requiere una validación adicional de los entornos y la configuración por parte de un CSE de Adobe.

Si le interesa la implementación azul/verde, tenga en cuenta los siguientes requisitos y limitaciones y póngase en contacto con su CSE.

#### Requisitos y limitaciones {#limitations}

* Azul/verde solo está disponible para pares de publicación/Dispatcher.
* La vista previa de los pares de Dispatcher/Publish no forma parte de las implementaciones en azul/verde.
* Cada par de Dispatcher/publish es idéntico a cada otro par de Dispatcher/publish.
* Azul/verde solo está disponible en el entorno de producción.
* Azul/verde está disponible en AWS y en Azure.
* Azul/verde no está disponible para los clientes solo de Assets.
