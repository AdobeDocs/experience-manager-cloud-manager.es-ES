---
title: Configuración del programa
description: Después de la incorporación, el propietario de la empresa tiene que llevar a cabo alguna configuración inicial del programa.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 93%

---


# Configuración del programa {#program-setup}

Después de la incorporación, el propietario de la empresa configura el programa añadiendo una descripción y definiendo indicadores clave de rendimiento (KPI). Estos KPI se utilizan después para pruebas de rendimiento.

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

1. En la pestaña **KPI**, defina los indicadores clave de rendimiento (KPI). En este ejemplo, se definen los indicadores clave de rendimiento (KPI) independientes para **AEM Sites** y **AEM Assets**. Especifique los KPI para los productos para los que tiene licencia.

   Consulte la sección [KPI](#kpis) para obtener más información sobre cómo se miden los indicadores clave de rendimiento (KPI) en Cloud Manager.

   ![Definición de los indicadores clave de rendimiento (KPI)](/help/assets/Setup_Program-KPIs.png)

1. En la ficha **Aprovisionamiento**, puede definir las opciones de escalado Bajo demanda para sus entornos si el escalado automático está habilitado para su programa.

   El escalado automático solo se aplica al entorno de producción y es posible que no esté disponible para todos los programas de clientes.

   ![Opciones de aprovisionamiento](/help/assets/Setup_Program-Provisioning.png)

1. Haga clic en **Guardar**.

Se crea el programa. Los recursos pueden tardar varios minutos en aprovisionarse antes de que el programa esté listo para su uso.

## Editar un programa {#editing-program}

Los programas se pueden editar una vez configurados. Siga estos pasos para editar un programa.

1. Inicie sesión en Cloud Manager en [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) y seleccione la organización adecuada.

1. Vaya al programa desde la pantalla de inicio de Cloud Manager.

1. Haga clic en **Editar programa** para actualizar o modificar el programa desde la página **Información general**.

   ![Opción Editar programa](/help/assets/set-up-program/edit-program1.png)

1. Se muestra el cuadro de diálogo **Editar programa**, que le permite actualizar su programa. Consulte la sección [Configuración del programa con Cloud Manager](#program-setup-cloud-manager) para obtener más información sobre los campos disponibles.

   ![Cuadro de diálogo Editar programa](/help/assets/set-up-program/edit-program-general.png)

1. Haga clic en **Actualizar** para guardar los cambios.

Los cambios se guardan inmediatamente en Cloud Manager, pero no se reflejan en los entornos hasta que se ejecute la próxima canalización.

Si aún no ha creado una canalización, consulte [Configuración de canalizaciones de producción](/help/using/production-pipelines.md) y [Configuración de canalizaciones que no son de producción](/help/using/non-production-pipelines.md).

## Cambio entre programas {#swithing-programs}

Al trabajar en un programa, puede cambiar rápidamente a otro sin volver a la página de información general de Cloud Manager.

Utilice la barra de acciones para cambiar a otro programa, editar el actual o agregar uno nuevo.

![Conmutador de programas](/help/assets/set-up-program/setup2.png)

## Indicadores clave de rendimiento (KPI) {#kpis}

Los indicadores clave de rendimiento (KPI) de sitios se miden en pruebas ejecutadas en el entorno de ensayo. Normalmente, estos KPI se reducen para adaptarse a las capacidades del entorno de ensayo.

Por ejemplo, si un usuario espera un promedio de 1000 vistas de página por minuto en su entorno de producción y tiene cuatro servidores de Dispatcher/Publicación en producción, debe escalarlo a 250 vistas de página por minuto. En este escenario se da por hecho que el entorno de ensayo consiste únicamente en un único par de servidor de Dispatcher/publicación.

Las pruebas de rendimiento de Assets implican la carga repetida de recursos durante un periodo de 30 minutos. El tiempo de procesamiento de cada recurso y diversas métricas de nivel de sistema se miden a lo largo de la prueba.

Puede tener una red de distribución de contenido (CDN) como Akamai o CloudFront delante del entorno de producción. Dado que [!UICONTROL Cloud Manager] prueba directamente en el entorno de ensayo, los KPI deben reflejar únicamente el tráfico que se espera que pase a través de la red de distribución de contenido (CDN). Es decir, la caché falla. Esta experiencia suele ser un subconjunto relativamente pequeño del tráfico total de producción.

## Información general en vídeo {#video}

>[!VIDEO](https://video.tv.adobe.com/v/34622?captions=spa)
