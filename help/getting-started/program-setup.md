---
title: Configuración del programa
description: Después de la incorporación, el propietario de la empresa tendrá que llevar a cabo alguna configuración inicial del programa.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 91%

---


# Configuración del programa {#program-setup}

Después de la incorporación, el propietario de la empresa completa la configuración inicial del programa, incluida la descripción del programa y la definición de los indicadores clave de rendimiento (KPI), que se utilizan para las pruebas de rendimiento.

## Configuración del programa con [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

Siga estos pasos para configurar el programa y definir los indicadores clave de rendimiento (KPI).

1. Inicie sesión en Cloud Manager en [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) y seleccione la organización adecuada.

1. Haga clic en **Configurar programa** para iniciar el proceso de configuración.

   ![Configuración del programa](/help/assets/set-up-program/setup1.png)

1. En el cuadro de diálogo **Configurar programa**, puede introducir información del programa en tres pestañas:

   * **General**
   * **KPI**
   * **Aprovisionamiento**

1. En la pestaña **General**, agregue una descripción para su programa y, opcionalmente, cargue una miniatura haciendo clic en **Cambiar foto**.

   ![Pestaña General](/help/assets/Setup_Program-General.png)

1. En la pestaña **KPI**, defina los indicadores clave de rendimiento (KPI). En este ejemplo, se definen los indicadores clave de rendimiento (KPI) independientes para **AEM Sites** y **AEM Assets**. Podrá especificar los indicadores clave de rendimiento (KPI) para los productos con licencia.

   * Consulte la sección [KPI](#kpis) para obtener más información sobre cómo se miden los indicadores clave de rendimiento (KPI) en Cloud Manager.

   ![Definición de los indicadores clave de rendimiento (KPI)](/help/assets/Setup_Program-KPIs.png)

1. En la pestaña **Aprovisionamiento**, puede definir las opciones de escalado bajo demanda para sus entornos si el escalado automático está habilitado para su programa.

   * El escalado automático solo se aplica al entorno de producción y es posible que no esté disponible para todos los programas de clientes.

   ![Opciones de aprovisionamiento](/help/assets/Setup_Program-Provisioning.png)

1. Haga clic en **Guardar** para completar el asistente de configuración.

Se creará el programa. Los recursos pueden tardar varios minutos en aprovisionarse antes de que el programa esté listo para su uso.

## Edición de un programa {#editing-program}

Los programas se pueden editar una vez configurados. Siga estos pasos para editar un programa.

1. Inicie sesión en Cloud Manager en [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) y seleccione la organización adecuada.

1. Vaya al programa desde la pantalla de inicio de Cloud Manager.

1. Haga clic en **Editar programa** para actualizar o modificar el programa desde la página **Información general**.

   ![Opción Editar programa](/help/assets/set-up-program/edit-program1.png)

1. Se muestra el cuadro de diálogo **Editar programa**, que le permite actualizar su programa. Consulte la sección [Configuración del programa con Cloud Manager](#program-setup-cloud-manager) para obtener más información sobre los campos disponibles.

   ![Cuadro de diálogo Editar programa](/help/assets/set-up-program/edit-program-general.png)

1. Haga clic en **Actualizar** para guardar los cambios.

Tenga en cuenta que los cambios se guardan inmediatamente en Cloud Manager, pero no se reflejarán en los entornos hasta que se ejecute la próxima canalización.

Si todavía no ha creado una canalización, consulte los documentos [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) y [Configuración de canalizaciones que no son de producción](/help/using/non-production-pipelines.md).

## Cambio entre programas {#swithing-programs}

Al trabajar en un programa, puede cambiar rápidamente a otro sin volver a la página de información general de Cloud Manager.

Utilice la barra de acciones para cambiar a otro programa, editar el actual o agregar uno nuevo.

![Conmutador de programas](/help/assets/set-up-program/setup2.png)

## Indicadores clave de rendimiento (KPI) {#kpis}

Los indicadores clave de rendimiento (KPI) de sitios se miden en pruebas ejecutadas en el entorno de ensayo. Normalmente, estos KPI se reducen para adaptarse a las capacidades del entorno de ensayo.

Por ejemplo, si un usuario espera un promedio de 1000 vistas de página por minuto en su entorno de producción y tiene cuatro servidores de Dispatcher/Publicación en producción, debe escalarlo a 250 vistas de página por minuto. Esto supone que su entorno de ensayo consiste únicamente en un único par de servidor de Dispatcher/Publicación.

Las pruebas de rendimiento de Assets se realizan cargando recursos repetidamente durante un período de 30 minutos y midiendo el tiempo de procesamiento de cada recurso y de varias métricas de nivel del sistema.

Puede tener una red de distribución de contenido (CDN) como Akamai o CloudFront delante del entorno de producción. Como [!UICONTROL Cloud Manager] prueba directamente en el entorno de ensayo, los KPI deben reflejar únicamente el tráfico que se espera que pase a través de la red de distribución de contenido (CDN), es decir, los fallos de la caché. Esto suele ser un subconjunto relativamente pequeño del tráfico total de producción.

## Información general en vídeo {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
