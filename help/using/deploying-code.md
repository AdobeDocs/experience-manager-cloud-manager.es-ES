---
title: Implementar el código
seo-title: Implementar el código
description: Proporciona información general sobre el proceso de implementación en Cloud Manager
seo-description: Aprenda a implementar el código una vez que haya configurado la canalización (repositorio, entorno y entorno de prueba)
uuid: 4e3807e1-437e-4922-ba48-0bcadf293a99
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 832a4647-9b83-4a9d-b373-30fe16092b15
feature: Implementación de código
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
translation-type: tm+mt
source-git-commit: 9e7c6f7241900432155a1a32abfb440fb3f93172
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 1%

---

# Implementar el código {#deploy-your-code}

## Implementación de código con Cloud Manager {#deploying-code-with-cloud-manager}

Una vez configurada la canalización de producción (repositorio, entorno y entorno de prueba), estará listo para implementar el código.

1. Haga clic en **Implementar** desde Cloud Manager para iniciar el proceso de implementación.

   ![](assets/Deploy1.png)

1. Aparece la pantalla **Pipeline Execution**.

   Haga clic en **Build** para iniciar el proceso.

   ![](assets/Deploy2.png)

1. El proceso de compilación completa implementa el código.

   En el proceso de compilación participan las siguientes etapas:

   1. Implementación de fase
   1. Prueba de prueba
   1. Implementación de producción

   >[!NOTE]
   >
   >Además, puede revisar los pasos de varios procesos de implementación consultando los registros o revisando los resultados de los criterios de prueba.

   La **implementación por fases** incluye los siguientes pasos:

   * Validación: Este paso garantiza que la canalización esté configurada para utilizar los recursos disponibles actualmente, por ejemplo, que la rama configurada exista, los entornos estén disponibles.
   * Prueba de compilación y unidad: Este paso ejecuta un proceso de compilación en contenedores. Consulte [Explicación del entorno de compilación](/help/using/build-environment-details.md) para obtener más información sobre el entorno de compilación.
   * Escaneo de código: Este paso evalúa la calidad del código de la aplicación. Consulte [Comprender los resultados de la prueba](understand-your-test-results.md) para obtener más información sobre el proceso de prueba.
   * Implementar en fase

   ![](assets/Stage_Deployment1.png)

   La **Prueba de fase** incluye los siguientes pasos:

   * Pruebas de seguridad: Este paso evalúa el impacto de seguridad del código de la aplicación en el entorno AEM. Consulte [Comprender los resultados de la prueba](understand-your-test-results.md) para obtener más información sobre el proceso de prueba.
   * Pruebas de rendimiento: Este paso evalúa el rendimiento del código de la aplicación. Consulte [Comprender los resultados de la prueba](understand-your-test-results.md) para obtener más información sobre el proceso de prueba.

   ![](assets/Stage_Testing1.png)

   La **implementación de producción** incluye los siguientes pasos:

   * **Solicitud de aprobación**  (si está habilitada)
   * **Programar implementación de producción**  (si está habilitada)
   * **Compatibilidad con CSE**  (si está habilitada)
   * **Implementar en producción**

   ![](assets/Prod_Deployment1.png)

   >[!NOTE]
   >
   >**Programar implementación de producción** está habilitado al configurar la canalización.
   >
   >
   >Con esta opción, puede programar la implementación de producción o hacer clic en **Now** para ejecutar la implementación de producción inmediatamente.
   >
   >
   >La fecha y la hora programadas se especifican en términos de la zona horaria del usuario.
   >
   >
   >Haga clic en **Confirm** para comprobar la configuración.

   ![](assets/Production_Deployment1.png)

   Una vez que confirme la programación de implementación, se completará la implementación del código.

   Se muestra la siguiente pantalla cuando se selecciona la opción **Now** en el paso anterior.

   ![](assets/Production_Deployment2.png)

## Tiempos de espera {#timeouts}

Los siguientes pasos agotarán el tiempo de espera si se deja esperando los comentarios del usuario:

| Etapa | Tiempo de espera |
|--- |--- |
| Prueba de calidad de código | 7 días |
| Pruebas de seguridad | 7 días |
| Pruebas de rendimiento | 7 días |
| Solicitud de aprobación | 7 días |
| Programar implementación de producción | 7 días |
| Compatibilidad con CSE | 7 días |

## Proceso de implementación {#deployment-process}

En la siguiente sección se describe cómo se implementan los paquetes AEM y Dispatcher en la fase de fase y en la fase de producción.

