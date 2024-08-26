---
title: Introducción a Cloud Manager para AMS
description: Empiece aquí para conocer Cloud Manager para Adobe Managed Services (AMS) y cómo permite a las organizaciones autoadministrar Adobe Experience Manager en la nube.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 4c4a2688cab8e5c81efa4b7b5e26f3c7b5dc30d6
workflow-type: tm+mt
source-wordcount: '1256'
ht-degree: 55%

---


# Introducción a [!UICONTROL Cloud Manager] para AMS {#introduction-to-cloud-manager}

Empiece aquí para conocer Cloud Manager for AMS (Adobe Managed Services) y cómo permite a las organizaciones autoadministrar Adobe Experience Manager en la nube.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Introducción a Cloud Manager para AMS"
>abstract="Permite a las organizaciones autoadministrar Adobe Experience Manager en la nube. Incluye un marco de trabajo de integración y entrega continuas (CI/CD) que permite a los equipos de TI y a los asociados de la implementación acelerar la entrega de las personalizaciones o actualizaciones sin poner en riesgo el rendimiento o la seguridad."
>additional-url="https://experienceleague.adobe.com/es/docs/experience-manager-learn/cloud-service/cloud-manager/programs#cloud-manager" text="Creación de programas"
>additional-url="https://experienceleague.adobe.com/es/docs/experience-manager-learn/cloud-service/cloud-manager/environments#cloud-manager" text="Creación de entornos"

## Introducción {#introduction}

[!UICONTROL Cloud Manager] para Adobe Experience Manager ofrece a los desarrolladores la capacidad de crear experiencias de cliente impactantes mediante flujos de trabajo optimizados, basados en las prácticas recomendadas de Adobe Experience Manager. Las canalizaciones de CI/CD optimizadas para Adobe Experience Manager le permiten combinar flujos de trabajo de desarrollo fácilmente con solo registrar el código, que puede moverse hasta estar listo para la producción. Durante la fase de compilación, las actualizaciones del código personalizado se prueban exhaustivamente, comparándolas con las prácticas recomendadas para ofrecer aplicaciones fiables a sus clientes. Cloud Manager utiliza un enfoque de API abierta y le permite integrarse con sus sistemas sin interrumpir los procesos y herramientas existentes.

>[!NOTE]
>
>Esta documentación describe específicamente las funciones y características de Cloud Manager para Adobe Managed Services (AMS).
>
>El equivalente para AEM as a Cloud Service se encuentra en la [Documentación de AEM as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/implementing/home).

Con Cloud Manager, su equipo de desarrollo se beneficia de las siguientes funciones:

* Integración y entrega continuas (CI/CD) del código para reducir el tiempo de salida al mercado de meses o semanas a días u horas.

* Inspección del código, pruebas de rendimiento y validación de seguridad basadas en prácticas recomendadas antes de pasar a producción, para minimizar las interrupciones en esta.

* Conectividad de API para complementar los procesos de DevOps existentes.

* Escalado automático que detecta de forma inteligente la necesidad de aumentar la capacidad y pone en línea automáticamente segmentos adicionales de Dispatcher/publicación.

![Flujo de CI/CD](/help/assets/screen_shot_2018-05-12at73843pm.png)Flujo de proceso de CI/CD usado en [!UICONTROL Cloud Manager].

## Características principales de [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

A continuación se profundiza en algunas características clave de Cloud Manager.

### Interfaz de autoservicio {#self-service-interface}

La interfaz de usuario (IU) para [!UICONTROL Cloud Manager] le permite acceder y administrar el entorno de la nube fácilmente, así como la canalización de CD/CI fácilmente para sus aplicaciones de Adobe Experience Manager.

Puede definir indicadores clave de rendimiento (KPI) específicos a la aplicación, como las vistas de página máximas por minuto o el tiempo de respuesta de carga de página esperado. Estos KPI sirven de base para medir el éxito de la implementación. Las funciones y los permisos de los distintos integrantes del equipo se pueden definir fácilmente. La interfaz de autoservicio le proporciona control total. También proporciona enlaces a recursos sobre prácticas recomendadas y acceso a expertos en Adobe para obtener orientación cuando sea necesario.

Para explorar y empezar a usar la interfaz de usuario de [!UICONTROL Cloud Manager], consulte [Primer inicio de sesión](/help/getting-started/first-time-login.md).

### Canalización de CI/CD {#ci-cd-pipeline}

Una de las funcionalidades clave de [!UICONTROL Cloud Manager] es la capacidad de utilizar una canalización de CD/CI optimizada para acelerar el envío de código personalizado o las actualizaciones, como la adición de nuevos componentes en el sitio web.

A través de la IU de [!UICONTROL Cloud Manager], los clientes pueden configurar y poner en marcha su canalización de CD/CI. Como parte de esta canalización, se realiza un análisis exhaustivo del código para garantizar que solo las aplicaciones de alta calidad pasen al entorno de producción.

Para obtener más información sobre la configuración de la canalización desde la interfaz de usuario de [!UICONTROL Cloud Manager], consulte [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) y [Configuración de canalizaciones que no son de producción](/help/using/non-production-pipelines.md).

### Modos de implementación flexibles {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] ofrece a los clientes modos de implementación flexibles y configurables para que puedan entregar experiencias en función de las cambiantes exigencias empresariales.

