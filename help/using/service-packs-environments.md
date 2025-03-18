---
title: 'Actualizaciones de Service Pack para entornos de desarrollo: usuario que lo adoptó por anticipado'
description: Descubra cómo ahora puede iniciar actualizaciones de Service Pack para entornos de desarrollo a través de la interfaz de usuario de Cloud Manager.
exl-id: 996a8eee-843f-45a6-8f7a-31ea405c2b32
source-git-commit: 91691878a2c135cc9fe123c06afcf775a962a2e0
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---

# Actualizaciones de Service Pack para entornos de desarrollo (usuario que lo adoptó por anticipado) {#stage-prod-only}

Descubra cómo puede iniciar actualizaciones de Service Pack para entornos de desarrollo a través de la interfaz de usuario de Cloud Manager.

>[!NOTE]
>
>Esta funcionalidad solo está disponible para [el programa de clientes pioneros](/help/release-notes/current.md#early-adoption).

## Información general {#service-pack-updates-overview}

Puede iniciar actualizaciones de Service Pack para entornos de desarrollo a través de la interfaz de usuario de Cloud Manager. Esta función le permite buscar actualizaciones de Service Pack disponibles y administrar el proceso de instalación de forma independiente.

**Ventajas principales**

* Proporciona un mayor control sobre las actualizaciones del Service Pack de Cloud Manager.
* Reduce la dependencia de los ingenieros de éxito del cliente (CSE) de Adobe para iniciar actualizaciones.
* Rastrea todo el proceso de actualización a través de Cloud Manager.

**Limitaciones actuales**

* La opción de actualización de autoservicio solo está disponible para entornos de desarrollo.
* Los informes de error limitados están disponibles para las actualizaciones fallidas.
* Si surgen problemas, debe ponerse en contacto con los CSE de Adobe para realizar más investigaciones.

## Iniciar una actualización del Service Pack

1. Inicie sesión en Cloud Manager con privilegios de administrador de implementación.
1. Vaya a la página Resumen del programa.
1. En la sección Entornos, haga clic en el icono ![Más, puntos suspensivos](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

   ![Buscar la actualización del Service Pack en el menú desplegable](/help/using/assets/service-pack-check-for-updates.png)

1. En el menú desplegable, haga clic en ![Abrir en icono claro](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg) **Buscar actualizaciones** para buscar actualizaciones de Service Pack disponibles.

   ![Aparece una lista de actualizaciones disponibles](/help/using/assets/service-pack-versions.png)

1. Haga clic en la versión del Service Pack que desee en la lista.
1. Haga clic en **Actualizar Service Pack** para iniciar el proceso de actualización.
1. En el cuadro de diálogo de confirmación, revise los detalles y confirme la actualización.

   Una vez confirmado, se inicia el proceso de instalación y se puede realizar un seguimiento del progreso en Cloud Manager.

## Seguimiento de la actualización del Service Pack

Después de iniciar la actualización, puede monitorizar el progreso en la Página de actividad de Cloud Manager.

**Para realizar un seguimiento de la actualización del Service Pack:**

1. Navegue hasta la página Actividad del panel de Cloud Manager.
1. Busque la entrada de instalación del paquete de servicio.

   ![Instalaciones de Service Pack](/help/using/assets/service-pack-installation.png)

1. Haga clic en la entrada para ver el progreso detallado y las actualizaciones de estado similares a los siguientes:

   ![Progreso de la instalación del Service Pack](/help/using/assets/service-pack-progression.png)

### Solucionar errores de instalación

* Si la instalación falla, Cloud Manager déclencheur automáticamente una reversión al estado anterior.
* Si los problemas persisten, haga clic en **Descargar registro** para recopilar los registros de errores y, a continuación, póngase en contacto con el Soporte técnico de Adobe para solucionar los problemas.

## Aprobar o rechazar la ejecución del Service Pack

Una vez finalizada la instalación, se requiere su aprobación (o rechazo) para finalizar la actualización.

**Para aprobar o rechazar la ejecución del Service Pack:**

1. Abra la página Actividad en Cloud Manager.
1. Busque la solicitud de aprobación pendiente para la actualización del Service Pack.

   ![Rechazar o aprobar la actualización del Service Pack](/help/using/assets/service-pack-reject-approve.png)

1. Realice una de las siguientes acciones:

   * Para finalizar la actualización, haz clic en **Aprobar**.

   ![Aprobación del Service Pack](/help/using/assets/service-pack-approve.png)

   * Para cancelar la actualización, haz clic en **Rechazar**.
Se canceló la instalación del Service Pack y no se aplican cambios.

   ![Rechazo del Service Pack](/help/using/assets/service-pack-reject.png)
