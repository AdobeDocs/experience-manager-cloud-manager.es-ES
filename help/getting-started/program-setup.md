---
title: Configuración del programa
description: Después de la incorporación, el propietario de la empresa tendrá que realizar alguna configuración inicial del programa.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 1%

---


# Configuración del programa {#program-setup}

Después de la incorporación, el propietario de la empresa completa la configuración inicial del programa, incluida la configuración de la descripción del programa y la definición de los indicadores clave de rendimiento (KPI), que se utilizan para las pruebas de rendimiento.

## Configuración del programa con [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

Siga estos pasos para configurar el programa y definir los KPI.

1. Inicie sesión en Cloud Manager en [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) y seleccione la organización adecuada.

1. Haga clic en **Programa de instalación** para iniciar el proceso de configuración.

   ![Configurar programa](/help/assets/set-up-program/setup1.png)

1. En el **Programa de instalación** puede introducir información del programa en tres pestañas:

   * **General**
   * **KPI**
   * **Aprovisionamiento**

1. En el **General** , añada una descripción para su programa y, opcionalmente, cargue una miniatura haciendo clic en **Cambiar foto**.

   ![Ficha General](/help/assets/Setup_Program-General.png)

1. En el **KPI** , defina los KPI. En este ejemplo, se definen KPI independientes para **AEM Sites** y **AEM Assets**. Podrá especificar los KPI para los productos con licencia.

   * Consulte la sección [KPI](#kpis) para obtener más información sobre cómo se miden los KPI en Cloud Manager.

   ![Definición de KPI](/help/assets/Setup_Program-KPIs.png)

1. En el **Aprovisionamiento** , puede definir las opciones de escalado bajo demanda para sus entornos si el escalado automático está habilitado para su programa.

   * El escalado automático solo se aplica al entorno de producción y es posible que no esté disponible para todos los programas de clientes.

   ![Opciones de aprovisionamiento](/help/assets/Setup_Program-Provisioning.png)

1. Haga clic en **Guardar** para completar el asistente de configuración.

Se creará el programa. Los recursos pueden tardar varios minutos en aprovisionarse antes de que el programa esté listo para su uso.

## Edición de un programa {#editing-program}

Los programas se pueden editar una vez configurados. Siga estos pasos para editar un programa.

1. Inicie sesión en Cloud Manager en [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) y seleccione la organización adecuada.

1. Vaya al programa desde la pantalla de inicio de Cloud Manager.

1. Haga clic en **Editar programa** para actualizar o modificar el programa desde la **Información general** página.

   ![Opción Editar programa](/help/assets/set-up-program/edit-program1.png)

1. La variable **Editar programa** , lo que le permite actualizar su programa. Consulte la sección [Configuración del programa con Cloud Manager](#program-setup-cloud-manager) para obtener más información sobre los campos disponibles.

   ![Cuadro de diálogo Editar programa](/help/assets/set-up-program/edit-program-general.png)

1. Haga clic en **Actualizar** para guardar los cambios.

Tenga en cuenta que los cambios se guardan inmediatamente en Cloud Manager, pero no se reflejarán en los entornos hasta que se ejecute la próxima canalización.

Si aún no ha creado una canalización, consulte los documentos [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) y [Configuración de canalizaciones que no sean de producción.](/help/using/non-production-pipelines.md)

## Cambio entre programas {#swithing-programs}

Al trabajar en un programa, puede cambiar rápidamente a otro sin volver a la página de información general de Cloud Manager.

Utilice la barra de acciones para cambiar a otro programa, editar el programa actual o agregar un nuevo programa.

![Conmutador de programas](/help/assets/set-up-program/setup2.png)

## KPI {#kpis}

Los KPI de sitios se miden en pruebas ejecutadas en el entorno de ensayo. Normalmente, estos KPI se reducen para adaptarse a las capacidades del entorno de ensayo.

Por ejemplo, si un usuario espera un promedio de 1000 vistas de página por minuto en su entorno de producción y tiene cuatro servidores de Dispatcher/publicación en producción, debe escalarlo a 250 vistas de página por minuto. Esto supone que su entorno de ensayo consiste únicamente en un único par de Dispatcher/servidor de publicación.

La prueba de rendimiento de los recursos se realiza cargando los recursos repetidamente durante un período de prueba de 30 minutos y midiendo el tiempo de procesamiento de cada recurso, así como varias métricas a nivel del sistema.

Puede tener una red de entrega de contenido (CDN) como Akamai o CloudFront delante del entorno de producción. Since [!UICONTROL Cloud Manager] pruebas directamente con el entorno de ensayo, el KPI debe reflejar únicamente el tráfico que se espera que pase a través de la CDN, es decir, la caché no funciona. Normalmente, este será un subconjunto relativamente pequeño del tráfico total de producción.

## Información general en vídeo {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
