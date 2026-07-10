---
title: Canalizaciones de CI/CD
description: Obtenga información acerca de las canalizaciones de CI/CD y cómo administran las implementaciones en entornos de ensayo y producción en Cloud Manager.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
TQID: https://experienceleague.adobe.com/BwkZH2MIbXrzSxf0yk9yeDZZIpw7-Ldue-OPQPkWrdg
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754bid: ff09c71c-26a9-449a-85f8-2aeb8ce96100
subfeature_v2: id: c14b2f98-ee16-4c49-b87b-919c91b01d9d
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 694d3e8dad6e2ba86186a4bf6fdda3739e1041da
workflow-type: tm+mt
source-wordcount: 1122
ht-degree: 50%

---

# Canalizaciones de CI/CD {#ci-cd-pipeline}

Obtenga información acerca de las canalizaciones de CI/CD y cómo administran las implementaciones en entornos de ensayo y producción en Cloud Manager.

## Información general {#overview}

[!UICONTROL Cloud Manager] incluye un marco de trabajo de integración continua/envío continuo (CI/CD), que permite a los equipos de implementación probar y entregar rápidamente código nuevo o actualizado. Los equipos de implementación pueden configurar e iniciar una CI/CD Pipeline automatizada . Esta canalización sigue las prácticas recomendadas de codificación de Adobe para realizar un análisis exhaustivo del código y garantizar la máxima calidad.

La canalización de CI/CD también automatiza los procesos de prueba de unidades y de rendimiento para aumentar la eficiencia e identificar proactivamente los problemas críticos que son costosos de solucionar tras la implementación. Los equipos de implementación pueden acceder a un informe completo de rendimiento del código para obtener visibilidad sobre el impacto potencial en los indicadores clave de rendimiento (KPI) y las validaciones de seguridad críticas si el código se implementa en producción.

## Acerca del proceso de canalización {#pipeline-process}

Este diagrama ilustra lo que sucede una vez que se activa una versión en [!UICONTROL Cloud Manager] mediante una canalización.

