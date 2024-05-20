---
title: Navegación por la IU de Cloud Manager
description: Descubra cómo está organizada la IU de Cloud Manager y cómo navegar para administrar sus programas y entornos.
exl-id: 9c1545ce-1c6d-417f-a6f4-fe53caef3433
source-git-commit: 9d0f4dd29e2d05ab3f6900ee23c536b91c849e65
workflow-type: tm+mt
source-wordcount: '1292'
ht-degree: 100%

---

# Navegación por la IU de Cloud Manager {#navigation}

Descubra cómo está organizada la IU de Cloud Manager y cómo navegar para administrar sus programas y entornos.

La IU de Cloud Manager está compuesta principalmente por dos interfaces gráficas:

* [La consola Mis programas](#my-programs) donde puede ver y administrar todos los programas.
* [La ventana Información general del programa](#program-overview) donde puede ver los detalles de un programa individual y administrarlo.

## Consola Mis programas {#my-programs}

Al iniciar sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccionar la organización adecuada, se llega a la consola **Mis programas**.

![Consola Mis programas](assets/my-programs-console.png)

La consola Mis programas proporciona información general de todos los programas a los que tiene acceso en la organización seleccionada. Se compone de partes.

1. [Barras de herramientas](#toolbars-my-programs-toolbars) para la selección de organizaciones, alertas y configuración de la cuenta.
1. [Estadísticas y llamada a la acción](#statistics) para obtener una descripción general de su actividad reciente
1. [Programas y licencias](#programs-license) para conocer el estado actual de la licencia y administrar los programas
1. [Vínculos rápidos](#quick-links) para acceder fácilmente a los recursos relacionados

>[!TIP]
>
>Consulte el documento [Programas y tipos de programas](/help/getting-started/program-setup.md) para obtener más información sobre los programas.

### Barras de herramientas {#my-programs-toolbars}

Hay dos barras de herramientas una encima de la otra.

#### Encabezado de Cloud Manager {#cloud-manager-header}

El primero es el encabezado de Cloud Manager, que es persistente mientras navega por Cloud Manager. Es un anclaje que le permite acceder a la configuración y a la información que se aplican a todos los programas de Cloud Manager.

![El encabezado de Experience Cloud](assets/experience-cloud-header.png)

1. El botón Cloud Manager le devolverá a la consola Mis programas de Cloud Manager independientemente de dónde se encuentre en Cloud Manager.
1. Toque o haga clic en el botón Comentarios para proporcionar comentarios a Adobe sobre Cloud Manager.
1. El selector de organización muestra la organización en la que está conectado actualmente (en este ejemplo, Foundation Internal). Toque o haga clic para cambiar a otra organización si su Adobe ID está asociado a varias.
1. Al tocar o hacer clic en el conmutador de soluciones, puede ir rápidamente a otras soluciones de Experience Cloud.
1. El icono de ayuda proporciona acceso rápido a los recursos de aprendizaje y asistencia.
1. El icono de notificaciones se muestra con la cantidad de [notificaciones](/help/using/notifications.md) incompletas asignadas actualmente.
1. Seleccione el icono que representa a su usuario para acceder a la configuración. Si no tiene una imagen de usuario configurada, se le asigna un icono de forma aleatoria.

#### Barra de herramientas del programa {#program-toolbar}

La barra de herramientas del programa proporciona vínculos para cambiar entre los programas de Cloud Manager y las acciones apropiadas para el contexto.

![Barra de herramientas del programa](assets/program-toolbar.png)

1. El selector de programas se abre en una lista desplegable en la que puede seleccionar rápidamente otros programas o realizar acciones adecuadas al contexto, como crear un nuevo programa.
1. El vínculo de introducción le permite acceder al [recorrido de documentación de incorporación](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/onboarding/journey/overview) para ayudarle a ponerse en marcha con Cloud Manager.
   * Tenga en cuenta que el recorrido de incorporación está diseñado para AEM as a Cloud Service y no para Cloud Service de AMS, aunque muchos conceptos son los mismos.
1. El botón de acción ofrece acciones adecuadas al contexto, como crear un nuevo programa.

### Estadísticas {#statistics}

La sección de estadísticas proporciona datos acumulados para su organización. Por ejemplo, si ha configurado correctamente sus programas, pueden mostrarse estadísticas de las actividades de los últimos 90 días, como las siguientes:

* Número de [implementaciones](/help/using/code-deployment.md)
* Número de [problemas de calidad del código](/help/using/code-quality-testing.md) identificados
* Número de compilaciones

O si acaba de comenzar la configuración de su organización, puede haber sugerencias sobre los pasos siguientes o los recursos de documentación.

### Programas y licencias {#programs-license}

El contenido principal de la consola Mis programas es la lista de programas y el estado de la licencia.

#### Pestaña Programas {#programs}

La pestaña **Programas** enumera las tarjetas que representan cada programa al que tiene acceso. Toque o haga clic en una tarjeta para acceder a la página **información general del programa** para obtener más información sobre el programa.

Utilice las opciones de ordenación para encontrar el programa que necesita.

![Opciones de ordenación](assets/my-programs-sorting.png)

* Ordenar por
   * Fecha de creación (predeterminada)
   * Nombre del programa
   * Estado
* De subida (predeterminado)/De bajada
* Vista de cuadrícula (predeterminado)
* Vista de lista   

Cada programa está representado por una tarjeta (o fila en una tabla), que proporciona información general del programa y vínculos rápidos para realizar acciones.

![Tarjeta de programa](assets/program-card.png)

* Imagen del programa (si está configurada)
* Nombre del programa
* Tipo de servicio: **Experience Manager Cloud** para [programas de AEM as a Cloud Service](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/implementing/home) o **Experience Manager** para programas de AMS
* Estado
* Soluciones configuradas
* Fecha de creación

El icono de información también permite acceder rápidamente a la información adicional sobre el programa (útil en la vista de listas).

![Información](assets/information-view.png)

El icono de puntos suspensivos le permite acceder a acciones adicionales a realizar en el programa.

![Botón de puntos suspensivos para programas](assets/program-ellipsis.png)

* Navegue a un [entorno](/help/using/managing-environments.md) particular del programa
* Abra la [información general del programa](#program-overview)
* [Edite el programa](/help/getting-started/program-setup.md)
* Mostrar monitorización

#### Pestaña Licencia {#license-tab}

La pestaña **Licencia** le permite acceder rápidamente al panel de licencias.

### Vínculos rápidos {#quick-links}

La sección de vínculos rápidos le permite acceder a los recursos relacionados de uso común.

## Ventana Información del programa {#program-overview}

Una vez que seleccione un programa en la consola Mis programas, accede a la Información general del programa.

![Información general del programa](assets/program-overview.png)

La descripción general del programa le permite acceder a todos los detalles de un programa de Cloud Manager. Al igual que la consola Mis programas, está formada por varias partes.

1. [Barras de herramientas](#program-overview-toolbar) para volver rápidamente a la consola Mis programas y navegar por el programa
1. [Pestañas](#program-tabs) para cambiar entre los diferentes aspectos del programa
1. Una [llamada a la acción](#cta) basada en las últimas acciones del programa
1. Una [descripción general de los entornos](#environments) del programa
1. Una [descripción general de las canalizaciones](#pipelines) del programa
1. Vínculos a [recursos útiles](#useful-resources)

### Barras de herramientas {#program-overview-toolbar}

Las barras de herramientas para la información general del programa son muy similares a las de la [consola Mis programas.](#my-programs-toolbars) Aquí solo se ilustran las diferencias.

#### Encabezado de Cloud Manager {#cloud-manager-header-2}

El encabezado de Cloud Manager tiene un menú de hamburguesa que se abre automáticamente para mostrar las pestañas navegables de la información general del programa.

![Menú de hamburguesa de Cloud Manager](assets/cloud-manager-hamburger.png)

Toque o haga clic en el icono de menú de hamburguesa para ocultar las pestañas.

#### Barra de herramientas del programa {#program-toolbar-2}

La barra de herramientas de programas le permite cambiar rápidamente a otros programas, pero además le da acceso a acciones apropiadas para el contexto, como agregar y editar el programa.

![Barra de herramientas Programa](assets/cloud-manager-program-toolbar.png)

Además, la barra de herramientas siempre indica en qué pestaña se encuentra si ha elegido ocultar las pestañas mediante el menú de hamburguesa.

### Pestañas del programa {#program-tabs}

Cada programa tiene muchas opciones y datos asociados. Estos datos se recopilan en pestañas para facilitar la navegación por el programa. Las pestañas le permiten acceder a lo siguiente:

* Información general: la descripción general del programa tal como se describe en el documento actual
* [Actividad](/help/using/managing-pipelines.md#activity): el historial de ejecuciones de canalización del programa
* [Canalizaciones](/help/using/managing-pipelines.md#pipelines): todas las canalizaciones configuradas para el programa
* [Repositorios](/help/managing-code/repositories.md): todos los repositorios configurados para el programa
* [Informes](/help/using/monitoring-environments.md#system-monitoring-overview): métricas como datos de SLA
* [Entornos](/help/using/managing-environments.md): todos los entornos configurados para el programa
* [Conjuntos de contenido](/help/using/content-copy.md): conjuntos de contenido creados con fines de copia
* [Copiar actividad de contenido](/help/using/content-copy.md): actividades de copia de contenido
* Rutas de aprendizaje: recursos de aprendizaje adicionales sobre Cloud Manager

De forma predeterminada, al abrir un programa, llega a la pestaña **Información general**. La pestaña actual está resaltada. Seleccione otra pestaña para mostrar sus detalles.

Utilice el menú de hamburguesa de la [Encabezado de Cloud Manager](#cloud-manager-header-2) para ocultar las pestañas.

### Llamada a la acción {#cta}

La sección de llamada a la acción le proporcionará información útil según el estado del programa. Para un programa nuevo, puede ver los pasos siguientes ofrecidos, así como un recordatorio de una fecha de lanzamiento, [se configura durante la creación del programa.](/help/getting-started/program-setup.md)

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
