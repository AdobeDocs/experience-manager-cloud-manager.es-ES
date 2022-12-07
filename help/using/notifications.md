---
title: Notificaciones
description: Descubra cómo Cloud Manager le notifica de los eventos importantes.
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
source-git-commit: e767d9ff5e3df0047d2cf47d7b0842854101a01a
workflow-type: ht
source-wordcount: '573'
ht-degree: 100%

---


# Notificaciones {#notifications}

Descubra cómo Cloud Manager le notifica de los eventos importantes.

## Notificaciones en Cloud Manager {#cloud-manager-notifications}

[!UICONTROL Cloud Manager] le envía notificaciones cuando se inicia y finaliza una canalización de producción (correctamente o no) y al comienzo de una implementación de producción, así como cuando se llega a los pasos **Aprobación de lanzamiento** y **Programado**. Estas se envían a través del sistema de notificaciones de [!UICONTROL Experience Cloud].

>[!NOTE]
>
>Las notificaciones programadas y de aprobación solo se envían a los usuarios con las funciones **Propietario empresarial**, **Administrador de programas** y **Administrador de implementación**.

Las notificaciones aparecen en una barra lateral dentro de [!UICONTROL Cloud Manager] y en todo Adobe [!UICONTROL Experience Cloud].

El icono de campana del encabezado se señala cuando tiene nuevas notificaciones.

![Icono de notificaciones](/help/assets/notifications-bell-badged.png)

Haga clic en el icono de campana para abrir la barra lateral y ver las notificaciones. En la pestaña **Notificaciones** de la barra lateral, se muestran las notificaciones más recientes, como las confirmaciones de implementación. Las notificaciones corresponden a sus entornos.

![Barra lateral de notificaciones](/help/assets/notifications-activities.png)

La pestaña **Anuncios** incluye anuncios de producto de Adobe. Los anuncios hacen referencia al producto.

![Barra lateral de notificaciones](/help/assets/notificaitons-announcements.png)

Haga clic en una notificación o anuncio para ver sus detalles. Las notificaciones vinculadas a actividades como las implementaciones de canalización le llevan al detalle de esa actividad, como la ventana de ejecución de la canalización.

Haga clic en la opción **Ver todo** en la parte inferior del panel para ver todos los anuncios de la bandeja de entrada.

Haga clic en la opción **Marcar todo como leído** en la parte inferior del panel para marcar todas las notificaciones no leídas como leídas y borrar el distintivo del icono de la campana.

## Configuración de notificaciones {#configuration}

Puede personalizar cómo recibe las notificaciones y cuáles.

Haga clic en el icono de engranaje en la parte superior de la barra lateral de notificaciones.

![Icono de configuración de notificaciones](/help/assets/notifications-configuration.png)

Esto abre la ventana **Preferencias de Experience Cloud**, donde puede definir las suscripciones de notificación y cómo recibe las notificaciones.

### Suscripciones {#subscriptions}

Las suscripciones definen para qué productos recibe notificaciones y cuáles.

![Suscripciones de notificaciones](/help/assets/notifications-subscriptions.png)

De forma predeterminada, recibirá todas las notificaciones de todos los productos. Haga clic en **Personalizar** junto a un producto para definir los tipos de notificaciones que recibe de este.

![Personalización de la suscripción a notificaciones](/help/assets/notifications-subscriptions-customize.png)

### Prioridad {#priority}

Las alertas de prioridad se marcarán con una etiqueta **ALTA** y se pueden configurar para que se reciban exclusivamente como alertas. En la sección **Prioridad**, puede definir qué categorías se clasifican como notificaciones prioritarias.

![Prioridad de notificaciones](/help/assets/notifications-priority.png)

Utilice la lista desplegable para añadir a la lista de categorías que cumplen los requisitos de prioridad. Haga clic en la X situada junto a los nombres de las categorías para quitarlas.

### Alertas {#alerts}

Las alertas aparecen en la esquina superior derecha de la ventana durante unos segundos. Utilice la sección **Alertas** para definir para qué notificaciones recibe alertas.

![Alertas de notificación](/help/assets/notifications-alerts.png)

Puede definir el comportamiento de las alertas.

* **Mostrar alertas para**: define los tipos de notificaciones que activan alertas
* **Las alertas deben permanecer en pantalla hasta que las descarte**: controla si las alertas deben persistir a menos que las descarte activamente
* **Duración**: define cuánto tiempo debe permanecer la alerta en la pantalla si no ha elegido que permanezca en ella.

### Correo electrónico {#emails}

Las notificaciones están disponibles en la interfaz de usuario en todas las soluciones de Adobe [!UICONTROL Experience Cloud]. También puede optar por que estas notificaciones se envíen por correo electrónico en la sección **Correos electrónicos**.

![Correos electrónicos de notificación](/help/assets/notifications-emails.png)

De forma predeterminada, no se envían correos electrónicos. Puede optar por recibir correos electrónicos como los siguientes:

* Instantáneamente
* Cada día
* Cada semana

Cuando se selecciona **Notificaciones inmediatas**, los correos electrónicos se envían inmediatamente para cada notificación. Para **Resumen diario** y **Resumen semanal**, puede elegir cuándo se envía el diario y en qué día y cuándo se envía el semanal.
