---
title: Permisos personalizados
description: Descubra cómo puede utilizar los permisos personalizados para crear nuevos perfiles de estos con permisos configurables para restringir el acceso a programas, canalizaciones y entornos para usuarios de Cloud Manager.
exl-id: a81eda9f-aa89-40ea-8e4c-52367a0a6aba
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 99%

---

# Permisos personalizados {#custom-permissions}

Descubra cómo puede utilizar los permisos personalizados para crear nuevos perfiles de estos con permisos configurables para restringir el acceso a programas, canalizaciones y entornos para usuarios de Cloud Manager.

## Introducción {#introduction}

Cloud Manager tiene un conjunto de funciones predefinidas que regulan el acceso a las diversas funciones de Cloud Manager:

* Propietario del negocio
* Administrador de programa
* Administrador de implementación
* Desarrollador

Los permisos personalizados permiten a los usuarios crear nuevos perfiles de permisos personalizados con permisos configurables para restringir el acceso de los usuarios de Cloud Manager a programas, canalizaciones y entornos.

>[!TIP]
>
>Para obtener más información sobre las funciones predefinidas, consulte [Permisos basados en funciones](/help/requirements/role-based-permissions.md).

## Utilizar los permisos personalizados {#using}

La creación y el uso de sus propios permisos personalizados requieren los tres pasos siguientes:

