---
title: Permisos personalizados
description: Descubra cómo puede utilizar permisos personalizados para crear nuevos perfiles de permisos personalizados con permisos configurables para restringir el acceso a programas, canalizaciones y entornos para usuarios de Cloud Manager.
source-git-commit: e1a3814041a8a7842e39ab09289c83e9c935b4ab
workflow-type: tm+mt
source-wordcount: '1444'
ht-degree: 2%

---


# Permisos personalizados {#custom-permissions}

Descubra cómo puede utilizar permisos personalizados para crear nuevos perfiles de permisos personalizados con permisos configurables para restringir el acceso a programas, canalizaciones y entornos para usuarios de Cloud Manager.

>[!NOTE]
>
>Esta función solo está disponible para [el programa de adopción temprana.](/help/release-notes/current.md#early-adoption)

## Introducción {#introduction}

Cloud Manager tiene un conjunto de funciones predefinidas que rigen el acceso a varias funciones de Cloud Manager:

* Propietario del negocio
* Administrador de programa
* Administrador de implementación
* Desarrollador

Los permisos personalizados permiten a los usuarios crear nuevos perfiles de permisos personalizados con permisos configurables para restringir el acceso de los usuarios de Cloud Manager a programas, canalizaciones y entornos.

>[!TIP]
>
>Para obtener más información sobre las funciones predefinidas, consulte el documento [Permisos basados en funciones.](/help/requirements/role-based-permissions.md)

## Uso de permisos personalizados {#using}

Para crear y utilizar sus propios permisos personalizados se requieren tres pasos:

1. [Cree un nuevo perfil de producto.](#create)
1. [Asigne permisos personalizados al nuevo perfil de producto.](#assign-permissions)
1. [Asigne usuarios al nuevo perfil de productos.](#assign-users)

En esta sección se detallan estos pasos. Puede que le resulte útil consultar la [Términos](#terms) y [Permisos configurables](#configurable-permissions) secciones a medida que crea sus propios permisos personalizados.

>[!NOTE]
>
>Debe tener derechos de administrador de productos en Admin Console para crear nuevos perfiles y administrar permisos para Cloud Manager.

### Crear un nuevo perfil de producto {#create}

Primero debe crear un nuevo perfil de producto para poder asignar permisos personalizados.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)

1. Seleccione el producto **AEM Managed Services**.

1. Busque una instancia de y con un nombre que coincida con el patrón `*-cloud-manager` y toque o haga clic para administrar usuarios y permisos.

1. Se le redirigirá a **Productos** pestaña del Admin Console, donde puede administrar usuarios y permisos para cloud manager. En el Admin Console, toque o haga clic en **Nuevo perfil** botón.

![Botón Nuevo perfil](/help/assets/admin-console-new-profile.png)

1. Proporcione los detalles generales sobre el perfil.

   * **Nombre del perfil del producto** - Un nombre descriptivo para el perfil
   * **Nombre para mostrar** - Un nombre abreviado que se mostrará en la interfaz de usuario (opciones)
   * **Descripción** - Una descripción informativa del perfil en la que se explique su finalidad (opcional)
   * **Notificar a los usuarios por correo electrónico** : cuando se selecciona, se notifica a los usuarios por correo electrónico cuando se agregan o eliminan de este perfil.

1. Haga clic o pulse **Guardar** cuando se complete.

El nuevo perfil de producto se guarda y es visible en la lista de perfiles de producto del Admin Console.

### Asignar permisos personalizados al perfil {#assign-permissions}

Ahora que tiene un nuevo perfil de producto, puede asignarle permisos personalizados.

1. En el Admin Console, toque o haga clic en el nombre del [nuevo perfil de producto que acaba de crear.](#create)

1. En la ventana que se abre, seleccione la **Permisos** para ver una lista de permisos editables.

   ![Permisos editables](/help/assets/permissions-tab.png)

1. Toque o haga clic en **Editar** Vínculo de un permiso para editarlo.

1. El **Editar permisos** se abre.
   * El permiso seleccionado en el paso anterior se selecciona en la columna izquierda.
   * Los elementos de permiso disponibles para la asignación del permiso se encuentran en la columna central denominada **Permiso disponible** Elementos.
   * Los elementos de permisos asignados se encuentran en la columna derecha con la etiqueta **Elementos de permisos incluidos**.

   ![Editar elementos de permiso](/help/assets/edit-permission-items.png)

1. Pulse o haga clic en el signo más (`+`) junto al elemento de permiso para añadirlo a la columna **Elementos de permisos incluidos**.

   * Haga clic o pulse en `i` junto a un elemento de permiso para obtener más información al respecto.

1. Haga clic o pulse en **Añadir todo** en la parte superior del **Permisos disponibles** para agregar todos los permisos. Del mismo modo, toque o haga clic **Eliminar todo** para quitar todos los permisos seleccionados previamente.

1. Haga clic o pulse **Guardar** cuando haya terminado de definir los elementos de permiso para el nuevo perfil de producto.

El nuevo perfil de producto ahora se guarda con sus permisos personalizados.

### Asignar usuarios a los permisos personalizados {#assign-users}

Ahora puede asignar usuarios al nuevo perfil de producto que ha creado con permisos personalizados.

1. En el Admin Console, toque o haga clic en el nombre del [nuevo perfil de producto al que acaba de asignar permisos personalizados.](#assign-permissions)

1. En la ventana que se abre, seleccione la **Usuarios** pestaña.

1. Haga clic o pulse en **Agregar usuarios** y asigne usuarios a su nuevo perfil de productos con permisos personalizados.

Consulte la sección **Adición de usuarios y grupos de usuarios a un perfil de producto** del documento [Administración de perfiles de producto para usuarios empresariales](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html) para obtener más información sobre cómo utilizar el Admin Console.

## Permisos configurables {#configurable-permissions}

Los siguientes permisos están disponibles para crear perfiles personalizados.

| Permiso | Descripción |
|---|---|
| Acceso al programa | Permitir que los usuarios tengan acceso a los programas |
| Edición de programa | Permitir que los usuarios editen programas |
| Creación de canalización | Permitir que los usuarios creen nuevas canalizaciones |
| Eliminación de canalización | Permitir que los usuarios eliminen canalizaciones |
| Edición de canalización | Permitir que los usuarios editen canalizaciones |
| Implementaciones de producción aprobadas/rechazadas | Permitir que los usuarios aprueben o rechacen un paso de implementación de producción |
| Ejecuciones de canalización canceladas | Permitir a los usuarios cancelar las ejecuciones de canalización |
| Inicio de ejecuciones de canalización | Permitir que los usuarios inicien nuevas ejecuciones de canalización |
| Anular/Rechazar errores importantes de métricas | Permitir que los usuarios anulen o rechacen errores importantes de métricas |
| Programación de implementaciones de producción | Permitir a los usuarios programar un paso de implementación de producción |
| Acceso a información de repositorio | Permitir a los usuarios acceder a la información del repositorio y generar una contraseña de acceso |

### Permisos en el nivel de organización {#organization-level}

Los permisos de nivel de organización hacen referencia a permisos que siempre se conceden a todos los programas de una organización.

Los siguientes permisos son permisos de nivel de organización:

* **Acceso a información de repositorio** Este permiso de nivel de inquilino/organización permite a los usuarios generar un nombre de usuario, una contraseña y una URL de repositorio para acceder y contribuir en el proyecto del cliente.
   * El nombre de usuario y la contraseña para acceder al repositorio serán comunes en todos los repositorios de la organización, pero la URL del repositorio será única para cada programa.
   * Consulte el documento [Repositorio de códigos de origen](/help/requirements/source-code-repository.md) para obtener más información.

## Términos {#terms}

Los siguientes términos se utilizan para crear y administrar permisos personalizados y funciones predefinidas.

| Término | Descripción |
|---|---|
| Permisos predefinidos | Funciones predefinidas como **Propietario del negocio**, **Administrador de implementación**, etc. para regular varias funciones de Cloud Manager. Para obtener más información sobre las funciones predefinidas, consulte el documento [Permisos basados en funciones.](/help/requirements/role-based-permissions.md) |
| Permisos personalizados | Características de Cloud Manager que permiten a los usuarios crear perfiles de permiso para definir funciones que rigen las funciones compatibles con Cloud Manager |
| Perfil de permisos | Se crea en Admin Console para administrar permisos configurables que se aplicarán a los usuarios que forman parte del perfil de permisos |
| Permiso configurable | Permisos de Cloud Manager que se pueden configurar en el perfil de permisos |
| Elemento de permiso | Un programa, entorno o recurso de canalización en el que se puede aplicar un permiso |

Los elementos de permisos hacen referencia al ámbito en el que se aplicará el permiso. Normalmente, será una de las siguientes:

| Tipo de elemento de permiso | Ejemplos | Descripción |
|---|---|---|
| Organización | organización:compañíaA | Todos los recursos aplicables de una organización. Un recurso puede ser un programa, un entorno o una canalización. Si el usuario agrega una organización para cualquier permiso, todos los recursos nuevos de esa organización también tendrán ese permiso. |
| Programa | Programa A | Todos los recursos aplicables de un programa |
| Entorno | Programa A: entorno | Aplicable en un entorno específico |
| Canalización | Programa A: Canalización | Aplicable en una canalización específica |

## Restricciones {#limitations}

Tenga en cuenta las siguientes limitaciones al utilizar permisos personalizados.

* A [el conjunto limitado de permisos está disponible](#configurable-permissions) para crear perfiles personalizados.
* Recursos como programa, entorno, canalización, etc. Los permisos creados en Cloud Manager pueden tardar dos minutos en mostrarse en Admin Console para la configuración de permisos.
* En casos excepcionales en los que el servicio de permisos personalizados no responde, los perfiles predefinidos siguen estando disponibles y los usuarios de perfiles predefinidos siguen teniendo el acceso adecuado.

## Preguntas más frecuentes {#faq}

### ¿Qué perfiles de permisos son perfiles de permisos predefinidos?

* Propietario del negocio
* Administrador de programa
* Administrador de implementación
* Desarrollador

Para obtener más información sobre las funciones predefinidas, consulte el documento [Permisos basados en funciones.](/help/requirements/role-based-permissions.md)

### ¿Qué les sucede a los perfiles de permiso predefinidos con introducción a los perfiles personalizados?

Los perfiles de producto predeterminados y las funciones de Cloud Manager siguen funcionando igual que antes.

### ¿Puedo editar perfiles de permisos predefinidos?

No, los perfiles predeterminados no se pueden editar. No puede agregar ni quitar permisos al perfil de permisos predeterminado. Solo puede añadir o quitar usuarios de perfiles predefinidos.

### ¿Debería eliminar los perfiles de permiso predefinidos, ya que los perfiles personalizados ya están disponibles?

Los perfiles de permiso predefinidos no se deben eliminar del Admin Console.

### ¿Puedo añadir usuarios a varios perfiles de permisos?

Sí, un usuario puede formar parte de varios perfiles, incluidos perfiles de permisos predefinidos y personalizados. Cuando se asigna a un usuario a varios perfiles, los permisos combinados de todos los perfiles de permiso asignados estarán disponibles para ese usuario.

### ¿Qué sucede si un usuario tiene permiso para editar un entorno o canalización pero no tiene acceso a un programa que contenga el entorno o canalización?

En este caso, el usuario no podrá acceder al entorno o la canalización si no tiene el **Acceso al programa** permisos que contengan el entorno o la canalización.

### AEM ¿Qué sucede si tengo programas as a Cloud Service y de AMS tanto en la misma organización de IMS como en la otra? ¿Puedo administrar permisos desde un perfil? {#ams-and-aemaacs}

Debe crear un perfil independiente para cada tipo de producto (es decir, uno para los Cloud Service y otro para los AEM de Adobe Managed Services o AMS).
