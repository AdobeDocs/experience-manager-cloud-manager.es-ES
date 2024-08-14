---
title: Agregar usuarios y funciones
description: Aprenda a utilizar Admin Console para agregar usuarios y funciones y crear perfiles.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 81%

---


# Agregar usuarios y funciones {#add-users-and-roles}

Muchas funciones de [!UICONTROL Cloud Manager] requieren permisos específicos para su uso. Por ejemplo, solo se permite a determinados usuarios establecer los indicadores clave de rendimiento (KPI) de un programa. Estos permisos se agrupan lógicamente en funciones.

[!UICONTROL Cloud Manager] actualmente define cuatro funciones de los usuarios que rigen la disponibilidad de las siguientes funciones específicas:

* Propietario del negocio
* Administrador de programa
* Administrador de implementación
* Desarrollador

>[!NOTE]
>
>Para usar [!UICONTROL Cloud Manager], debe tener un Adobe ID y el contexto del producto de Adobe Managed Services.

## Definiciones de funciones {#role-definitions}

Esta tabla resume las funciones.

| Función [!UICONTROL Cloud Manager] | Descripción |
|--- |--- |
| Propietario del negocio | Este usuario es responsable de definir los indicadores clave de rendimiento (KPI), aprobar implementaciones de producción y anular errores importantes de tres niveles cuando sea necesario. |
| Administrador de programa | Este usuario emplea [!UICONTROL Cloud Manager] para realizar la configuración del equipo, revisar el estado y ver los indicadores clave de rendimiento (KPI) y puede aprobar errores importantes de tres niveles cuando sea necesario. |
| Administrador de implementación | Este usuario gestiona las operaciones de implementación y utiliza [!UICONTROL Cloud Manager] para ejecutar implementaciones de ensayo/producción, editar las canalizaciones CI/CD, aprobar errores importantes de tres niveles cuando sea necesario y puede acceder al repositorio de Git. |
| Desarrollador | Este usuario desarrolla y prueba el código de aplicación personalizado y emplea principalmente [!UICONTROL Cloud Manager] para ver el estado de implementación y puede acceder al repositorio de Git para confirmaciones de código. |
| Ingeniero de éxito del cliente (Customer Success Engineer) | Este usuario suele admitir el éxito de los clientes para los clientes de AMS e interactúa con [!UICONTROL Cloud Manager] para ejecutar implementaciones que requieran supervisión del ingeniero de éxito del cliente (CSE). |
| Autor de contenido | Este usuario generalmente no interactúa con [!UICONTROL Cloud Manager], pero puede utilizar el conmutador de programas de [!UICONTROL Cloud Manager] para acceder a AEM. |

>[!NOTE]
>
>El personaje ficticio del desarrollador en Admin Console no está relacionado con la función de desarrollador en [!UICONTROL Cloud Manager].

## Uso de Admin Console para crear un perfil {#using-admin-console-to-create-a-profile}

Las funciones de [!UICONTROL Cloud Manager] se administran desde Admin Console. Las suscripciones a funciones específicas se proporcionan añadiendo el usuario a un perfil de producto de [!UICONTROL Cloud Manager].

Admin Console es una ubicación central para administrar los derechos de Adobe en toda la organización. Para obtener más información sobre Adobe Admin Console, consulte la documentación de [Admin Console](https://helpx.adobe.com/es/enterprise/using/admin-console.html).

Para proporcionar los permisos adecuados basados en funciones a los usuarios de [!UICONTROL Cloud Manager], un administrador de la organización del cliente debe crear perfiles de producto nuevos en el contexto de producto de [!UICONTROL AEM Managed Services] correspondiente a cada una de las cuatro funciones de [!UICONTROL Cloud Manager]:

* Propietario del negocio
* Administrador de implementación
* Desarrollador
* Administrador de programa

Puede crear o agregar usuarios/grupos a estos perfiles de producto con Admin Console.

1. Inicie sesión en el Admin Console en [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

1. Haga clic en la ficha **Información general**, haga clic en el producto que desee modificar en la tarjeta **Productos y servicios**. Si no aparece en la lista, use la pestaña **Productos** para localizar el producto y hacer clic en él.

   ![Pestaña Información general de Admin Console](/help/assets/admin-console-overview.png)

1. En la pestaña **Productos**, haga clic en el entorno para el que desee agregar usuarios/grupos a perfiles de producto.

   ![Pestaña Productos de Admin Console](/help/assets/admin-console-product.png)

1. En la pestaña **Perfil de producto** del producto, haga clic en **Nuevo perfil** para agregar un nuevo perfil.

   ![Perfil nuevo](/help/assets/admin-console-product-profiles.png)

1. Proporcione la información para establecer una función nueva para [!UICONTROL Cloud Manager].

   * **Nombre del perfil**: el **Nombre del perfil** puede ser cualquier cosa, aunque, para evitar confusiones, se recomienda usar los valores de la columna **Nombre de perfil recomendado**.
   * **Nombre para mostrar**: el **Nombre para mostrar** debe ser el valor técnico definido por [!UICONTROL Cloud Manager] (véase la tabla siguiente).
   * **Grupo de permisos**: puede elegir un grupo de permisos para el perfil (no siempre disponible).

   ![Creación de un nuevo perfil](/help/assets/screen_shot_2018-05-04at171819.png)

   | Función | Nombre para mostrar (obligatorio) | Nombre de perfil recomendado |
   |---|---|---|
   | Propietario del negocio | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager]: función de propietario de la empresa |
   | Administrador de implementación | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager]: función de administrador de implementación |
   | Desarrollador | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager]: función de desarrollador |
   | Administrador de programa | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager]: función de administrador de programas |


1. Haga clic en **Listo** para guardar el nuevo perfil.

## Asignación de perfiles a usuarios o grupos de usuarios {#assign-profiles}

Una vez creados los perfiles de producto, puede asignarles usuarios o grupos de usuarios.

1. Inicie sesión en el Admin Console en [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

1. En Admin Console, elija la pestaña **Usuarios**.

   ![Pestaña Usuarios](/help/assets/admin-console-users.png)

1. Haga clic en **Usuarios** en el panel de navegación izquierdo y, a continuación, haga clic en un usuario para modificarlo.

1. Haga clic en el botón de los tres puntos de la sección **Productos** y seleccione **Editar**.

   ![Editar usuario](/help/assets/admin-console-edit-user.png)

1. En el cuadro de diálogo **Editar productos y grupos de usuarios**, haga clic en el botón más y seleccione los perfiles que desea asignar al usuario.

   * Si el usuario ya está asignado a las funciones, el botón más es un botón de edición (un lápiz), pero funciona del mismo modo.

   ![Editar productos y grupos de usuarios](/help/assets/admin-console-edit-products-and-user-groups.png)

1. Haga clic en **Guardar** para guardar los perfiles en el usuario.

Repita los mismos pasos para asignar perfiles a grupos de usuarios, pero seleccione **Grupos de usuarios** del panel de navegación izquierdo de la pestaña **Usuarios**. Haga clic en un grupo de usuarios y seleccione la ficha **Perfiles de productos asignados** y haga clic en **Asignar perfil de productos** para asignar perfiles.

![Asignar perfiles al grupo](/help/assets/admin-console-edit-user-groups.png)
