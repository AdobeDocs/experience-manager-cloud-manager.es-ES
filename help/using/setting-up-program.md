---
title: Configuración del programa
seo-title: Configuración del programa
description: Tras la admisión, el propietario del negocio deberá realizar alguna configuración inicial del programa.
seo-description: 'Tras la admisión, el propietario del negocio deberá realizar alguna configuración inicial de Adobe AEM Cloud Manager. Esto implica configurar la descripción del programa y definir los KPI que se utilizarán para la prueba de rendimiento. '
uuid: 9 ecf 8743-1 f 5 a -4744-86 af-e 2256567642 f
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introducción
discoiquuid: c 2393540-e 852-4 f 7 c-aafd -1427209065 d 2
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Configuración del programa {#setup-your-program}

Tras la admisión, el propietario del negocio deberá completar una configuración inicial del programa. Esto implica configurar la descripción del programa y definir los indicadores de rendimiento clave (KPI) que se utilizarán para la prueba de rendimiento. Opcionalmente, se puede cargar una miniatura. Además, el propietario comercial puede configurar los entornos al configurar el programa.

Los KPI definidos sirven como referencia para la prueba de rendimiento que se pasa cada vez que se ejecuta la canalización.

>[!NOTE]
>
>Los KPI definidos se miden en las pruebas ejecutándose en el entorno **de etapa** . Normalmente, estos KPI se reducen para adaptarse a las capacidades del entorno de etapa.
>
>Por ejemplo, un usuario espera una media de 1000 vistas de página por minuto en **el entorno de producción** y tener cuatro servidores de distribuidor/publicación en producción debería escalar esto a 250 vistas de página por minuto (suponiendo que su entorno de etapa consiste únicamente en un único par de servidor de publicación/publicación).
>
>Además, muchos usuarios tendrán una red de entrega de contenido (CDN), como Akamai o cloudfront frente al entorno de producción. Dado que [!UICONTROL Cloud Manager] las pruebas todavía se comparan directamente con el entorno de etapa, el KPI debe reflejar solamente el tráfico esperado para pasar por el CDN, es decir, la caché se deshace. Generalmente, éste será un subconjunto relativamente pequeño del tráfico total de producción.

## Uso [!UICONTROL Cloud Manager] para configurar el programa {#using-cloud-manager-to-setup-your-program}

Siga los pasos a continuación para configurar el programa y definir KPI:

1. Click **Setup Program** to start the setup process in [!UICONTROL Cloud Manager].

   ![](assets/SetUpProgram1.png)

1. La **pantalla Programa** de configuración muestra la información del programa Editar.

1. Verá tres opciones como **General**, **KPI** y **Aprovisionamiento** .

1. En **la** ficha General, cargue una miniatura en el programa. También puede agregar una descripción relevante al programa.

   ![](assets/Setup_Program-General.png)

1. En **KPI**, puede definir los dos KPI (expectativas para cada implementación). Los KPI separados se definen para **AEM Sites** y **AEM Assets**. Podrá especificar los KPI para los productos que tiene licencia.

   **AEM Sites**

   1. ¿Cuál es el tiempo de respuesta del percentil 95 que es aceptable para usted?

      * Valor recomendado - 3 segundos
   1. ¿Cuántas vistas de página por minuto bajo la carga máxima?

      * Valor recomendado - 200 vistas de página por minuto
   **AEM Assets**

   Desde su lanzamiento inicial, Cloud Manager ha podido ejecutar pruebas de rendimiento para programas de AEM Sites. Con esta versión, se ha agregado la capacidad de ejecutar pruebas de rendimiento para programas AEM Assets. La prueba de rendimiento de los recursos se realiza cargando recursos repetidamente durante un período de prueba de 30 minutos y midiendo el tiempo de procesamiento de cada recurso, así como varias métricas de nivel de sistema.
Durante la configuración del programa, se especifican KPI específicos de recursos:

   * 95 º tiempo de procesamiento de percentil
   * Recursos cargados por minuto
   ![](assets/Setup_Program-KPIs.png)

1. En **Aprovisionamiento**, puede ver o editar la configuración de aprovisionamiento para entornos de producción y sin producción en el programa. Verá **la Escala automática activada**, si se ha activado el escalado automático para el programa.

   >[!NOTE]
   >
   >* La función de escala automática solo se aplica al entorno de producción y es posible que no esté disponible para todos los programas de cliente.
   >* La escala a petición no está disponible para esta versión de [!UICONTROL Cloud Manager].


   ![](assets/Setup_Program-Provisioning.png)

1. Haga clic **en Guardar** para completar el asistente para configuración.

   >[!NOTE]
   >
   >Siempre puede editar el programa una vez configurado el programa inicial. Siga los pasos a continuación para obtener más detalles.

## Edición de un programa

1. Vaya a la solución en la pantalla de inicio de **Cloud Manager** .

   ![](assets/SetUpProgram5.png)

1. Seleccione la solución y haga clic en **Editar** para actualizar o modificar el programa, como se muestra en la figura siguiente.

   ![](assets/SetUpProgram6.png)

1. Se abre la pantalla **Editar programa** que permite actualizar o modificar el programa.

   ![](assets/Editing_Program-screen3.png)

## Pasos siguientes {#the-next-steps}

Si ya ha configurado **Pipeline**, la próxima ejecución tendrá en cuenta la configuración actualizada. Si todavía no ha configurado la canalización, siga los pasos para configurar su canal primero.

Consulte [Configuración de la cartera CI/CD](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html) para configurar la canalización.
