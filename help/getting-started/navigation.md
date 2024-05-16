---
title: Navegación por la IU de Cloud Manager
description: Descubra cómo está organizada la interfaz de usuario de Cloud Manager y cómo navegar para administrar sus programas y entornos.
exl-id: 9c1545ce-1c6d-417f-a6f4-fe53caef3433
source-git-commit: 9d0f4dd29e2d05ab3f6900ee23c536b91c849e65
workflow-type: tm+mt
source-wordcount: '1292'
ht-degree: 5%

---

# Navegación por la IU de Cloud Manager {#navigation}

Descubra cómo está organizada la interfaz de usuario de Cloud Manager y cómo navegar para administrar sus programas y entornos.

La interfaz de usuario de Cloud Manager está compuesta principalmente por dos interfaces gráficas:

* [La consola Mis programas](#my-programs) donde puede ver y administrar todos los programas.
* [La ventana Resumen del programa](#program-overview) donde puede ver los detalles de y administrar un programa individual.

## Consola Mis programas {#my-programs}

Al iniciar sesión en Cloud Manager en, a las [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización adecuada, llegará a la **Mis programas** consola.

![Consola Mis programas](assets/my-programs-console.png)

La consola Mis programas proporciona una descripción general de todos los programas a los que tiene acceso en la organización seleccionada. Se compone de varias partes.

1. [Barras de herramientas](#toolbars-my-programs-toolbars) para la selección de organizaciones, alertas y configuración de cuentas
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
1. Toque o haga clic en el botón Comentarios para proporcionar comentarios al Adobe sobre Cloud Manager.
1. El selector de organización muestra la organización en la que está conectado actualmente (en este ejemplo, Foundation Internal). Toque o haga clic para cambiar a otra organización si su Adobe ID está asociado a varias.
1. Al tocar o hacer clic en el conmutador de soluciones, puede ir rápidamente a otras soluciones de Experience Cloud.
1. El icono de ayuda proporciona acceso rápido a los recursos de aprendizaje y asistencia.
1. El icono de notificaciones está marcado con el número de asignaciones incompletas actualmente [notificaciones.](/help/using/notifications.md)
1. Seleccione el icono que representa al usuario para acceder a su configuración de usuario. Si no tiene una imagen de usuario configurada, se le asigna un icono de forma aleatoria.

#### Barra de programas {#program-toolbar}

La barra de herramientas del programa proporciona vínculos para cambiar entre los programas de Cloud Manager y las acciones apropiadas para el contexto.

![Barra de herramientas Programa](assets/program-toolbar.png)

1. El selector de programas se abre en una lista desplegable en la que puede seleccionar rápidamente otros programas o realizar acciones adecuadas al contexto, como crear un nuevo programa
1. El vínculo de introducción le permite acceder a [recorrido de documentación de incorporación](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/overview) para ayudarle a ponerse en marcha con Cloud Manager.
   * Tenga en cuenta que el recorrido AEM de incorporación está diseñado para los as a Cloud Service y no para los Cloud Service de AMS, pero muchos conceptos son los mismos.
1. El botón de acción ofrece acciones adecuadas al contexto, como crear un nuevo programa.

### Estadísticas {#statistics}

La sección de estadísticas proporciona datos acumulados para su organización. Por ejemplo, si ha configurado correctamente sus programas, pueden mostrarse estadísticas de las actividades de los últimos 90 días, como las siguientes:

* Número de [implementaciones](/help/using/code-deployment.md)
* Número de [problemas de calidad del código](/help/using/code-quality-testing.md) identificado
* Número de compilaciones

O si acaba de comenzar la configuración de su organización, puede haber sugerencias sobre los pasos siguientes o los recursos de documentación.

### Programas y licencias {#programs-license}

El contenido principal de la consola Mis programas es la lista de programas y el estado de la licencia.

#### Pestaña Programas {#programs}

El **Programas** La pestaña enumera las tarjetas que representan cada programa al que tiene acceso. Toque o haga clic en una tarjeta para acceder a **Resumen del programa** del programa para obtener más información sobre el programa.

Utilice las opciones de clasificación para encontrar mejor el programa que necesita.

![Opciones de ordenación](assets/my-programs-sorting.png)

* Ordenar por
   * Fecha de creación (predeterminada)
   * Nombre del programa
   * Estado
* Ascendente (predeterminado) / Descendente
* Vista de cuadrícula (predeterminada)
* Vista de lista   

Cada programa está representado por una tarjeta (o fila en una tabla), que proporciona una descripción general del programa y vínculos rápidos para realizar acciones.

![Tarjeta de programa](assets/program-card.png)

* Imagen del programa (si está configurado)
* Nombre del programa
* Tipo de servicio: **Experience Manager Cloud** para [AEM programas as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/home) o **Experience Manager** para programas de AMS
* Estado
* Soluciones configuradas
* Fecha de creación

El icono de información también permite acceder rápidamente a información adicional sobre el programa (útil en la vista de listas).

![Información](assets/information-view.png)

El icono de puntos suspensivos le permite acceder a acciones adicionales que puede realizar en el programa.

![Botón de puntos suspensivos para programas](assets/program-ellipsis.png)

* Navegar a un en particular [entorno](/help/using/managing-environments.md) del programa
* Abra el [descripción general del programa](#program-overview)
* [Editar el programa](/help/getting-started/program-setup.md)
* Mostrar monitorización

#### Pestaña Licencia {#license-tab}

El **Licencia** le permite acceder rápidamente al tablero de licencias.

### Enlaces rápidos {#quick-links}

La sección de vínculos rápidos le permite acceder a recursos relacionados de uso común.

## Ventana Resumen del Programa {#program-overview}

Una vez que seleccione un programa en la consola Mis programas, accederá a Información general del programa.

![Información general del programa](assets/program-overview.png)

La descripción general del programa le permite acceder a todos los detalles de un programa de Cloud Manager. Al igual que la consola Mis programas, está formada por varias partes.

1. [Barras de herramientas](#program-overview-toolbar) para volver rápidamente a la consola Mis programas y navegar por el programa
1. [Fichas](#program-tabs) cambiar entre los diferentes aspectos del programa
1. A [llamada a acción](#cta) basado en las últimas acciones del programa
1. Un [descripción general de los entornos](#environments) del programa
1. Un [descripción general de las canalizaciones](#pipelines) del programa
1. Vínculos a [recursos útiles](#useful-resources)

### Barras de herramientas {#program-overview-toolbar}

Las barras de herramientas para la descripción general del programa son muy similares a las del [Consola Mis programas.](#my-programs-toolbars) Aquí solo se ilustran las diferencias.

#### Encabezado de Cloud Manager {#cloud-manager-header-2}

El encabezado de Cloud Manager tiene un menú de hamburguesa que se abre automáticamente para mostrar las pestañas navegables de la descripción general del programa.

![Menú de hamburguesa de Cloud Manager](assets/cloud-manager-hamburger.png)

Toque o haga clic en el icono de menú de hamburguesa para ocultar las pestañas.

#### Barra de programas {#program-toolbar-2}

La barra de herramientas de programas le permite cambiar rápidamente a otros programas, pero además le da acceso a acciones apropiadas para el contexto, como agregar y editar el programa.

![Barra de herramientas Programa](assets/cloud-manager-program-toolbar.png)

Además, la barra de herramientas siempre indica en qué ficha se encuentra si ha elegido ocultar las fichas mediante el menú de hamburguesa.

### Fichas de programa {#program-tabs}

Cada programa tiene muchas opciones y datos asociados. Estos datos se recopilan en pestañas para facilitar la navegación por el programa. Las pestañas le permiten acceder a:

* Información general: la descripción general del programa tal como se describe en el documento actual
* [Actividad](/help/using/managing-pipelines.md#activity) - El historial de ejecuciones de canalización del programa
* [Canalizaciones](/help/using/managing-pipelines.md#pipelines) - Todas las canalizaciones configuradas para el programa
* [Repositorios](/help/managing-code/repositories.md) - Todos los repositorios configurados para el programa
* [Informes](/help/using/monitoring-environments.md#system-monitoring-overview) - Métricas como datos de SLA
* [Entornos](/help/using/managing-environments.md) - Todos los entornos configurados para el programa
* [Conjuntos de contenido](/help/using/content-copy.md) - Conjuntos de contenido creados con fines de copia
* [Copiar actividad de contenido](/help/using/content-copy.md) - Actividades de copia de contenido
* Rutas de aprendizaje: Recursos de aprendizaje adicionales sobre Cloud Manager

De forma predeterminada, al abrir un programa, llega a la **Información general** pestaña. La pestaña actual está resaltada. Seleccione otra pestaña para mostrar sus detalles.

Utilice el menú de hamburguesa de la [Encabezado de Cloud Manager](#cloud-manager-header-2) para ocultar las pestañas.

### Llamada a acción {#cta}

La sección de llamada a la acción le proporcionará información útil según el estado del programa. Para un programa nuevo, puede ver los pasos siguientes ofrecidos, así como un recordatorio de una fecha de lanzamiento, [se configura durante la creación del programa.](/help/getting-started/program-setup.md)

Para un programa activo, el estado de la última implementación con vínculos para obtener más información e iniciar una nueva implementación.

![Llamada a acción](assets/info-banner.png)

### Tarjeta Entornos {#environments}

El **Entornos** le ofrece una descripción general de sus entornos, así como vínculos para acciones rápidas.

La tarjeta **Entornos** solo enumera tres entornos. Clic **Mostrar todo** para ver todos los entornos del programa.

Consulte el documento [Administración de entornos](/help/using/managing-environments.md) para obtener más información sobre cómo administrar los entornos.

### Tarjeta de canalizaciones {#pipelines}

El **Canalizaciones** Esta tarjeta le ofrece una descripción general de sus canalizaciones, así como vínculos para acciones rápidas.

El **Canalizaciones** La tarjeta solo enumera tres canalizaciones. Clic **Mostrar todo** para ver todas las canalizaciones del programa.

Consulte el documento [Administración de canalizaciones](/help/using/managing-pipelines.md) para obtener más información sobre cómo administrar las canalizaciones.

### Recursos útiles {#useful-resources}

El **Recursos útiles** proporciona vínculos a recursos de aprendizaje adicionales para Cloud Manager.