![El proceso de canalización](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Paso de canalización | Descripción |
| --- | --- |
| &#x200B;1. Iniciar una versión | Un administrador de implementación activa una versión manualmente, con una confirmación de Git o en función de una programación recurrente. |
| &#x200B;2. Creación de una etiqueta de versión | [!UICONTROL Cloud Manager] crea una etiqueta de Git para marcar la versión con un número de versión generado automáticamente, por ejemplo, `2018.531.245527.0000001222`. |
| &#x200B;3. Compilado como versión con versión generada automáticamente | [!UICONTROL Cloud Manager] compila la aplicación con el número de versión recién asignado. |
| &#x200B;4. Evaluar la calidad del código | [!UICONTROL Cloud Manager] analiza el código fuente y proporciona un resumen antes de que se pueda implementar en el entorno de ensayo. |
| &#x200B;5. Artefactos con versiones almacenados | Los artefactos de la versión se almacenan para su uso posterior en los pasos de implementación. |
| &#x200B;6. Implementación automática de artefactos en el ensayo de AMS AEM | El artefacto de la versión se implementa en el entorno de ensayo. |
| &#x200B;7. Déclencheur de pruebas automatizadas | [!UICONTROL Cloud Manager] ejecuta pruebas de rendimiento y seguridad en el artefacto. |
| &#x200B;8. Implementación del déclencheur de producción | Una vez completadas las pruebas automatizadas, [!UICONTROL Cloud Manager] inicia la implementación en producción. |
| &#x200B;9. [!UICONTROL Cloud Manager] obtiene artefactos para implementar | [!UICONTROL Cloud Manager] extrae los artefactos de la versión almacenados. |
| &#x200B;10. Implementar artefactos en producción | Los artefactos de la versión se implementan en el entorno de producción. |

### Fuentes de código {#code-sources}

Las canalizaciones también pueden variar según el tipo de código que implementan, además de la producción y la no producción.

* **[Canalizaciones de pila completa](#full-stack-pipeline)**: implemente el código completo de la aplicación AEM junto con las configuraciones de HTTPD/Dispatcher.
* **[Canalizaciones de configuración de nivel web](#web-tier-config-pipelines)**: implementen solo configuraciones de HTTPD/Dispatcher.

### Canalizaciones de pila completa {#full-stack-pipeline}

Las canalizaciones de pila completa implementan el código de aplicación de AEM completo en el tiempo de ejecución de AEM y, de forma predeterminada, también implementan configuraciones de nivel web.

Se aplican las siguientes restricciones.

* Un usuario debe iniciar sesión con el rol **Administrador de implementación** para configurar o ejecutar canalizaciones.
* En cualquier momento, solo puede haber una canalización de pila completa por entorno.

A continuación se describe cómo la canalización de pila completa interactúa con una [canalización de configuración de nivel web](#web-tier-config-pipelines).

* La canalización de pila completa para un entorno ignora la configuración de Dispatcher si existe la canalización de configuración de nivel web correspondiente.
* Si la canalización de configuración del nivel web correspondiente para el entorno no existe, el usuario puede configurar la canalización de pila completa para incluir o ignorar la configuración de Dispatcher.

Las canalizaciones de pila completa pueden ser canalizaciones de calidad del código o implementación.

#### Configuración de canalizaciones de pila completa {#configure-full-stack}

Consulte [Agregar una canalización de producción](/help/using/production-pipelines.md#full-stack-code).Consulte [Agregar una canalización que no sea de producción](/help/using/non-production-pipelines.md#add-non-production-pipeline).

### Canalizaciones de configuración de nivel web {#web-tier-config-pipelines}

Las canalizaciones de configuración de nivel web permiten la implementación exclusiva de la configuración de HTTPD/Dispatcher en el tiempo de ejecución de AEM, desacoplándola de otros cambios de código. Es una canalización optimizada que proporciona a los usuarios que solo desean implementar los cambios de configuración de Dispatcher, un medio acelerado para hacerlo en solo unos minutos.

>[!TIP]
>
>Las canalizaciones de configuración de nivel web le permiten almacenar su configuración web en la misma ubicación de origen o en una diferente como canalización de pila completa, según lo que mejor se adapte a la estructura de su proyecto.

Se aplican las siguientes restricciones.

* Un usuario debe iniciar sesión con el rol **Administrador de implementación** para configurar o ejecutar canalizaciones.
* En cualquier momento, solo puede haber una canalización de configuración de nivel web por entorno.
* El usuario no puede configurar una canalización de configuración de nivel web cuando se está ejecutando su canalización de pila completa correspondiente.

A continuación se describe cómo la canalización de configuración del nivel web interactúa con la [canalización de pila completa](#full-stack-pipeline).

* Si no se configura una canalización de configuración de nivel web para un entorno, el usuario puede elegir incluir o ignorar la configuración de Dispatcher al configurar la canalización de pila completa.
* Una vez que una canalización de configuración de nivel web está configurada para un entorno, su canalización de pila completa correspondiente (si existe) ignora la configuración de Dispatcher durante la ejecución y la implementación.
* Después de eliminar una canalización de configuración de nivel web, su canalización de pila completa correspondiente (si existe) se restablece para implementar las configuraciones de Dispatcher durante su ejecución.

>[!NOTE]
>
>Para los programas de AMS con la implementación azul-verde habilitada, las actualizaciones de nivel web utilizan la implementación móvil de forma predeterminada. Utilice una canalización de pila completa si necesita una implementación azul-verde para los cambios del nivel web.

#### Configuración de canalizaciones de nivel web {#configure-web-tier}

Consulte [Agregar una canalización de producción](/help/using/production-pipelines.md#web-tier-config).Consulte [Agregar una canalización que no sea de producción](/help/using/non-production-pipelines.md#add-non-production-pipeline).

### Compilaciones más rápidas con Smart Build {#use=smart-build}

Cloud Manager ahora usa una estrategia de compilación optimizada llamada **Smart Build**, que usa el almacenamiento en caché a nivel de módulo para acelerar el proceso de compilación. Durante cada compilación, solo se reconstruyen los módulos que han cambiado, mientras que los módulos sin modificar se reutilizan de la caché.

La generación inteligente está disponible para canalizaciones de implementación de calidad de código y pila completa (desarrollo, fase y producción).

Vea [Agregar una canalización que no es de producción](/help/using/non-production-pipelines.md#add-non-production-pipeline) y [Acerca del uso de Smart Build en una canalización que no es de producción](/help/using/non-production-pipelines.md#about-smart-build).


### Configuración de una canalización de CI/CD {#how-to-setup-a-ci-cd-pipeline}

Para obtener más información acerca de la configuración de la canalización, consulte los documentos [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) y [Configuración de canalizaciones que no son de producción](/help/using/non-production-pipelines.md).

## Puertas de calidad {#quality-gates}

La canalización de CI/CD proporciona puertas de calidad o criterios de aceptación que deben cumplirse para que el código pueda moverse del entorno de ensayo al de implementación. Hay tres puertas en la canalización:

* Calidad de código
* Pruebas de rendimiento
* Pruebas de seguridad

Para cada una de estas puertas, hay tres niveles de problemas que se pueden identificar:

* **Crítico**: los problemas críticos identificados por la puerta causan un fallo inmediato de la canalización.
* **Importante**: los problemas importantes identificados por la puerta hacen que la canalización entre en un estado de pausa. Un administrador de implementación, un administrador de proyectos o un propietario empresarial pueden anular los problemas, lo que permite que la canalización continúe. De forma alternativa, pueden aceptar los problemas, lo cual haría que la canalización se detenga con un error.
* **Información**: los problemas de información identificados por la puerta se proporcionan exclusivamente con fines informativos y no tienen impacto en la ejecución de la canalización.

Este es un ejemplo de análisis de código con problemas identificados.

![Ejemplo de análisis de código](/help/assets/quality-gate-failed.png)

### Cómo configurar puertas {#how-to-setup-gates}

Consulte el documento [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) para obtener más información sobre la configuración de las puertas de código, calidad y rendimiento.
