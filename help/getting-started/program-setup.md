---
title: Configuración del programa
description: Después de la incorporación, el propietario de la empresa tiene que llevar a cabo alguna configuración inicial del programa.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
TQID: https://experienceleague.adobe.com/AqaA4GSOptV11h2y4V1Mt15KmEhEYBaiM-RvBFjtfWY
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: fa6be369b979682cebf68852603725d8754605ab
workflow-type: tm+mt
source-wordcount: 549
ht-degree: 65%

---

# Configuración del programa {#program-setup}

Después de la incorporación, el cliente potencial empresarial configura el programa agregando una descripción y definiendo indicadores clave de rendimiento (KPI). Estos KPI se utilizan después para pruebas de rendimiento.

## Configuración del programa con [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

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

   El escalado automático solo se aplica al entorno de producción y no está disponible para algunos programas de clientes.

   ![Opciones de aprovisionamiento](/help/assets/Setup_Program-Provisioning.png)

1. Haga clic en **Guardar**.

Se crea el programa. Los recursos tardan varios minutos en aprovisionarse antes de que el programa esté listo para su uso.

## Editar un programa {#editing-program}

Los programas se pueden editar una vez configurados.

**Para editar un programa:**

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

Los indicadores clave de rendimiento (KPI) de sitios se miden en pruebas ejecutadas en el entorno de ensayo. Normalmente, estos KPI se ajustan para que coincidan con las capacidades del entorno de ensayo.

Por ejemplo, un usuario que espera un promedio de 1000 vistas de página por minuto en su entorno de producción y que tiene cuatro servidores de Dispatcher/publicación en producción, reduce este escenario a 250 vistas de página por minuto. En este escenario se da por hecho que el entorno de ensayo consiste únicamente en un único par de servidor de Dispatcher/publicación.

Las pruebas de rendimiento de Assets implican la carga repetida de recursos durante un periodo de 30 minutos. El tiempo de procesamiento de cada recurso y diversas métricas de nivel de sistema se miden a lo largo de la prueba.

Tiene una red de entrega de contenido (CDN) como Akamai o CloudFront configurada para su entorno de producción. Como [!UICONTROL Cloud Manager] prueba directamente en el entorno de ensayo, el KPI refleja únicamente el tráfico que se espera que pase a través de la red de distribución de contenido (CDN). Es decir, la caché falla. Normalmente, este tráfico es un subconjunto relativamente pequeño del tráfico total de producción.

## Información general en vídeo {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
