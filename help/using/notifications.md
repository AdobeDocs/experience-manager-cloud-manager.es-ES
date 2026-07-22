---
title: Notificaciones
description: Descubra cómo Cloud Manager le notifica de los eventos importantes.
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
TQID: https://experienceleague.adobe.com/WBAHeIAH1XL6oVy342wLaUAoAHkUoN1AbcAl2Erkte4
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 65b260abe417925f26d647fb9857d32c30455f9b
workflow-type: tm+mt
source-wordcount: 562
ht-degree: 52%

---

# Notificaciones {#notifications}

Descubra cómo Cloud Manager le notifica de los eventos importantes.

## Notificaciones en Cloud Manager {#cloud-manager-notifications}

Las notificaciones se envían cuando se inicia y finaliza una canalización de producción (correctamente o no) durante una implementación de producción. Y, cuando se alcancen los pasos **Aprobación de lanzamiento** y **Programado**. Estas se envían a través del sistema de notificaciones de [!UICONTROL Experience Cloud].

>[!NOTE]
>
>Las notificaciones programadas y de aprobación solo se envían a los usuarios con las funciones **Propietario empresarial**, **Administrador de programas** y **Administrador de implementación**.

Las notificaciones aparecen en una barra lateral dentro de [!UICONTROL Cloud Manager] y en todo Adobe [!UICONTROL Experience Cloud].

El icono de campana del encabezado muestra un indicador cuando tiene nuevas notificaciones.

![Icono de notificaciones](/help/assets/notifications-bell-badged.png)

Haga clic en el icono de campana para abrir la barra lateral y ver las notificaciones. La pestaña **Notificaciones** en la barra lateral muestran las notificaciones más recientes, como las confirmaciones de implementación. Las notificaciones corresponden a sus entornos.

![Barra lateral de notificaciones](/help/assets/notifications-activities.png)

La pestaña **Anuncios** incluye anuncios de productos de Adobe. Los anuncios proporcionan información sobre el producto.

![Barra lateral de notificaciones](/help/assets/notificaitons-announcements.png)

Haga clic en una notificación o un anuncio para ver los detalles. Las notificaciones vinculadas a actividades como las implementaciones de canalización le dirigen a los detalles de esa actividad, como la ventana de ejecución de la canalización.

Haga clic en la opción **Ver todos** en la parte inferior del panel para ver todos los anuncios de la bandeja de entrada.

Haga clic en la opción **Marcar todo como leído** en la parte inferior del panel para marcar todas las notificaciones no leídas como leídas y quitar el distintivo del icono de la campana.

## Configuración de notificaciones {#configuration}

Puede personalizar cómo recibe las notificaciones y cuáles.

Haga clic en el icono de engranaje en la parte superior de la barra lateral de notificaciones.

![Icono de configuración de notificaciones](/help/assets/notifications-configuration.png)

Se abre la ventana de **preferencias de Experience Cloud**, donde puede definir las suscripciones de notificación y cómo recibe las notificaciones.

### Suscripciones {#subscriptions}

Las suscripciones definen para qué productos recibe notificaciones y qué notificaciones recibe.

![Suscripciones de notificaciones](/help/assets/notifications-subscriptions.png)

De forma predeterminada, recibirá todas las notificaciones de todos los productos. Para definir los tipos de notificaciones que recibes sobre un producto, haz clic en **Personalizar** junto a él.

![Personalización de la suscripción a notificaciones](/help/assets/notifications-subscriptions-customize.png)

### Prioridad {#priority}

Las alertas de prioridad están marcadas con la etiqueta **HIGH**. Puede configurarlos para que se envíen exclusivamente como notificaciones. En la sección **Prioridad**, puede definir qué categorías se clasifican como notificaciones prioritarias.

![Prioridad de notificaciones](/help/assets/notifications-priority.png)

Utilice la lista desplegable para añadir a la lista de categorías que cumplen los requisitos de prioridad. Haga clic en el icono Eliminar situado junto a los nombres de las categorías para eliminarlas.

### Alertas {#alerts}

Las alertas aparecen en la esquina superior derecha de la ventana durante unos segundos. Utilice la sección **Alertas** para definir para qué notificaciones recibe alertas.

![Alertas de notificación](/help/assets/notifications-alerts.png)

Puede definir el comportamiento de las alertas.

* **Mostrar alertas para**: define los tipos de notificaciones que almacenan en déclencheur las alertas.
* **Las alertas permanecen en pantalla hasta que las descarta**: controla si las alertas persisten a menos que las descarte activamente.
* **Duración**: define cuánto tiempo permanece la alerta en la pantalla si no ha elegido que permanezca en ella.

### Correo electrónico {#emails}

Las notificaciones están disponibles en la interfaz de usuario web en todas las soluciones de Adobe [!UICONTROL Experience Cloud]. Para recibir estas notificaciones por correo electrónico, ingrese dentro de la sección **Correos electrónicos**.

![Correos electrónicos de notificación](/help/assets/notifications-emails.png)

De forma predeterminada, no se envían correos electrónicos. Puede optar por recibir correos electrónicos como los siguientes:

* Instantáneamente
* Cada día
* Cada semana

Cuando se selecciona **Notificaciones inmediatas**, los correos electrónicos se envían inmediatamente para cada notificación. Para **Resumen diario** y **Resumen semanal**, puede elegir cuándo se envía el resumen diario y en qué día y cuándo se envía el resumen semanal.
