---
title: Agregar usuarios y funciones
description: Aprenda a utilizar el Admin Console para añadir usuarios y funciones y crear perfiles.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 16%

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

Esta tabla resume los roles.

| [!UICONTROL Cloud Manager] Función | Descripción |
|--- |--- |
| Propietario del negocio | Este usuario es responsable de definir KPI, aprobar implementaciones de producción y anular errores importantes de 3 niveles cuando sea necesario. |
| Administrador de programa | Este usuario utiliza [!UICONTROL Cloud Manager] para realizar la configuración del equipo, revise el estado, vea los KPI y pueda aprobar errores importantes de 3 niveles cuando sea necesario. |
| Administrador de implementación | Este usuario gestiona las operaciones de implementación y utiliza [!UICONTROL Cloud Manager] para ejecutar implementaciones de ensayo/producción, edite las canalizaciones CI/CD, apruebe errores importantes de 3 niveles cuando sea necesario y pueda acceder al repositorio de Git. |
| Desarrollador | Este usuario desarrolla y prueba el código de aplicación personalizado y utiliza principalmente [!UICONTROL Cloud Manager] para ver el estado de implementación y puede acceder al repositorio de Git para confirmaciones de código. |
| Ingeniero de éxito del cliente | Este usuario suele admitir el éxito de los clientes para los clientes de AMS e interactúa con [!UICONTROL Cloud Manager] para ejecutar despliegues que requieran supervisión de la CSE. |
| Autor de contenido | Este usuario generalmente no interactúa con [!UICONTROL Cloud Manager] pero puede utilizar la variable [!UICONTROL Cloud Manager] alternador de programas para acceder a AEM. |

>[!NOTE]
>
>El perfil de desarrollador en el Admin Console no está relacionado con la función de desarrollador en [!UICONTROL Cloud Manager].

## Uso del Admin Console para crear un perfil {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] las funciones se administran desde el Admin Console . Las suscripciones a funciones específicas se proporcionan añadiendo el usuario a un [!UICONTROL Cloud Manager] perfil de producto.

El Admin Console es una ubicación central para administrar las autorizaciones de Adobe en toda la organización. Para obtener más información sobre Adobe Admin Console, consulte la documentación de [Admin Console.](https://helpx.adobe.com/es/enterprise/using/admin-console.html)

>[!NOTE]
>
>Para acceder a Admin Console y configurar su equipo (usuarios y funciones), visite [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

Para proporcionar los permisos adecuados basados en funciones a [!UICONTROL Cloud Manager] usuarios, un administrador de la organización del cliente debe crear nuevos perfiles de producto en la sección [!UICONTROL AEM Managed Services] contexto de producto correspondiente a cada uno de los cuatro [!UICONTROL Cloud Manager] roles:

* Propietario del negocio
* Administrador de implementación
* Desarrollador
* Administrador de programa

Puede crear o agregar usuarios/grupos a estos perfiles de producto con el Admin Console .

1. Inicie sesión en el Admin Console y haga clic en **Nuevo perfil** para agregar un nuevo perfil.

   ![Nuevo perfil](/help/assets/admin_console_roles-1.png)

1. Proporcione la información para configurar una nueva función para [!UICONTROL Cloud Manager].

   * **Nombre de perfil**
   * **Nombre para mostrar**
   * **Grupo de permisos**

1. Haga clic en **Listo** para completar el paso de creación de perfiles.

Al crear perfiles de producto, la variable **Nombre para mostrar** debe ser el valor técnico definido por [!UICONTROL Cloud Manager] (véase la tabla siguiente). La variable **Nombre del perfil** puede ser cualquier cosa, aunque para evitar confusiones, se recomienda usar los valores de la variable **Nombre de perfil recomendado** para abrir el Navegador. Para ello, al crear el perfil de producto, desactive la casilla **Igual que el nombre de perfil** y especifique el valor correspondiente como **Nombre para mostrar**.

| **Función** | **Nombre para mostrar (obligatorio)** | **Nombre de perfil recomendado** |
|---|---|---|
| Propietario del negocio | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Rol de propietario del negocio |
| Administrador de implementación | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Función de administrador de implementación |
| Desarrollador | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Función de desarrollador |
| Administrador de programa | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - Función de administrador de programas |

![Creación de un nuevo perfil](/help/assets/screen_shot_2018-05-04at171819.png)

Una vez creado el perfil de producto, puede agregar usuarios (o grupos) a estos perfiles de producto.

![Edición del usuario](/help/assets/image2018-4-9_15-19-26.png)

![Grupos de usuarios](/help/assets/image2018-4-9_15-16-47.png)
