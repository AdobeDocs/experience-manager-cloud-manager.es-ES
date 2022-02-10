---
title: Configurar el programa
seo-title: Set Up Your Program
description: Después de la incorporación, el propietario de la empresa tendrá que realizar alguna configuración inicial del programa.
seo-description: After onboarding, the business owner will need to do some initial setup of Adobe AEM Cloud Manager. This involves setting the program description and defining the KPIs which will be used for performance testing.
feature: Getting Started
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 71d44c7e3673ca62fcd2203ecc0bc4ed9fa22002
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 1%

---

# Configurar el programa {#setup-your-program}

Después de la incorporación, el propietario de la empresa deberá completar la configuración inicial del programa. Esto implica configurar la descripción del programa y definir los indicadores clave de rendimiento (KPI) que se utilizarán para las pruebas de rendimiento. Opcionalmente, se puede cargar una miniatura. Además, el propietario del negocio puede configurar el aprovisionamiento de entornos mientras configura el programa.

Los KPI definidos sirven como punto de referencia para las pruebas de rendimiento que se pasan cada vez que se ejecuta la canalización.

>[!NOTE]
>Los KPI definidos se miden en pruebas ejecutadas en la variable **fase** entorno. Normalmente, estos KPI se reducen para adaptarse a las capacidades del entorno de ensayo.
>Por ejemplo, un usuario espera un promedio de 1000 vistas de página por minuto en su producción **Entorno** y tener cuatro servidores de Dispatcher/Publish en producción debería escalar esto a 250 vistas de página por minuto (suponiendo que su entorno de ensayo consiste en un único par de Dispatcher/servidor de publicación).
>Además, muchos usuarios tendrán una red de entrega de contenido (CDN), como Akamai o CloudFront, delante de su entorno de producción. Since [!UICONTROL Cloud Manager] pruebas con el entorno de ensayo directamente, el KPI debe reflejar únicamente el tráfico que se espera que pase a través de la CDN, es decir, la caché no funciona. Normalmente, este será un subconjunto relativamente pequeño del tráfico total de producción.

## Uso [!UICONTROL Cloud Manager] para configurar el programa {#using-cloud-manager-to-setup-your-program}

Siga los pasos a continuación para configurar el programa y definir los KPI:

1. Haga clic en **Programa de instalación** para iniciar el proceso de configuración en [!UICONTROL Cloud Manager].

   ![image1](assets/set-up-program/setup1.png)

   >[!NOTE]
   > Siempre puede cambiar, editar o agregar un nuevo programa desde la barra de acciones, como se muestra en la figura siguiente.

   ![image1](assets/set-up-program/setup2.png)


1. La variable **Programa de instalación** muestra la pantalla Editar información del programa.

1. Verá tres opciones como **General**, **KPI** y **Aprovisionamiento** pestaña .

1. En **General** , cargue una miniatura en el programa. También puede agregar una descripción relevante al programa.

   ![](assets/Setup_Program-General.png)

1. En **KPI**, puede definir sus dos KPI (expectativas para cada implementación). Se definen KPI independientes para **AEM Sites** y **AEM Assets**. Podrá especificar los KPI para los productos con licencia.

   **AEM Sites**

   1. ¿Cuál es el tiempo de respuesta del percentil 95 que es aceptable para usted?

      * Valor recomendado: 3 segundos
   1. ¿Cuántas vistas de página por minuto bajo la carga máxima?

      * Valor recomendado: 200 vistas de página por minuto

   **AEM Assets**

   Desde su versión inicial, Cloud Manager ha podido ejecutar pruebas de rendimiento para programas de AEM Sites. Con esta versión, también se ha agregado la capacidad para ejecutar pruebas de rendimiento para programas de AEM Assets. La prueba de rendimiento de los recursos se realiza cargando los recursos repetidamente durante un período de prueba de 30 minutos y midiendo el tiempo de procesamiento de cada recurso, así como varias métricas a nivel del sistema.
Durante la configuración del programa, se especifican los KPI específicos de los recursos:

   * Tiempo de procesamiento del percentil 95
   * Recursos cargados por minuto

   ![](assets/Setup_Program-KPIs.png)

1. En **Aprovisionamiento**, puede ver o editar la configuración de aprovisionamiento para entornos de producción y no de producción en su programa. Verá **La escala automática está activada**, si el escalado automático se ha activado para el programa.

   >[!NOTE]
   >La función de escalado automático solo se aplica al entorno de producción y es posible que no esté disponible para todos los programas para clientes.

   ![](assets/Setup_Program-Provisioning.png)

1. Haga clic en **Guardar** para completar el asistente de configuración.

   >[!NOTE]
   >Siempre puede editar el programa una vez que el programa inicial ya esté configurado. Siga los pasos a continuación para obtener más información.

## Edición de un programa {#editing-program}

1. Vaya al programa desde la **Cloud Manager** pantalla de inicio.

1. Haga clic en **Editar programa** para actualizar o modificar el programa desde la **Información general** como se muestra en la figura siguiente.

   ![](assets/set-up-program/edit-program1.png)

1. La variable **Editar programa** pantallas que le permiten actualizar o modificar su programa.

   Puede actualizar la descripción del programa desde la **General** pestaña .

   ![](assets/set-up-program/edit-program-general.png)

   Vaya a **KPI** para actualizar información sobre AEM Sites y Assets.

   ![](assets/set-up-program/edit-program-kpi.png)

   Además, puede desplazarse a **Aprovisionamiento** para editar la configuración de aprovisionamiento para los entornos de producción y no de producción en el programa.

   ![](assets/set-up-program/edit-program-provision.png)

1. Haga clic en **Actualizar** para guardar las ediciones.

## Pasos siguientes {#the-next-steps}

Si ya ha configurado la canalización, la siguiente ejecución tendrá en cuenta la configuración actualizada. Si todavía no ha configurado la canalización, siga los pasos para configurar primero la canalización.

Consulte los documentos [Configuración de canalizaciones de producción](configuring-production-pipelines.md) y [Configuración de canalizaciones que no sean de producción](configuring-non-production-pipelines.md) para configurar la canalización.
