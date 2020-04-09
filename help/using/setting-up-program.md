---
title: Configurar el programa
seo-title: Configurar el programa
description: Después del embarque, el propietario de la empresa tendrá que realizar una configuración inicial del programa.
seo-description: 'Después de la integración, el propietario de la empresa deberá realizar alguna configuración inicial de Adobe AEM Cloud Manager. Esto implica configurar la descripción del programa y definir los KPI que se utilizarán para las pruebas de rendimiento. '
uuid: 9ecf8743-1f5a-4744-86af-e2256567642f
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: c2393540-e852-4f7c-aafd-1427209065d2
translation-type: tm+mt
source-git-commit: 16893b8bcd2b2d681a14bb6be3786e358e1952fb

---


# Configurar el programa {#setup-your-program}

Después del embarque, el propietario de la empresa deberá completar la configuración inicial del programa. Esto implica configurar la descripción del programa y definir los indicadores de rendimiento clave (KPI) que se utilizarán para las pruebas de rendimiento. Opcionalmente, se puede cargar una miniatura. Además, el propietario de la empresa puede configurar el aprovisionamiento de entornos al configurar el programa.

Los KPI definidos sirven de referencia para las pruebas de rendimiento que se pasan cada vez que se ejecuta la canalización.

>[!NOTE]
>
>Los KPI definidos se miden en pruebas ejecutadas en el entorno de **etapa** . Normalmente, estos KPI se reducen para adaptarse a las capacidades del entorno de la etapa.
>
>Por ejemplo, un usuario que espere un promedio de 1000 vistas de página por minuto en el **Entorno** de producción y tenga cuatro servidores de distribución/publicación en producción debería escalarlo a 250 vistas de página por minuto (suponiendo que su entorno de etapa consiste en un solo par de despachantes/servidores de publicación).
>
>Además, muchos usuarios tendrán una red de Envío de contenido (CDN), como Akamai o CloudFront, frente al entorno de producción. Dado que [!UICONTROL Cloud Manager] las pruebas se comparan directamente con el entorno del escenario, el KPI debe reflejar únicamente el tráfico que se espera que pase a través de la CDN, es decir, los errores de caché. Normalmente, este será un subconjunto relativamente pequeño del tráfico total de producción.

## Uso [!UICONTROL Cloud Manager] para configurar el Programa {#using-cloud-manager-to-setup-your-program}

Siga los pasos a continuación para configurar el programa y definir KPI:

1. Haga clic en **Ajustes Programa** para inicio del proceso de configuración en [!UICONTROL Cloud Manager].

   ![image1](assets/set-up-program/setup1.png)

   >[!NOTE]
   > Siempre puede cambiar, editar o agregar un nuevo programa desde la barra de acciones, como se muestra en la figura siguiente.

   ![image1](assets/set-up-program/setup2.png)


1. La pantalla Programa **de** configuración muestra Editar información de Programa.

1. Verá tres opciones: **General**, **KPI** y **Aprovisionamiento** .

1. En la ficha **General** , cargue una miniatura en el programa. También puede agregar una descripción relevante al programa.

   ![](assets/Setup_Program-General.png)

1. En **KPI**, puede definir sus dos KPI (expectativas para cada implementación). Los KPI independientes se definen para **AEM Sites** y **AEM Assets**. Podrá especificar los KPI para los productos con licencia.

   **AEM Sites**

   1. ¿Cuál es el tiempo de respuesta del porcentaje 95 que usted puede aceptar?

      * Valor recomendado: 3 segundos
   1. ¿Cuántas Vistas de página por minuto bajo la carga máxima?

      * Valor recomendado: 200 vistas de página por minuto
   **AEM Assets**

   Desde su lanzamiento inicial, Cloud Manager ha podido ejecutar pruebas de rendimiento para programas de AEM Sites. Con esta versión, también se ha agregado la capacidad de ejecutar pruebas de rendimiento para programas de AEM Assets. La prueba de rendimiento de los recursos se realiza cargando los recursos repetidamente durante un período de prueba de 30 minutos y midiendo el tiempo de procesamiento de cada recurso, así como varias métricas a nivel del sistema.
Durante la configuración de Programa, se especifican KPI específicos de recursos:

   * Tiempo de procesamiento del porcentaje 95
   * Recursos cargados por minuto
   ![](assets/Setup_Program-KPIs.png)

1. En **Aprovisionamiento**, puede realizar la vista o editar la configuración de aprovisionamiento para entornos de producción y no de producción en su programa. Verá que la escala **automática está activada** si la escala automática se ha activado para el programa.

   >[!NOTE]
   >
   >* La función de escalado automático solo se aplica al entorno de producción y es posible que no esté disponible para todos los programas del cliente.
   >* La escala a petición no está disponible para esta versión de [!UICONTROL Cloud Manager].


   ![](assets/Setup_Program-Provisioning.png)

1. Haga clic en **Guardar** para completar el asistente de configuración.

   >[!NOTE]
   >
   >Siempre puede editar el programa una vez que el programa inicial ya se haya configurado. Siga los pasos a continuación para obtener más detalles.

## Edición de un Programa

1. Vaya a la solución en la pantalla de inicio de **Cloud Manager** .

   ![](assets/SetUpProgram5.png)

1. Seleccione la solución y haga clic en **Editar** para actualizar o modificar el programa, como se muestra en la figura siguiente.

   ![](assets/SetUpProgram6.png)

1. Se abre la pantalla **Editar Programa** que permite actualizar o modificar el programa.

   ![](assets/Editing_Program-screen3.png)

## Pasos siguientes {#the-next-steps}

Si ya ha configurado la **canalización**, la siguiente ejecución tendrá en cuenta la configuración actualizada. Si todavía no ha configurado la canalización, siga los pasos para configurar la canalización primero.

Consulte [Configuración de la canalización](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html) CI/CD para configurar la canalización.
