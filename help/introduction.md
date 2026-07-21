---
title: Introducción a Cloud Manager para AMS
description: Empiece aquí para conocer Cloud Manager para Adobe Managed Services (AMS) y cómo permite a las organizaciones autoadministrar Adobe Experience Manager en la nube.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
TQID: https://experienceleague.adobe.com/VR-H6ubMFgVrkfzDvY4JWYlUtM-Dkztdewr5LiSZK1w
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
  - id: ff09c71c-26a9-449a-85f8-2aeb8ce96100
subfeature_v2:
  - id: a4d14782-c381-4db2-89e3-8cf3f31b103c
  - id: c14b2f98-ee16-4c49-b87b-919c91b01d9d
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ee4f497a8bb5fb2d37fd8283721ebc9891f9053a
workflow-type: tm+mt
source-wordcount: 1266
ht-degree: 69%

---

# Introducción a [!UICONTROL Cloud Manager] para AMS {#introduction-to-cloud-manager}

Para conocer Cloud Manager for AMS (Adobe Managed Services) y cómo permite a las organizaciones autoadministrar Adobe Experience Manager en la nube, comience aquí.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Introducción a Cloud Manager para AMS"
>abstract="Permite a las organizaciones autoadministrar Adobe Experience Manager en la nube mediante un marco de trabajo de CI/CD. Este marco ayuda a los equipos a acelerar las personalizaciones o actualizaciones sin poner en riesgo el rendimiento o la seguridad."
>additional-url="https://experienceleague.adobe.com/es/docs/experience-manager-learn/cloud-service/cloud-manager/programs#cloud-manager" text="Creación de programas"
>additional-url="https://experienceleague.adobe.com/es/docs/experience-manager-learn/cloud-service/cloud-manager/environments#cloud-manager" text="Creación de entornos"

## Introducción {#introduction}

[!UICONTROL Cloud Manager] para Adobe Experience Manager ofrece a los desarrolladores la capacidad de crear experiencias de cliente impactantes mediante flujos de trabajo optimizados, basados en las prácticas recomendadas de Adobe Experience Manager. Las canalizaciones de CI/CD optimizadas para Adobe Experience Manager le permiten combinar flujos de trabajo de desarrollo protegiendo el código, que luego pasa a estar listo para la producción. Durante la fase de compilación, las actualizaciones del código personalizado se prueban exhaustivamente, comparándolas con las prácticas recomendadas para ofrecer aplicaciones fiables a sus clientes. Cloud Manager utiliza un enfoque de API abierta y le permite integrarse con sus sistemas sin interrumpir los procesos y herramientas existentes.

>[!NOTE]
>
>Esta documentación describe específicamente las funciones y características de Cloud Manager para Adobe Managed Services (AMS).
>
>El equivalente para AEM as a Cloud Service se encuentra en la [Documentación de AEM as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/implementing/home).

Con Cloud Manager, su equipo de desarrollo se beneficia de las siguientes funciones:

* Integración y entrega continuas (CI/CD) del código para reducir los ciclos de desarrollo de meses o semanas a días u horas.
* Inspección del código, pruebas de rendimiento y validación de seguridad basadas en procedimientos recomendados antes de pasar a producción, para minimizar las interrupciones en esta última.
* Conectividad de API para complementar los procesos de DevOps existentes.
* Escalado automático que detecta la necesidad de aumentar la capacidad y aprovisiona automáticamente segmentos adicionales de Dispatcher/publicación.

![CI/CD flow](/help/assets/screen_shot_2018-05-12at73843pm.png)El flujo del proceso de CI/CD que se usa en [!UICONTROL Cloud Manager].

## Funciones opcionales en [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Las siguientes secciones resaltan las funciones clave de Cloud Manager.

### Interfaz de autoservicio {#self-service-interface}

Para explorar y empezar con la IU de [!UICONTROL Cloud Manager], consulte el documento [Primer inicio de sesión](/help/getting-started/first-time-login.md).

La interfaz de usuario (IU) para [!UICONTROL Cloud Manager] le permite acceder y administrar el entorno de la nube y la canalización de CI/CD fácilmente para sus aplicaciones de Adobe Experience Manager.

Puede definir indicadores clave de rendimiento (KPI) específicos de la aplicación, como las vistas de página máximas por minuto o el tiempo de respuesta de carga de página esperado. Estos KPI sirven de base para medir el éxito de la implementación. Las funciones y los permisos de los distintos integrantes del equipo se pueden definir fácilmente. La interfaz de autoservicio le proporciona control total. También proporciona enlaces a recursos sobre prácticas recomendadas y acceso a expertos en Adobe para obtener orientación cuando sea necesario.

### Canalización de CI/CD {#ci-cd-pipeline}

Una de las funcionalidades clave de [!UICONTROL Cloud Manager] es la capacidad de usar una canalización de CD/CI optimizada para acelerar la entrega de código personalizado o las actualizaciones, como la adición de nuevos componentes en el sitio web.

A través de la interfaz de usuario de [!UICONTROL Cloud Manager], puede configurar e iniciar su canalización de CD/CI. Como parte de esta canalización, se realiza un análisis exhaustivo del código para garantizar que solo las aplicaciones de alta calidad pasen al entorno de producción.

Para obtener más información sobre la configuración de canalizaciones desde la interfaz de usuario de [!UICONTROL Cloud Manager], consulte [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) y [Configuración de canalizaciones que no son de producción](/help/using/non-production-pipelines.md).