Cloud Manager carga todos los archivos target/*.zip producidos por el proceso de compilación en una ubicación de almacenamiento.  Estos artefactos se recuperan de esta ubicación durante las fases de implementación de la canalización.

Cuando Cloud Manager se implementa en topologías que no son de producción, el objetivo es completar la implementación lo antes posible y, por lo tanto, los artefactos se implementan en todos los nodos de forma simultánea de la siguiente manera:

1. Cloud Manager determina si cada artefacto es un paquete AEM o dispatcher.
1. Cloud Manager elimina todos los distribuidores del equilibrador de carga para aislar el entorno durante la implementación.

   A menos que se configure lo contrario, puede omitir los cambios del equilibrador de carga en las implementaciones de desarrollo y ensayo, es decir, separar y adjuntar pasos en ambas canalizaciones que no sean de producción, para entornos de desarrollo y para la canalización de producción, para entornos de ensayo.

   ![](assets/load_balancer.png)

   >[!NOTE]
   >
   >Se espera que esta función la usen principalmente los clientes 1-1-1.

1. Cada artefacto de AEM se implementa en cada instancia de AEM a través de las API del administrador de paquetes, con dependencias de paquete que determinan el orden de implementación.

   Para obtener más información sobre cómo puede utilizar paquetes para instalar nuevas funciones, transferir contenido entre instancias y realizar copias de seguridad del contenido del repositorio, consulte Cómo trabajar con paquetes.

   >[!NOTE]
   >
   >Todos los artefactos AEM se implementan tanto en el autor como en los editores. Los modos de ejecución deben aprovecharse cuando se requieran configuraciones específicas de nodos. Para obtener más información sobre cómo los modos de ejecución permiten ajustar la instancia de AEM para un fin específico, consulte Modos de ejecución.

1. El artefacto de Dispatcher se implementa en cada Dispatcher de la siguiente manera:

   1. Las configuraciones actuales se respaldan y copian en una ubicación temporal
   1. Todas las configuraciones se eliminan excepto los archivos inmutables. Consulte Administrar las configuraciones de Dispatcher para obtener más información. Esto borra los directorios para garantizar que no queden archivos huérfanos.
   1. El artefacto se extrae en el directorio `httpd`.  Los archivos inmutables no se sobrescriben. Los cambios que realice en los archivos inmutables del repositorio de Git se ignorarán en el momento de la implementación.  Estos archivos son fundamentales para el marco de Dispatcher de AMS y no se pueden cambiar.
   1. Apache realiza una prueba de configuración. Si no se encuentran errores, el servicio se vuelve a cargar. Si se produce un error, las configuraciones se restauran desde la copia de seguridad, el servicio se vuelve a cargar y el error se devuelve a Cloud Manager.
   1. Cada ruta especificada en la configuración de la canalización se invalida o se vacía de la caché de Dispatcher.

   >[!NOTE]
   >Cloud Manager espera que el artefacto de Dispatcher contenga el conjunto completo de archivos.  Todos los archivos de configuración de Dispatcher deben estar presentes en el repositorio de Git. Si faltan archivos o carpetas, se producirá un error de implementación.

1. Después de la implementación correcta de todos los paquetes de AEM y Dispatcher en todos los nodos, los distribuidores se vuelven a añadir al equilibrador de carga y la implementación se completa.

   >[!NOTE]
   >Puede omitir los cambios del equilibrador de carga en las implementaciones de desarrollo y fase, es decir, separar y adjuntar pasos en ambas canalizaciones que no sean de producción, para entornos de desarrollador y para la canalización de producción, para entornos de ensayo.

### Implementación en fase de producción {#deployment-production-phase}

El proceso de implementación en topologías de producción difiere ligeramente para minimizar el impacto en los visitantes AEM sitio.

Las implementaciones de producción generalmente siguen los mismos pasos que se describen arriba, pero de forma gradual:

1. Implemente AEM paquetes para crear.
1. Desasocie Dispatcher1 del equilibrador de carga.
1. Implemente AEM paquetes para publicar1 y el paquete de Dispatcher para dispatcher1 en paralelo y vacíe la caché de Dispatcher.
1. Vuelva a colocar Dispatcher1 en el equilibrador de carga.
1. Una vez que Dispatcher1 vuelva a estar en servicio, separe Dispatcher2 del equilibrador de carga.
1. Implemente AEM paquetes para publicar2 y el paquete de Dispatcher para dispatcher2 en paralelo y vacíe la caché de Dispatcher.
1. Vuelva a colocar Dispatcher2 en el equilibrador de carga.
Este proceso continúa hasta que la implementación haya llegado a todos los editores y distribuidores de la topología.
