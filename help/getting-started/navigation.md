---
title: Navegación por la IU de Cloud Manager
description: Descubra cómo está organizada la IU de Cloud Manager y cómo navegar para administrar sus programas y entornos.
exl-id: 9c1545ce-1c6d-417f-a6f4-fe53caef3433
source-git-commit: cc41d4716aa3c3683010b6dd392b5355b129d1ef
workflow-type: tm+mt
source-wordcount: '1530'
ht-degree: 52%

---


# Navegar por la IU de Cloud Manager {#navigation}

Descubra cómo está organizada la IU de Cloud Manager y cómo navegar para administrar sus programas y entornos.

La IU de Cloud Manager está compuesta principalmente por dos interfaces gráficas:

* [La consola Mis programas](#my-programs-console) es donde puede ver y administrar todos los programas.
* [La ventana Información general del programa](#program-overview) es donde puede ver los detalles de un programa individual y administrarlo.

## Consola Mis programas {#my-programs-console}

Al iniciar sesión en Cloud Manager en [experience.adobe.com](https://experience.adobe.com/experiencemanager) y seleccionar la organización adecuada, llegará a la consola **Mis programas**.

![Consola Mis programas](/help/getting-started/assets/cloud-manager-my-programs-console.png)

La consola **Mis programas** proporciona una descripción general de todos los programas a los que tiene acceso en la organización seleccionada. Se compone de partes.

|   | Área | Descripción |
| --- | --- | --- |
| 1 | [Barras de herramientas](#toolbars-my-programs-toolbars) | Se utiliza para la selección de organizaciones, alertas y configuración de cuentas. |
| 2 | Pestaña del panel lateral izquierdo | Varias fichas que le permiten alternar la vista actual de sus programas, incluidas las siguientes:<br><ul><li>**Experience Manager** abre la página principal de las distintas soluciones de AEM</li><li>**Todos los programas** que muestra todos los programas disponibles.</li><li>**Licencia** abre el tablero de licencias. El Tablero de licencias solo se aplica a *programas de AEM as a Cloud Service* (AEMaaCS), no a programas de Adobe Managed Services como AEM 6.5 y AEM 6.5 LTS. Para determinar el tipo de servicio que tiene su programa (AEMaaCS o AMS), consulte la [sección Tarjetas de programa](#program-cards) de este artículo. Las pestañas se cierran de forma predeterminada y se pueden mostrar con el menú desplegable ![Mostrar icono de menú, hamburguesa](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), ubicado a la izquierda del [encabezado de Cloud Manager](#cloud-manager-header).</li></ol> |
| 3 | [Mis programas](#my-programs-section) | Enumera todos los programas disponibles que puede seleccionar.<br>Consulte [Programas y tipos de programas](/help/getting-started/program-setup.md) para obtener detalles sobre los programas. |
| 4 | [Estadísticas y llamadas a la acción](#cta-statistics) | Proporciona una descripción general de la actividad reciente. |
| 5 | [Vínculos rápidos](#quick-links) | Acceso rápido a recursos relacionados. |


### Barras de herramientas {#my-programs-toolbars}

Hay dos barras de herramientas una encima de la otra.

#### Encabezado de Cloud Manager {#cloud-manager-header}

El primero es el encabezado de Cloud Manager. El encabezado se mantiene a medida que navega por Cloud Manager. Es un anclaje que le permite acceder a la configuración y a la información que se aplican a todos los programas de Cloud Manager.

![El encabezado de Experience Cloud](/help/getting-started/assets/cloud-manager-header-toolbar.png)

| Área | Descripción |
| --- | --- |
| ![Mostrar icono de menú, hamburguesa](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) | Menú desplegable que proporciona acceso a las fichas de partes específicas de un programa individual.<br>Para determinar el tipo de servicio que tiene su programa (AMS o AEMaaCS), consulte la [sección Tarjetas de programa](#program-cards) de este documento. |
| ![Icono rojo y blanco de Adobe](/help/getting-started/assets/AdobeLogoWhiteOnRed.svg) Cloud Manager | Haga clic para abrir la consola **Mis programas** de Cloud Manager, independientemente de su ubicación en Cloud Manager. |
| *`Name of selected organization`* | El selector de organización muestra la organización en la que está conectado actualmente (en este ejemplo, *Foundation Internal*). Haga clic aquí para cambiar a otra organización si Adobe ID está asociado a varias organizaciones. |
| ![Icono de comentarios](/help/getting-started/assets/AppComment.svg) Comentarios | Haga clic en para proporcionar comentarios a Adobe sobre Cloud Manager. |
| ![icono del Asistente de IA](/help/getting-started/assets/AIChat.svg) | El asistente de IA ofrece una interfaz conversacional diseñada para agilizar la búsqueda de respuestas a sus consultas relacionadas con AEM. Ver [Asistente de IA](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/ai-assistant/ai-assistant-in-aem) |
| ![Icono de ayuda](https://spectrum.adobe.com/static/icons/workflow_18/Smock_HelpOutline_18_N.svg) | Haga clic en para proporcionar acceso rápido a los recursos de aprendizaje y asistencia. |
| ![Icono de campana blanca](/help/getting-started/assets/Bell.svg) | Haga clic para ver el número de [notificaciones](/help/using/notifications.md) incompletas asignadas actualmente |
| ![Icono de aplicaciones](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) | Haga clic en para desplazarse rápidamente entre la página de inicio de AEM y las soluciones de AEM |
| *`Dynamic Account icon`* | Haz clic en tu imagen de usuario para acceder a **Configuración de la cuenta** y **Configuración del programa**, o para cerrar la sesión.<br>Si elige no agregar una imagen de usuario, se asigna aleatoriamente un icono (como se ve en la imagen de la barra de herramientas anterior). |

<!--
1. The ![Show menu icon, hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) icon on the left side of the header is  
   * The License Dashboard only applies to AEM as a Cloud Service programs, not AMS programs.
   * To determine the type of service your program has (AMS or AEMaaCS), see the [Program Cards section](#program-cards) of this document.
1. The **Adobe Cloud Manager** button takes you back to the **My Programs** console of Cloud Manager no matter where you are in Cloud Manager.
1. Click **Feedback** to provide feedback to Adobe about Cloud Manager.
1. The organization selector displays the organization that you are currently signed into (in this example, Foundation Internal). Click to switch to another organization if your Adobe ID is associated with multiple.
1. Clicking the solutions switcher lets you quickly jump to other Experience Cloud solutions.
1. The Help icon provides quick access to learning and support resources.
1. The notifications icon is badged with the number of currently assigned incomplete [notifications](/help/using/notifications.md)
1. Select the icon representing your user to access your user settings. If you do not select a user picture, an icon is randomly assigned. -->

#### Barra de herramientas del programa {#program-toolbar}

La barra de herramientas del programa proporciona vínculos para cambiar entre los programas de Cloud Manager y las acciones apropiadas para el contexto.

![barra de herramientas del programa Cloud Manager](/help/getting-started/assets/cloud-manager-programs-toolbar.png)

|   | Área | Descripción |
| --- | --- | --- |
| 1 | Mis programas | Haga clic para abrir una lista desplegable en la que puede elegir agregar un programa, seleccionar otros programas existentes o volver a la página principal de Experience Manager. |
| 2 | ![Icono de información](/help/getting-started/assets/Info.svg) Introducción | Haga clic para acceder al [recorrido de la documentación de incorporación](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/onboarding/journey/overview) y ponerlo en marcha con Cloud Manager.<br>El recorrido de incorporación está diseñado para Cloud Manager en Adobe Experience Manager as a Cloud Service (AEMaaCS) y no para Cloud Manager en Adobe Managed Services (AMS). Sin embargo, muchos conceptos son los mismos. |
| 3 | *`Dynamic action button`* | El botón de acción ofrece acciones apropiadas al contexto en las que puede hacer clic, como **Agregar programa** (visto en el ejemplo anterior) o agregar un dominio. |

### Llamadas a la acción y estadísticas {#cta-statistics}

La sección de llamadas a la acción y estadísticas proporciona datos acumulados para su organización. Por ejemplo, si ha configurado correctamente sus programas, pueden mostrarse las estadísticas de sus actividades de los últimos 90 días, entre ellas:

* Número de [implementaciones](/help/using/code-deployment.md)
* Número de [problemas de calidad del código](/help/using/code-quality-testing.md) identificados
* Número de compilaciones

O si acaba de comenzar la configuración de su organización, puede haber sugerencias sobre los pasos siguientes o los recursos de documentación.

### Mis programas {#my-programs-section}

El contenido principal de la consola Mis programas es la sección **Mis programas** que enumera sus programas como tarjetas individuales. Toque o haga clic en una tarjeta para acceder a la página **información general del programa** para obtener más información sobre el programa.

Según sus privilegios, es posible que no pueda seleccionar determinados programas.

Puede utilizar las siguientes opciones de ordenación para encontrar rápidamente el programa que desea:

![Opciones de ordenación](/help/getting-started/assets/cloud-manager-my-programs-sorting.png)

* Ordenar por:
   * Fecha de creación
   * Nombre del programa
   * Estado
* ![Icono de orden descendente](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderDown_18_N.svg) / ![Icono de orden ascendente](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderUp_18_N.svg) Ordene los programas descendente o ascendente, respectivamente.
* ![Icono de vista de cuadrícula clásica](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ClassicGridView_18_N.svg) / ![Icono o lista con viñetas de texto](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TextBulleted_18_N.svg) Ver programas en forma de cuadrícula o lista, respectivamente.

#### Tarjetas de programa {#program-cards}

Cada programa está representado por una tarjeta o fila en una tabla, que proporciona información general del programa y vínculos rápidos para realizar acciones.

![Tarjeta de programa](/help/getting-started/assets/cloud-manager-program-card.png)

* Imagen del programa (si está configurada)
* Nombre del programa (en el ejemplo anterior, *WKND Magazine*)
* Tipo de servicio:
   * **Experience Manager** para programas de AMS
   * **Experience Manager Cloud** para [programas de AEM as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/implementing/home)
* Estado (en el ejemplo anterior, *Listo*)
* Soluciones configuradas
* Fecha de creación

Haz clic en ![Icono de información](/help/getting-started/assets/Info.svg) para obtener acceso rápido a información adicional sobre el programa (útil en la vista de lista).

![Ventana emergente de información en Cloud Manager AMS](/help/getting-started/assets/cloud-manager-information-view.png)

Haga clic en el icono ![Más, los puntos suspensivos](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) le proporcionan acceso a acciones adicionales que puede realizar en el programa.

![Botón de puntos suspensivos para programas](/help/getting-started/assets/cloud-manager-program-ellipsis.png)

* Inicio de Experience Manager
* Navegue a un [entorno](/help/using/managing-environments.md) particular del programa
* Abra la [información general del programa](#program-overview)
* [Edite el programa](/help/getting-started/program-setup.md)
* Mostrar monitorización

### Vínculos rápidos {#quick-links}

La sección de vínculos rápidos le permite acceder a útiles recursos relacionados.

## Ventana Información del programa {#program-overview}

Si selecciona un programa en la consola [**Mis programas**](#my-programs-console), accederá a la página **Información general del programa**.

![Información general del programa](/help/getting-started/assets/cloud-manager-program-overview.png)

**Información general del programa** le proporciona acceso a todos los detalles de un programa de Cloud Manager. Al igual que **Mis programas**, consta de varias partes.

1. [Barras de herramientas](#program-overview-toolbar) para volver rápidamente a la consola **Mis programas** y navegar por el programa.
1. [Área de fichas](#program-tabs) para cambiar entre diferentes aspectos del programa.
1. Una [llamada a la acción](#cta) basada en las últimas acciones del programa.
1. [Entornos](#environments) asociados del programa.
1. [Canalizaciones](#pipelines) asociadas del programa.

### Barras de herramientas {#program-overview-toolbar}

Las barras de herramientas para la información general del programa son muy similares a las de la [consola Mis programas](#my-programs-toolbars). Aquí solo se ilustran las diferencias.

#### Encabezado de Cloud Manager {#cloud-manager-header-2}

El encabezado de Cloud Manager tiene un menú desplegable ![Mostrar icono de menú, hamburguesa](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) que se abre automáticamente para mostrar las pestañas navegables de la Información general del programa.

Haga clic en ![Mostrar icono de menú, hamburguesa](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para ocultar las fichas.

#### Barra de herramientas del programa {#program-toolbar-2}

La barra de herramientas de programas le permite cambiar rápidamente a otros programas, pero además le da acceso a acciones apropiadas para el contexto, como agregar y editar el programa.

![Barra de herramientas del programa](assets/cloud-manager-program-toolbar.png)

Además, si oculta las pestañas usando ![Mostrar icono de menú, hamburguesa](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), la barra de herramientas puede mostrar la pestaña en la que se encuentra actualmente.

### Pestañas del programa {#program-tabs}

Cada programa tiene muchas opciones y datos asociados. Estos datos se recopilan en pestañas para facilitar la navegación por el programa. Las pestañas le permiten acceder a lo siguiente:

* Información general: la descripción general del programa tal como se describe en el documento actual
* [Actividad](/help/using/managing-pipelines.md#activity): el historial de ejecuciones de canalización del programa
* [Canalizaciones](/help/using/managing-pipelines.md#pipelines): todas las canalizaciones configuradas para el programa
* [Repositorios](/help/managing-code/managing-repositories.md): todos los repositorios configurados para el programa
* [Informes](/help/using/monitoring-environments.md#system-monitoring-overview): métricas como datos de SLA
* [Entornos](/help/using/managing-environments.md): todos los entornos configurados para el programa
* [Conjuntos de contenido](/help/using/content-copy.md): conjuntos de contenido creados con fines de copia
* [Copiar actividad de contenido](/help/using/content-copy.md): actividades de copia de contenido
* Rutas de aprendizaje: recursos de aprendizaje adicionales sobre Cloud Manager

De forma predeterminada, al abrir un programa, llega a la pestaña **Información general**. La pestaña actual está resaltada. Seleccione otra pestaña para mostrar sus detalles.

Use ![Mostrar icono de menú, hamburguesa](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) en el [encabezado de Cloud Manager](#cloud-manager-header-2) para ocultar las pestañas.

### Llamada a la acción {#cta}

La sección de llamada a la acción le proporciona información útil según el estado del programa. Para un programa nuevo, puede ver los pasos siguientes ofrecidos, así como un recordatorio de una fecha de lanzamiento, [se configura durante la creación del programa](/help/getting-started/program-setup.md).

Para un programa activo, el estado de la última implementación con vínculos para obtener más información e iniciar una nueva implementación.

![Llamada a la acción](assets/info-banner.png)

### Tarjeta Entornos {#environments}

La tarjeta **Entornos** le ofrece una descripción general de sus entornos, así como vínculos para acciones rápidas.

La tarjeta **Entornos** solo enumera tres entornos. Haga clic en **Mostrar todo** para ver todos los entornos del programa.

Consulte el documento [Administración de entornos](/help/using/managing-environments.md) para obtener más información sobre cómo administrar los entornos.

### Tarjeta de canalizaciones {#pipelines}

La tarjeta de **Canalizaciones** le ofrece una descripción general de sus canalizaciones, así como vínculos para acciones rápidas.

La tarjeta **Canalizaciones** solo enumera tres canalizaciones. Haga clic en **Mostrar todo** para ver todas las canalizaciones del programa.

Consulte el documento [Administración de canalizaciones](/help/using/managing-pipelines.md) para obtener más información sobre cómo administrar las canalizaciones.

### Recursos útiles {#useful-resources}

La sección **Recursos útiles** proporciona vínculos a recursos de aprendizaje adicionales para Cloud Manager.