### Modos de implementación flexibles {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] ofrece a los clientes modos de implementación flexibles y configurables para que puedan entregar experiencias en función de las cambiantes exigencias empresariales.

Gracias a su modo de activación automático, el código se implementa automáticamente en un entorno basado en eventos específicos como la confirmación de código. También puede programar implementaciones de código durante intervalos de tiempo especificados, incluso fuera del horario laboral.

Independientemente del activador de la implementación, siempre se efectúan comprobaciones de calidad como parte de la ejecución de la canalización de CI/CD, cada vez que se activa una implementación. Las comprobaciones de calidad incluyen la inspección del código, las pruebas de seguridad y las pruebas de rendimiento, todas las cuales se entregan como funciones estándar sin que usted o sus socios deban realizar ningún esfuerzo.

Para obtener más información acerca de la implementación del código y las pruebas de calidad, consulte el documento [Implementación del código](/help/using/code-deployment.md).

## Funciones opcionales en Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager ofrece funciones avanzadas adicionales que benefician a su proyecto según la configuración y las necesidades de su entorno en particular. Para obtener más información, póngase en contacto con su ingeniero de éxito del cliente (Customer Success Engineer, CSE) o su representante de Adobe si estas funciones le interesan.

### Escalado automático {#autoscaling}

Cuando el entorno de producción está sujeto a una carga inusualmente alta, [!UICONTROL Cloud Manager] detecta la necesidad de capacidad adicional y la aprovisiona automáticamente mediante su característica de escalado automático.

Ante un evento de esta naturaleza, [!UICONTROL Cloud Manager] déclencheur automáticamente el proceso de aprovisionamiento de escalado automático, envía una notificación del evento de escalado automático y aprovisiona capacidad adicional en cuestión de minutos. Las capacidades adicionales se aprovisionan en el entorno de producción y en las mismas regiones, lo que coincide con las especificaciones del sistema de los nodos de Dispatcher/publicación en ejecución.

La función de escalado automático se aplica al nivel de Dispatcher/publicación, utilizando escalado horizontal para agregar de uno a diez segmentos de pares de Dispatcher/publicación. Se escala manualmente cualquier capacidad adicional aprovisionada en un período de diez días laborables, tal como determine el ingeniero de administración del éxito del cliente (Customer Success Engineer, CSE) de Adobe.

>[!NOTE]
>
>Si le interesa explorar si el escalado automático es apropiado para su aplicación, póngase en contacto con su CSE o representante de Adobe.

### Implementaciones azules/verdes {#blue-green}

La implementación azul/verde es una técnica que reduce el tiempo de inactividad y el riesgo al ejecutar dos entornos de producción idénticos llamados azul y verde.

En cualquier momento, solo uno de los entornos está activo, y sirve todo el tráfico de producción. En general, el azul es el entorno activo actual y el verde está inactivo.

* La implementación azul/verde es un complemento de las canalizaciones de CI/CD de Cloud Manager en el que se crea un segundo conjunto de instancias de publicación y Dispatcher (verde) y se utiliza para implementaciones. A continuación, las instancias verdes se adjuntan al equilibrador de carga de producción y las instancias antiguas (azules) se eliminan y terminan.
* Esta implementación azul/verde trata las instancias como transitorias y cada iteración de una canalización azul/verde crea un nuevo conjunto de servidores de publicación y Dispatcher.
* Se crea un equilibrador de carga verde como parte de la configuración. Este equilibrador de carga nunca cambia y es el destino de su URL verde o de &quot;prueba&quot;.
* Durante una implementación azul/verde, se creará una réplica exacta de los niveles de publicación/Dispatcher existentes.

#### Flujo de implementación azul/verde {#flow}

Cuando la implementación azul/verde está habilitada, el flujo de implementación difiere del flujo de implementación de Cloud Service estándar.

| Etapa | Implementación azul/verde | Implementación estándar |
| --- | --- | --- |
| 1 | Implementación de autor | Implementación de autor |
| 2 | Pausa para pruebas | - |
| 3 | Creación de una infraestructura verde | - |
| 4 | Implementación en niveles verdes de Publish/Dispatcher | Implementación en publicador |
| 5 | Pausa para pruebas (hasta 24 horas) | - |
| 6 | Adición de la infraestructura verde al equilibrador de carga de producción | - |
| 7 | Eliminación de la infraestructura azul del equilibrador de carga de producción | - |
| 8 | Pausa para la aprobación final (hasta 24 horas) | - |
| 9 | La infraestructura azul se termina automáticamente | - |
| 10 | La canalización finaliza | - |

#### Implementación de azul/verde {#implementing}

Todos los usuarios de AMS que utilicen Cloud Manager para implementaciones de producción pueden emplear la implementación azul/verde. Sin embargo, el uso de la implementación azul/verde requiere una validación adicional de los entornos y la configuración por parte de un CSE de Adobe.

Si le interesa la implementación azul/verde, tenga en cuenta los siguientes requisitos y limitaciones y póngase en contacto con su CSE.

#### Requisitos y limitaciones {#limitations}

* Azul/verde solo está disponible para pares de publicación/Dispatcher.
* Los pares de previsualización de Dispatcher/publicación no forman parte de las implementaciones azules/verdes.
* Cada par de Dispatcher/publicación es idéntico a los otros pares de Dispatcher/publicación.
* Azul/verde solo está disponible en el entorno de producción.
* Azul/verde está disponible en AWS y en Azure.
* Azul/verde no está disponible para los clientes solo de Assets.
