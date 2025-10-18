---
title: Implementación de código
description: Obtenga información sobre cómo implementar su código y qué sucede en Cloud Manager cuando lo hace.
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: b98e1711f1f98f52977dd6cb4cd2bc834d81a360
workflow-type: tm+mt
source-wordcount: '1636'
ht-degree: 98%

---


# Implementación de código {#code-deployment}

Obtenga información sobre cómo implementar su código y qué sucede en Cloud Manager cuando lo hace.

## Implementación de código con Cloud Manager {#deploying-code-with-cloud-manager}

Una vez que haya configurado la canalización de producción, incluidos el repositorio y los entornos necesarios, estará listo para implementar el código.

1. Haga clic en **Implementación** desde Cloud Manager para iniciar el proceso de implementación.

   ![Botón Implementar](/help/assets/Deploy1.png)

1. Se muestra la pantalla **Ejecución de canalización**. Haga clic en **Generar** para iniciar el proceso.

   ![Botón Generar](/help/assets/Deploy2.png)

El proceso de compilación inicia el proceso de implementación del código, incluidos los siguientes pasos:

* Implementación de fase
* Prueba de fase
* Implementación de producción

Puede revisar los pasos de varios procesos de implementación consultando los registros o los resultados de los criterios de prueba.

## Pasos de implementación {#deployment-steps}

