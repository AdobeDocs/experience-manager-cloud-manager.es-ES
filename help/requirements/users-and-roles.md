---
title: Agregar usuarios y funciones
description: Aprenda a utilizar Admin Console para agregar usuarios y funciones y crear perfiles.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: dd96d773ea3e6b9c45886fe41b28d3dd70cb8a61
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 22%

---


# Agregar usuarios y funciones {#add-users-and-roles}

Muchas funciones de [!UICONTROL Cloud Manager] requieren permisos específicos para su uso. Por ejemplo, solo se permite a determinados usuarios establecer los indicadores clave de rendimiento (KPI) de un programa. Estos permisos se agrupan lógicamente en funciones.

[!UICONTROL Cloud Manager] actualmente define cuatro funciones para los usuarios que rigen la disponibilidad de funciones específicas:

* Propietario del negocio
* Administrador de programa
* Administrador de implementación
* Desarrollador

>[!NOTE]
>
>Para usar [!UICONTROL Cloud Manager], debe tener un Adobe ID y el contexto del producto de Adobe Managed Services.

## Definiciones de funciones {#role-definitions}

Esta tabla resume las funciones.

| [!UICONTROL Cloud Manager] Función | Descripción |
|--- |--- |
| Propietario del negocio | Este usuario es responsable de definir los indicadores clave de rendimiento (KPI), aprobar implementaciones de producción y anular errores importantes de tres niveles cuando sea necesario. |
| Administrador de programa | Este usuario utiliza [!UICONTROL Cloud Manager] para realizar la configuración del equipo, revise el estado, vea los KPI y pueda aprobar errores importantes de 3 niveles cuando sea necesario. |
| Administrador de implementación | Este usuario gestiona las operaciones de implementación y utiliza [!UICONTROL Cloud Manager] para ejecutar implementaciones de ensayo/producción, edite las canalizaciones CI/CD, apruebe errores importantes de 3 niveles cuando sea necesario y pueda acceder al repositorio de Git. |
| Desarrollador | Este usuario desarrolla y prueba el código de aplicación personalizado y utiliza principalmente [!UICONTROL Cloud Manager] para ver el estado de implementación y puede acceder al repositorio de Git para confirmaciones de código. |
| Ingeniero de éxito del cliente (Customer Success Engineer) | Este usuario suele admitir el éxito de los clientes para los clientes de AMS e interactúa con [!UICONTROL Cloud Manager] para ejecutar despliegues que requieran supervisión de la CSE. |
| Autor de contenido | Este usuario generalmente no interactúa con [!UICONTROL Cloud Manager] pero puede utilizar la variable [!UICONTROL Cloud Manager] alternador de programas para acceder a AEM. |

>[!NOTE]
>
>El perfil de desarrollador en el Admin Console no está relacionado con la función de desarrollador en [!UICONTROL Cloud Manager].

## Uso de Admin Console para crear un perfil {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] las funciones se administran desde el Admin Console . Las suscripciones a funciones específicas se proporcionan añadiendo el usuario a un [!UICONTROL Cloud Manager] perfil de producto.

Admin Console es una ubicación central para administrar los derechos de Adobe en toda la organización. Para obtener más información sobre Adobe Admin Console, consulte la documentación de [Admin Console.](https://helpx.adobe.com/es/enterprise/using/admin-console.html)

Para proporcionar los permisos adecuados basados en funciones a [!UICONTROL Cloud Manager] usuarios, un administrador de la organización del cliente debe crear nuevos perfiles de producto en la sección [!UICONTROL AEM Managed Services] contexto de producto correspondiente a cada uno de los cuatro [!UICONTROL Cloud Manager] roles:

* Propietario del negocio
* Administrador de implementación
* Desarrollador
* Administrador de programa

Puede crear o agregar usuarios/grupos a estos perfiles de producto con Admin Console.

1. Inicie sesión en el Admin Console en [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Haga clic en el **Información general** , haga clic en el producto que desee modificar en la pestaña **Productos y servicios** tarjeta. Si no aparece en la lista, use el **Productos** para localizar el producto y hacer clic en él.

   ![Ficha Información general de Admin Console](/help/assets/admin-console-overview.png)

1. En el **Productos** , haga clic en el entorno para el que desee agregar usuarios/grupos a perfiles de producto.

   ![Pestaña Productos de Admin Console](/help/assets/admin-console-product.png)

1. En el **Perfil del producto** del producto, haga clic en **Nuevo perfil** para agregar un nuevo perfil.

   ![Perfil nuevo](/help/assets/admin-console-product-profiles.png)

1. Proporcione la información para configurar una nueva función para [!UICONTROL Cloud Manager].

   * **Nombre del perfil** - El **Nombre del perfil** puede ser cualquier cosa, aunque para evitar confusiones, se recomienda usar los valores de la variable **Nombre de perfil recomendado** para abrir el Navegador.
   * **Nombre para mostrar** - El **Nombre para mostrar** debe ser el valor técnico definido por [!UICONTROL Cloud Manager] (véase la tabla siguiente).
   * **Grupo de permisos** - Puede elegir un grupo de permisos para el perfil (no siempre disponible).

   ![Creación de un nuevo perfil](/help/assets/screen_shot_2018-05-04at171819.png)

   | Función | Nombre para mostrar (obligatorio) | Nombre de perfil recomendado |
   |---|---|---|
   | Propietario del negocio | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Rol de propietario del negocio |
   | Administrador de implementación | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Función de administrador de implementación |
   | Desarrollador | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Función de desarrollador |
   | Administrador de programa | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Función de administrador de programas |


1. Haga clic en **Listo** para guardar el nuevo perfil.

## Asignar perfiles a usuarios o grupos de usuarios {#assign-profiles}

Una vez creados los perfiles de producto, puede asignarles usuarios o grupos de usuarios.

1. Inicie sesión en el Admin Console en [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. En el Admin Console, elija la opción **Usuarios** pestaña .

   ![Ficha Usuarios](/help/assets/admin-console-users.png)

1. Haga clic en **Usuarios** en el panel de navegación izquierdo y, a continuación, haga clic en un usuario para modificarlo.

1. Haga clic en el botón de puntos suspensivos de la sección **Productos** y seleccione **Editar**.

   ![Editar usuario](/help/assets/admin-console-edit-user.png)

1. En el **Editar productos y grupos de usuarios** , haga clic en el botón más y seleccione los perfiles que desea asignar al usuario.

   * Si el usuario ya está asignado a las funciones, el botón más será un botón de edición (un lápiz), pero funciona del mismo modo.

   ![Editar productos y grupos de usuarios](/help/assets/admin-console-edit-products-and-user-groups.png)

1. Haga clic en **Guardar** para guardar los perfiles en el usuario.

Repita los mismos pasos para asignar perfiles a grupos de usuarios, pero seleccione **Grupos de usuarios** del panel de navegación izquierdo de la **Usuarios** pestaña . Haga clic en un grupo de usuarios y seleccione el **Perfiles de producto asignados** y haga clic en **Asignar perfil de producto** para asignar perfiles.

![Asignar perfiles al grupo](/help/assets/admin-console-edit-user-groups.png)