Gracias a su modo de activación automático, el código se implementa automáticamente en un entorno basado en eventos específicos como la confirmación de código. También puede programar implementaciones de código durante intervalos de tiempo especificados, incluso fuera del horario laboral.

Independientemente del activador de la implementación, siempre se efectúan comprobaciones de calidad como parte de la ejecución de la canalización de CI/CD, cada vez que se activa una implementación. Las comprobaciones de calidad incluyen la inspección del código, las pruebas de seguridad y las pruebas de rendimiento, todas ellas listas para usarse y sin que usted o sus socios deban realizar ningún esfuerzo.

Para obtener más información acerca de la implementación del código y las pruebas de calidad, consulte [Implementación del código](/help/using/code-deployment.md).

## Funciones opcionales en Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager ofrece funciones avanzadas adicionales, que pueden ser beneficiosas para su proyecto según la configuración y las necesidades de su entorno en particular. Si estas funciones le interesan, póngase en contacto con su ingeniero de éxito del cliente (Customer Success Engineer, CSE) o su representante de Adobe para hablarlo con más detalle.

### Escalado automático {#autoscaling}

Cuando el entorno de producción está sujeto a una carga inusualmente alta, [!UICONTROL Cloud Manager] detecta la necesidad de capacidad adicional y la pone en línea automáticamente mediante su funcionalidad de escalado automático.

Ante un evento de esta naturaleza, [!UICONTROL Cloud Manager] activa inmediatamente el proceso de aprovisionamiento de escalado automático, envía una notificación del evento de escalado automático y, en pocos minutos, lleva las capacidades adicionales en línea. Las capacidades adicionales se aprovisionan en el entorno de producción, en las mismas regiones y con las mismas especificaciones del sistema que los nodos de Dispatcher/publicación en ejecución.

La función escalado automático se aplica al nivel de Dispatcher/publicación, utilizando escalado horizontal para agregar de uno a diez segmentos de pares de Dispatcher/publicación. Se escalará manualmente cualquier capacidad adicional aprovisionada en un período de diez días laborables, tal como determine el ingeniero de administración del éxito del cliente (Customer Success Engineer, CSE) de Adobe.

>[!NOTE]
>
>Si le interesa explorar si el escalado automático es apropiado para su aplicación, póngase en contacto con su CSE o representante de Adobe.

### Implementaciones azules/verdes {#blue-green}

La implementación azul/verde es una técnica que reduce el tiempo de inactividad y el riesgo al ejecutar dos entornos de producción idénticos llamados azul y verde.

En cualquier momento, solo uno de los entornos está activo, y sirve todo el tráfico de producción. En general, el azul es el entorno activo actual y el verde está inactivo.

* La implementación azul/verde es un complemento de las canalizaciones de CI/CD de Cloud Manager en el que se crea un segundo conjunto de instancias de publicación y Dispatcher (verde) y se utiliza para implementaciones. A continuación, las instancias verdes se adjuntan al equilibrador de carga de producción y las instancias antiguas (azules) se eliminan y finalizan.
* Esta implementación azul/verde trata las instancias como transitorias y cada iteración de una canalización azul/verde crea un nuevo conjunto de servidores de publicación y Dispatcher.
* Se crea un equilibrador de carga verde como parte de la configuración. Este equilibrador de carga nunca cambia y es a lo que debería apuntar su URL verde o de &quot;prueba&quot;.
* Durante una implementación azul/verde, se crea una réplica exacta de los niveles de Dispatcher/publicación existentes.

#### Flujo de implementación azul/verde {#flow}

Cuando la implementación azul/verde está habilitada, el flujo de implementación difiere del flujo de implementación de Cloud Service estándar.

| Etapa | Implementación azul/verde | Implementación estándar |
|---|---|---|
| 1 | Implementación de autor | Implementación de autor |
| 2 | Pausa para pruebas | - |
| 3 | Creación de una infraestructura verde | - |
| 4 | Implementación en niveles verdes de publicación/Dispatcher | Implementación en publicador |
| 5 | Pausa para pruebas (hasta 24 horas) | - |
| 6 | Adición de la infraestructura verde al equilibrador de carga de producción | - |
| 7 | Eliminación de la infraestructura azul del equilibrador de carga de producción |
| 8 | Pausa para la aprobación final (hasta 24 horas) | - |
| 9 | La infraestructura azul se cierra automáticamente | - |
| 10 | La canalización finaliza | - |

#### Implementación del azul/verde {#implementing}

Todos los usuarios de AMS que utilicen Cloud Manager para implementaciones de producción pueden utilizar la implementación azul/verde. Sin embargo, el uso de la implementación azul/verde requiere una validación adicional de los entornos y la configuración por parte de un CSE de Adobe.

Si le interesa la implementación azul/verde, tenga en cuenta los siguientes requisitos y limitaciones y póngase en contacto con su CSE.

#### Requisitos y limitaciones {#limitations}

* Azul/verde solo está disponible para pares de Dispatcher/editor.
* Los pares de previsualización de Dispatcher/publicación no forman parte de las implementaciones azules/verdes.
* Cada par de Dispatcher/publicación es idéntico a los otros pares de Dispatcher/editor.
* Azul/verde solo está disponible en el entorno de producción.
* Azul/verde está disponible en AWS y en Azure.
* Azul/verde no está disponible para clientes solo de Assets.
