---
title: Agregar usuarios y funciones
description: Aprenda a utilizar Admin Console para agregar usuarios y funciones y crear perfiles.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: ht
source-wordcount: '536'
ht-degree: 100%

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

| Función de [!UICONTROL Cloud Manager] | Descripción |
|--- |--- |
| Propietario del negocio | Este usuario es responsable de definir los indicadores clave de rendimiento (KPI), aprobar implementaciones de producción y anular errores importantes de tres niveles cuando sea necesario. |
| Administrador de programa | Este usuario emplea [!UICONTROL Cloud Manager] para realizar la configuración del equipo, revisar el estado y ver los indicadores clave de rendimiento (KPI) y puede aprobar errores importantes de tres niveles cuando sea necesario. |
| Administrador de implementación | Este usuario gestiona las operaciones de implementación y utiliza [!UICONTROL Cloud Manager] para ejecutar implementaciones de ensayo/producción, editar las canalizaciones CI/CD, aprobar errores importantes de tres niveles cuando sea necesario y puede acceder al repositorio de Git. |
| Desarrollador | Este usuario desarrolla y prueba el código de aplicación personalizado y emplea principalmente [!UICONTROL Cloud Manager] para ver el estado de implementación y puede acceder al repositorio de Git para confirmaciones de código. |
| Ingeniero de éxito del cliente (Customer Success Engineer) | Este usuario suele admitir el éxito de los clientes para los clientes de AMS e interactúa con [!UICONTROL Cloud Manager] para ejecutar implementaciones que requieran supervisión del ingeniero de éxito del cliente (CSE). |
| Autor de contenido | Este usuario generalmente no interactúa con [!UICONTROL Cloud Manager], pero puede utilizar el conmutador de programas [!UICONTROL Cloud Manager] para acceder a AEM. |

>[!NOTE]
>
>El personaje ficticio del desarrollador en Admin Console no está relacionado con la función de desarrollador en [!UICONTROL Cloud Manager].

## Uso de Admin Console para crear un perfil {#using-admin-console-to-create-a-profile}

Las funciones de [!UICONTROL Cloud Manager] se administran desde Admin Console. Las suscripciones a funciones específicas se proporcionan añadiendo el usuario a un perfil de producto de [!UICONTROL Cloud Manager].

Admin Console es una ubicación central para administrar los derechos de Adobe en toda la organización. Para obtener más información sobre Adobe Admin Console, consulte la documentación de [Admin Console.](https://helpx.adobe.com/es/enterprise/using/admin-console.html)

>[!NOTE]
>
>Para acceder a Admin Console y configurar su equipo (usuarios y funciones), visite [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

Para proporcionar los permisos adecuados basados en funciones a los usuarios de [!UICONTROL Cloud Manager], un administrador de la organización del cliente debe crear perfiles de producto nuevos en el contexto de producto de [!UICONTROL AEM Managed Services] correspondiente a cada una de las cuatro funciones de [!UICONTROL Cloud Manager]:

* Propietario del negocio
* Administrador de implementación
* Desarrollador
* Administrador de programa

Puede crear o agregar usuarios/grupos a estos perfiles de producto con Admin Console.

1. Inicie sesión en Admin Console y haga clic en **Nuevo perfil** para agregar un perfil nuevo.

   ![Perfil nuevo](/help/assets/admin_console_roles-1.png)

1. Proporcione la información para establecer una función nueva para [!UICONTROL Cloud Manager].

   * **Nombre de perfil**
   * **Nombre para mostrar**
   * **Grupo de permisos**

1. Haga clic en **Listo** para completar el paso de creación de perfiles.

Al crear perfiles de producto, el **Nombre para mostrar** debe ser el valor técnico definido por [!UICONTROL Cloud Manager] (consulte la tabla siguiente). El **Nombre del perfil** puede ser cualquier cosa, aunque, para evitar confusiones, se recomienda usar los valores de la columna **Nombre del perfil recomendado**. Para ello, al crear el perfil de producto, desactive la casilla **Igual que el nombre de perfil** y especifique el valor correspondiente como **Nombre para mostrar**.

| **Función** | **Nombre para mostrar (obligatorio)** | **Nombre de perfil recomendado** |
|---|---|---|
| Propietario del negocio | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager]: función Propietario empresarial |
| Administrador de implementación | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager]: función Administrador de implementación |
| Desarrollador | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager]: función Desarrollador |
| Administrador de programa | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager]: función Administrador de programas |

![Creación de un nuevo perfil](/help/assets/screen_shot_2018-05-04at171819.png)

Una vez creado el perfil de producto, puede agregar usuarios (o grupos) a estos perfiles de producto.

![Edición del usuario](/help/assets/image2018-4-9_15-19-26.png)

![Grupos de usuarios](/help/assets/image2018-4-9_15-16-47.png)