1. [Cree un nuevo perfil de producto](#create).
1. [Asigne permisos personalizados al nuevo perfil de producto](#assign-permissions).
1. [Asigne usuarios al nuevo perfil de producto](#assign-users).

En esta sección se detallan estos pasos. Puede que le resulte útil consultar las secciones [Términos](#terms) y [Permisos configurables](#configurable-permissions) a medida que crea sus propios permisos personalizados.

>[!NOTE]
>
>Debe tener derechos de administrador de productos en Admin Console para crear nuevos perfiles y administrar permisos para Cloud Manager.

### Crear un nuevo perfil de producto {#create}

Primero cree un nuevo perfil de producto para poder asignar permisos personalizados.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)

1. Seleccione el producto **AEM Managed Services**.

1. Busque una instancia con un nombre que coincida con el patrón `*-cloud-manager` y haga clic para administrar usuarios y permisos.

1. Se le redirigirá a la pestaña **Productos** de Admin Console, donde puede administrar usuarios y permisos para Cloud Manager. En Admin Console, haga clic en **Nuevo perfil**.

![Botón Nuevo perfil](/help/assets/admin-console-new-profile.png)

1. Proporcione los detalles generales sobre el perfil.

   * **Nombre del perfil del producto**: un nombre descriptivo para el perfil
   * **Nombre para mostrar**: Un nombre abreviado que se muestra en la interfaz de usuario (opciones)
   * **Descripción**: una descripción informativa del perfil en la que se explique su finalidad (opcional)
   * **Notificar a los usuarios por correo electrónico**: Cuando se selecciona, el sistema notifica a los usuarios por correo electrónico cuando se añaden o quitan de este perfil.

1. Haga clic en **Guardar**.

El nuevo perfil de producto se guarda y es visible en la lista de perfiles de producto de Admin Console.

### Asigne permisos personalizados al nuevo perfil de producto {#assign-permissions}

Ahora que tiene un nuevo perfil de producto, puede asignarle permisos personalizados.

1. En Admin Console, haga clic en el nombre del [nuevo perfil de producto que acaba de crear](#create).

1. En la ventana que se abre, seleccione la pestaña **Permisos** para ver una lista de permisos editables.

   ![Permisos editables](/help/assets/permissions-tab.png)

1. Haga clic en el vínculo **Editar** para obtener permiso para editarlo.

1. Se abre la ventana **Editar permisos**.
   * El permiso seleccionado en el paso anterior se selecciona en la columna izquierda.
   * Los elementos de permiso disponibles para la asignación del permiso se encuentran en la columna central denominada Elementos de **permisos disponibles**.
   * Los elementos de permisos asignados se encuentran en la columna derecha con la etiqueta **Elementos de permisos incluidos**.

   ![Editar elementos de permiso](/help/assets/edit-permission-items.png)

1. Haga clic en el signo más (`+`) junto al elemento de permiso para añadirlo a la columna **Elementos de permisos incluidos**. Pulse en el icono `i` situado junto a un elemento de permiso para obtener más información al respecto.

1. En la parte superior de la columna **Permisos disponibles**, haga clic en **Agregar todos** para agregar todos los permisos. Del mismo modo, pulse o haga clic en **Quitar todo** para quitar todos los permisos seleccionados previamente.

1. Haga clic en **Guardar** cuando haya terminado de definir los elementos de permiso para el nuevo perfil de producto.

El nuevo perfil de producto se guarda ahora con sus permisos personalizados.

### Asigne usuarios al nuevo perfil de producto. {#assign-users}

Ahora puede asignar usuarios al nuevo perfil de producto que ha creado con permisos personalizados.

1. En Admin Console, pulse o haga clic en el nombre del [nuevo perfil de producto al que acaba de asignar permisos personalizados](#assign-permissions).

1. En la ventana que se abre, seleccione la pestaña **Usuarios**.

1. Haga clic en **Añadir usuarios** y asigne usuarios a su nuevo perfil de productos con permisos personalizados.

Consulte la sección **Adición de usuarios y grupos de usuarios a un perfil de producto** del documento [Administración de perfiles de producto para usuarios empresariales](https://helpx.adobe.com/es/enterprise/using/support-for-experience-cloud.html?lang=es) para obtener más información sobre cómo utilizar Admin Console.

## Permisos configurables {#configurable-permissions}

Los siguientes permisos están disponibles para crear perfiles personalizados.

| Permiso | Descripción |
|---|---|
| Acceso al programa | Permitir que los usuarios tengan acceso a los programas |
| Edición del programa | Permitir que los usuarios editen programas |
| Creación de canalización | Permitir que los usuarios creen nuevas canalizaciones |
| Eliminación de canalización | Permitir que los usuarios eliminen canalizaciones |
| Edición de canalizaciones | Permitir que los usuarios editen canalizaciones |
| Aprobar/Rechazar implementaciones de producción | Permitir que los usuarios aprueben o rechacen un paso de implementación de producción |
| Cancelar ejecuciones de canalización | Permitir a los usuarios cancelar las ejecuciones de canalización |
| Iniciar ejecuciones de canalizaciones | Permitir que los usuarios inicien nuevas ejecuciones de canalizaciones |
| Anular/Rechazar errores de métricas importantes | Permitir que los usuarios anulen o rechacen errores importantes de métricas |
| Programar implementaciones de producción | Permitir a los usuarios programar un paso de implementación de producción |
| Acceso a información de repositorios | Permitir a los usuarios acceder a la información del repositorio y generar una contraseña de acceso |
| Creación de repositorios | Permitir a los usuarios crear nuevos repositorios de Git |
| Eliminación de repositorios | Permitir que los usuarios eliminen repositorios Git |
| Edición de repositorios | Permitir que los usuarios editen repositorios de Git |
| Generación de código de repositorios | Permitir que los usuarios generen proyectos a partir de arquetipos |
| Administración de copia de contenido | Permitir que los usuarios administren las operaciones de copia de contenido |

### Permisos de nivel de organización {#organization-level}

Los permisos de nivel de organización siempre se aplican a todos los programas de una organización.

Un ejemplo de un permiso de nivel de organización en Cloud Manager es **Acceso a información de repositorio**. Este permiso permite a los usuarios generar un nombre de usuario, una contraseña y una URL de repositorio para acceder a proyectos de clientes y contribuir a ellos. Aunque el nombre de usuario y la contraseña siguen siendo coherentes en todos los repositorios de la organización, cada programa tiene una URL de repositorio única.

Consulte el documento [Repositorio de códigos de origen](/help/requirements/source-code-repository.md) para obtener más información.

## Términos {#terms}

Los siguientes términos se utilizan para crear y administrar permisos personalizados y funciones predefinidas.

| Término | Descripción |
|---|---|
| Permisos predefinidos | Funciones predefinidas como **Propietario del negocio**, **Administrador de implementación**, etc. para regular varias funciones de Cloud Manager. Para obtener más información sobre las funciones predefinidas, consulte [Permisos basados en funciones](/help/requirements/role-based-permissions.md). |
| Permisos personalizados | Características de Cloud Manager que permiten a los usuarios crear perfiles de permiso para definir funciones que regulen las funciones compatibles con Cloud Manager |
| Perfil de permisos | Se crea en Admin Console para administrar permisos configurables que se aplicarán a los usuarios que forman parte del perfil de permisos |
| Permiso configurable | Permisos de Cloud Manager que se pueden configurar en el perfil de permisos |
| Elemento de permiso | Un programa, entorno o recurso de canalización sobre el que se puede aplicar un permiso |

Los elementos de permisos hacen referencia al ámbito en el que se aplicará el permiso. Normalmente, será uno de los siguientes:

| Tipo de elemento de permiso | Ejemplos | Descripción |
|---|---|---|
| Organización | organization:companyA | Todos los recursos aplicables de una organización. Un recurso puede ser un programa, un entorno o una canalización. Si el usuario añade una organización para cualquier permiso, todos los recursos nuevos de esa organización también tendrán ese permiso. |
| Programa | Programa A | Todos los recursos aplicables de un programa |
| Entorno | Programa A: entorno | Aplicable en un entorno específico |
| Canalización | Programa A: canalización | Aplicable en una canalización específica |

## Restricciones {#limitations}

Tenga en cuenta las siguientes limitaciones al utilizar los permisos personalizados:

* Un [conjunto limitado de permisos está disponible](#configurable-permissions) para crear perfiles personalizados.
* Recursos como programa, entorno, canalización, etc. Los permisos creados en Cloud Manager pueden tardar dos minutos en mostrarse en Admin Console para la configuración de permisos.
* En casos excepcionales en los que el servicio de permisos personalizados no responde, los perfiles predefinidos siguen estando disponibles y teniendo el acceso adecuado.

## Preguntas frecuentes {#faq}

### ¿Qué perfiles de permisos son los predefinidos?

* Propietario del negocio
* Administrador de programa
* Administrador de implementación
* Desarrollador

Para obtener más información sobre las funciones predefinidas, consulte [Permisos basados en funciones](/help/requirements/role-based-permissions.md).

### ¿Qué les sucede a los perfiles de permiso predefinidos con introducción a los perfiles personalizados?

Los perfiles de producto predeterminados y las funciones de Cloud Manager siguen funcionando igual que antes.

### ¿Puedo editar perfiles de permisos predefinidos?

No, los perfiles predeterminados no se pueden editar. No puede añadir ni quitar permisos al perfil de permisos predeterminado. Solo puede añadir o quitar usuarios de perfiles predefinidos.

### ¿Debería eliminar los perfiles de permiso predefinidos, ya que los perfiles personalizados ya están disponibles?

Los perfiles de permiso predefinidos no se deben eliminar de Admin Console.

### ¿Puedo añadir usuarios a varios perfiles de permisos?

Sí, un usuario puede formar parte de varios perfiles, incluidos perfiles de permisos predefinidos y personalizados. Cuando se asigna a un usuario a varios perfiles, los permisos combinados de todos los perfiles de permiso asignados están disponibles para ese usuario.

### ¿Qué sucede si un usuario tiene permiso para editar un entorno o canalización, pero no tiene acceso a un programa que contenga el entorno o canalización?

En este caso, el usuario no puede acceder al entorno o la canalización si no tiene los permisos de **Acceso al programa** que contengan el entorno o la canalización.

### ¿Qué sucede si tengo los programas AEM as a Cloud Service y AMS en la misma organización de IMS? ¿Puedo administrar permisos desde un perfil? {#ams-and-aemaacs}

Cree un perfil independiente para cada tipo de producto. Es decir, uno para AEM as Cloud Service y otro para Managed Services de Adobe o AMS.