Durante cada paso de la implementación se producen varias acciones que se describen en esta sección. Consulte la sección [Detalles del proceso de implementación](#deployment-process) para obtener detalles técnicos sobre cómo se implementa el código en sí mismo entre bastidores.

### Paso de implementación de fase {#stage-deployment}

El paso **Implementación de fase** incluye las siguientes acciones:

* **Validación**: Este paso garantiza que la canalización esté configurada para utilizar los recursos disponibles actualmente. Por ejemplo, probar que la rama configurada existe y que los entornos están disponibles.
* **Prueba de compilación y unidad**: este paso ejecuta un proceso de compilación en contenedores. Consulte el documento [El entorno de compilación](/help/getting-started/build-environment.md) para obtener más información.
* **Escaneo de código**: este paso evalúa la calidad del código de la aplicación. Consulte [Comprender los resultados de la prueba](/help/using/code-quality-testing.md) para obtener más información sobre el proceso de prueba.
* **Implementar en fase**

![Implementación de fase](/help/assets/Stage_Deployment1.png)

### Paso de prueba de fase {#stage-testing}

El paso **Prueba de fase** incluye las siguientes acciones:

* **Pruebas de seguridad**: este paso evalúa el impacto del código en la seguridad en el entorno AEM. Consulte el documento [Comprender los resultados de la prueba](/help/using/code-quality-testing.md) para obtener más información sobre el proceso de prueba.
   * **Pruebas de rendimiento**: este paso evalúa el rendimiento del código. Consulte [Comprender los resultados de la prueba](/help/using/code-quality-testing.md) para obtener más información sobre el proceso de prueba.

### Paso de implementación de producción {#production-deployment}

El paso **Implementación de producción** incluye las siguientes acciones:

* **Solicitud de aprobación**
   * Esta opción está habilitada al configurar la canalización.
   * Con esta opción, puede programar la implementación de producción o hacer clic en **Ahora** para ejecutar la implementación de producción inmediatamente.
* **Programar implementación de producción**
   * Esta opción está habilitada al configurar la canalización.
   * La fecha y la hora programadas se especifican en términos de la zona horaria del usuario.
     ![Programar implementación](/help/assets/Production_Deployment1.png)
* **Compatibilidad con CSE** (si está habilitado)
* **Implementar en producción**

![Implementación de producción](/help/assets/Prod_Deployment1.png)

Una vez completada la implementación, el código se encuentra en su entorno de destino y puede ver los registros.

![Implementación completada](/help/assets/Production_Deployment2.png)

## Tiempos de espera {#timeouts}

Los siguientes pasos agotarán el tiempo de espera si se deja esperando los comentarios del usuario:

| Paso | Tiempo de espera |
|--- |--- |
| Prueba de calidad del código | 7 días |
| Pruebas de seguridad | 7 días |
| Pruebas de rendimiento | 7 días |
| Solicitud de aprobación (fase) | 7 días |
| Solicitud de aprobación (producción) | 14 días |
| Programar implementación de producción | 14 días |
| Implementación de producción administrada | 14 días |

## Detalles del proceso de implementación {#deployment-process}

Cloud Manager carga todos los archivos target/*.zip producidos por el proceso de compilación en una ubicación de almacenamiento. Estos artefactos se recuperan de esta ubicación durante las fases de implementación de la canalización.

Cuando Cloud Manager se implementa en topologías que no son de producción, la meta es completar la implementación lo antes posible y, por lo tanto, los artefactos se implementan en todos los nodos de forma simultánea de la siguiente manera:

1. Cloud Manager determina si cada artefacto es un paquete de AEM o Dispatcher.
1. Cloud Manager elimina todos los distribuidores del equilibrador de carga para aislar el entorno durante la implementación.

   * A menos que se configure lo contrario, puede omitir los cambios del equilibrador de carga en las implementaciones de desarrollo y ensayo. Es decir, para el entorno de desarrollo, desasocie y adjunte pasos tanto en las canalizaciones que no sean de producción, como para el entorno de ensayo en la canalización de producción.

   ![Omisión del equilibrador de carga](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >Se espera que los clientes 1-1-1 utilicen esta función.

1. Cada artefacto de AEM se implementa en cada instancia de AEM a través de las API del Administrador de paquetes, con dependencias de paquete que determinan el orden de implementación.

   * Para obtener más información sobre cómo utilizar paquetes para instalar nuevas funcionalidades, transferir contenido entre instancias y realizar copias de seguridad del contenido del repositorio. Consulte [Administrador de paquetes](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).

   >[!NOTE]
   >
   >Todos los artefactos AEM se implementan tanto en los autores como en los editores. Los modos de ejecución deben aprovecharse cuando se requieran las configuraciones específicas de los nodos. Para obtener más información sobre cómo los modos de ejecución le permiten ajustar la instancia de AEM para un fin específico, consulte la [sección Ejecutar Modos del documento Implementar en AEM as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/implementing/deploying/overview#runmodes).

1. El artefacto de Dispatcher se implementa en cada distribuidor de la siguiente manera:

   1. Se realiza una copia de seguridad de las configuraciones actuales y se copian en una ubicación temporal.
   1. Todas las configuraciones se eliminan, excepto los archivos inmutables. Consulte [Configuraciones de Dispatcher](/help/getting-started/dispatcher-configurations.md) para obtener más información. Esto borra los directorios para garantizar que no queden archivos huérfanos.
   1. El artefacto se extrae al directorio `httpd`. Los archivos inmutables no se sobrescriben. Los cambios que realice en los archivos inmutables del repositorio de Git se ignoran en el momento de la implementación. Estos archivos son fundamentales para el marco de trabajo de Dispatcher de AMS y no se pueden cambiar.
   1. Apache realiza una prueba de configuración. Si no se encuentran errores, el servicio se vuelve a cargar. Si se encuentran errores, las configuraciones se restauran desde la copia de seguridad, el servicio se vuelve a cargar y el error se devuelve a Cloud Manager.
   1. Cada ruta especificada en la configuración de la canalización se invalida o se vacía de la caché de Dispatcher.

   >[!NOTE]
   >
   >Cloud Manager espera que el artefacto de Dispatcher contenga el conjunto completo de archivos. Todos los archivos de configuración de Dispatcher deben estar presentes en el repositorio de Git. Si faltan archivos o carpetas, se produce un error de implementación.

1. Después de la implementación correcta de todos los paquetes de AEM y Dispatcher en todos los nodos, los distribuidores se vuelven a añadir al equilibrador de carga y se completa la implementación.

   >[!NOTE]
   >
   >Puede omitir los cambios del equilibrador de carga en las implementaciones de desarrollo y ensayo. Es decir, para el entorno de desarrollo, desasocie y adjunte pasos tanto en las canalizaciones que no sean de producción, como para el entorno de ensayo en la canalización de producción.

### Implementación en la fase de producción {#deployment-production-phase}

El proceso de implementación en topologías de producción difiere ligeramente para minimizar el impacto de los visitantes del sitio de AEM.

Las implementaciones de producción generalmente siguen los mismos pasos que se describen arriba, pero en secuencia:

1. Implemente paquetes de AEM para crear.
1. Desasocie dispatcher1 del equilibrador de carga.
1. Implemente los paquetes AEM para publish1 y el paquete de Dispatcher para dispatcher1 en paralelo y vacíe la caché de Dispatcher.
1. Vuelva a colocar dispatcher1 en el equilibrador de carga.
1. Una vez que dispatcher1 vuelva a estar en servicio, desasocie dispatcher2 del equilibrador de carga.
1. Implemente los paquetes AEM para publish2 y el paquete del distribuidor para dispatcher2 en paralelo y vacíe la caché de Dispatcher.
1. Vuelva a colocar dispatcher2 en el equilibrador de carga.

Este proceso continúa hasta que la implementación haya llegado a todos los editores y distribuidores de la topología.

## Modo de ejecución de canalización de emergencia {#emergency-pipeline}

En situaciones críticas, es posible que los clientes de Managed Services de Adobe necesiten implementar cambios de código en sus entornos de ensayo y producción inmediatamente. Esta capacidad les permite evitar el ciclo de prueba completo de Cloud Manager.

Para resolver estas situaciones, la canalización de producción de Cloud Manager se puede ejecutar en modo de emergencia. Cuando se utiliza este modo, no se ejecutan los pasos de prueba de seguridad y rendimiento. Todos los demás pasos, incluidos los pasos de aprobación configurados, se ejecutan como en el modo de ejecución normal de la canalización.

>[!NOTE]
>
>La función de modo de ejecución de canalización de emergencia se activa programa por programa. La activación la realizan los ingenieros de éxito del cliente.

### Uso del modo de ejecución de canalización de emergencia {#using-emergency-pipeline}

Al iniciar la ejecución de una canalización de producción, puede elegir entre el modo normal o de emergencia en un cuadro de diálogo. Esta opción está disponible si la función de modo de ejecución de canalización de emergencia está activada para el programa. Esta opción está disponible una vez habilitada la función.

![Ejecutar opciones de canalización](/help/assets/execution-emergency1.png)

Al ver la página de detalles de ejecución de la canalización para una ejecución operada en modo de emergencia, las rutas en la parte superior de la pantalla muestran el indicador de que la canalización se está ejecutando en modo de emergencia.

![Rutas del modo de emergencia](/help/assets/execution-emergency2.png)

La ejecución de una canalización en modo de emergencia también se puede realizar mediante la API o CLI de Cloud Manager. Para iniciar una ejecución en modo de emergencia, envíe una solicitud `PUT` al extremo de ejecución de la canalización con el parámetro de consulta `?pipelineExecutionMode=EMERGENCY` o, cuando utilice la CLI:

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## Volver a ejecutar una implementación de producción {#reexecute-deployment}

En raras ocasiones, los pasos de implementación de producción pueden fallar por motivos transitorios. En estos casos, puede volver a ejecutar el paso de implementación de producción siempre y cuando se haya completado, independientemente de si se ha realizado correctamente, se ha cancelado o no. Se puede volver a ejecutar utilizando la misma canalización que consta de los tres pasos siguientes:

1. **El paso de validación**: se trata de la misma validación que se produce durante la ejecución normal de una canalización.
1. **El paso de compilación**: en el contexto de una nueva ejecución, el paso de compilación copia artefactos, sin embargo, no ejecuta realmente un nuevo proceso de compilación.
1. **El paso de implementación de producción**: utiliza la misma configuración y opciones que el paso de implementación de producción en una ejecución de canalización normal.

En estas circunstancias, cuando se puede volver a ejecutar, la página de estado de la canalización de producción contiene la opción **Volver a ejecutar** junto a la opción habitual **Descargar registro de compilación**.

![La opción Volver a ejecutar en la ventana de información general de la canalización](/help/assets/re-execute.png)

>[!NOTE]
>
>En una nueva ejecución, el paso de compilación se etiqueta en la IU para reflejar que está copiando artefactos y no reconstruyendo.

### Limitaciones {#limitations}

* Volver a ejecutar el paso de implementación de producción solo está disponible para la última ejecución.
* Volver a ejecutar no está disponible para ejecuciones de reversión o de actualización del estado.
* Si la última ejecución ha fallado en cualquier momento antes del paso de implementación de producción, no será posible volver a ejecutarla.


### Volver a ejecutar la API {#reexecute-api}

Además de estar disponible en IU, puede utilizar [la API de Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Pipeline-Execution) para activar las nuevas ejecuciones, así como identificar las que se activaron como ejecuciones nuevas.

#### Activación de una nueva ejecución {#triggering}

Para activar una nueva ejecución, se debe realizar la solicitud `PUT` al vínculo HAL `http://ns.adobe.com/adobecloud/rel/pipeline/reExecute` en el estado del paso de implementación de producción.

* Si este vínculo está presente, la ejecución se puede reiniciar desde ese paso.
* Si está ausente, la ejecución no se puede reiniciar desde ese paso. 

Este vínculo solo está disponible para el paso de implementación de producción.

```javascript
 {
  "_links": {
    "http://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/metrics",
      "templated": false
    },
    "self": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530",
      "templated": false
    }
  },
  "id": "6187842",
  "stepId": "2983530",
  "phaseId": "1575676",
  "action": "deploy",
  "environment": "weretail-global-b75-prod",
  "environmentType": "prod",
  "environmentId": "59254",
  "startedAt": "2022-01-20T14:47:41.247+0000",
  "finishedAt": "2022-01-20T15:06:19.885+0000",
  "updatedAt": "2022-01-20T15:06:20.803+0000",
  "details": {
  },
  "status": "FINISHED"
```

El valor de la sintaxis del vínculo HAL `href` solo es un ejemplo y el valor real siempre debe leerse desde el vínculo HAL y no generarse.

Enviar una solicitud `PUT` a este extremo genera una respuesta `201` si es correcta. El cuerpo de respuesta es la representación de la nueva ejecución. Esto es similar a iniciar una ejecución normal a través de la API.

#### Identificación de una ejecución que se ha vuelto a ejecutar {#identifying}

El sistema identifica las ejecuciones que se vuelven a ejecutar por el valor `RE_EXECUTE` en el campo del activador.