---
title: Agregar usuarios y funciones
seo-title: Agregar usuarios y funciones
description: nulo
seo-description: Puede asignar pertenencias a funciones específicas agregando el usuario a un perfil de producto de Cloud Manager en Admin Console. Siga esta sección para obtener más información.
uuid: fa204c28-83df-48bb-8360-e158f080dee7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requisitos
discoiquuid: 1b421993-22c3-4de0-ba64-c1080d07ad5e
translation-type: tm+mt
source-git-commit: 73203dca7b20570103af429cf933610941b787be

---


# Agregar usuarios y funciones{#add-users-and-roles}

Muchas funciones de [!UICONTROL Cloud Manager] requieren permisos específicos para funcionar. Por ejemplo, solo algunos usuarios pueden establecer los Indicadores de rendimiento clave (KPI) para un programa. Estos permisos se agrupan lógicamente en funciones.

[!UICONTROL Cloud Manager] actualmente define cuatro funciones para los usuarios que rigen la disponibilidad de funciones específicas:

* Propietario del negocio
* Administrador de programas
* Administrador de implementación
* Desarrollador

>[!CAUTION]
>
>Para usar [!UICONTROL Cloud Manager], debe tener un Adobe ID y el contexto de producto de los servicios administrados de Adobe.

## Definiciones de funciones {#role-definitions}

>[!NOTE]
>
>La persona desarrolladora de Admin Console no está relacionada con la función de desarrollador de [!UICONTROL Cloud Manager].

La siguiente tabla resume los roles:

| [!UICONTROL Cloud Manager] Funciones | Descripción |
|--- |--- |
| Propietario del negocio | Responsable de definir KPI, aprobar implementaciones de producción y anular errores importantes de tres niveles. |
| Administrador de programas | Utiliza [!UICONTROL Cloud Manager] para realizar la configuración del equipo, revisar el estado y ver KPI. Puede aprobar errores importantes de tres niveles. |
| Administrador de implementación | Gestiona las operaciones de implementación. Utiliza [!UICONTROL Cloud Manager] para ejecutar implementaciones de fase/producción. Puede editar las tuberías de CD/CI. Puede aprobar errores importantes de tres niveles. Puede obtener acceso al repositorio Git. Comuníquese con el representante de CSE/AMS para solicitarlo. |
| Desarrollador | Desarrolla y prueba el código de aplicación personalizado. Se utiliza principalmente [!UICONTROL Cloud Manager] para ver el estado. Debe obtener acceso al repositorio Git para la confirmación de código. Comuníquese con el representante de CSE/AMS cuando agregue un usuario con esta función para otorgar acceso al repositorio de Git. |
| Ingeniero de éxito del cliente | Generalmente admite el éxito del cliente para los clientes de AMS. Interactúa con [!UICONTROL Cloud Manager] el fin de ejecutar despliegues que requieren supervisión de CSE. |
| Autor de contenido | Generalmente no interactúa con [!UICONTROL Cloud Manager]. Puede utilizar [!UICONTROL Cloud Manager] el conmutador de programas (después de haber navegado desde [!UICONTROL Experience Cloud]) para acceder a AEM. |

>[!NOTE]
>
>Su CSE administra el acceso al repositorio [!UICONTROL Cloud Manager] Git. Póngase en contacto con ellos para agregar y eliminar usuarios.
>
>Si un usuario recientemente agregado necesita acceder al repositorio Git, deberá ponerse en contacto con su representante de CSE/AMS para que se le conceda el acceso. Estas funciones no proporcionan acceso automático al repositorio Git. Sólo puede tener un máximo de 3 usuarios con acceso al repositorio Git.

## Uso de la Consola de administración para crear un perfil {#using-admin-console-to-create-a-profile}

Las funciones se administran desde [!UICONTROL Cloud Manager] Adobe Admin Console. Los miembros específicos de funciones se proporcionan agregando el usuario a un perfil de [!UICONTROL Cloud Manager] producto en Admin Console.

Puede asignar miembros de funciones específicas agregando el usuario a un perfil [!UICONTROL Cloud Manager] de **producto** en Adobe Admin Console, una ubicación central para administrar los derechos de Adobe en toda la organización. Para obtener más información sobre Adobe Admin Console, consulte la documentación de [Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html).

>[!NOTE]
>
>Para acceder a la consola de administración y configurar su equipo (usuarios y funciones), abra un navegador y visite [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

Para proporcionar a [!UICONTROL Cloud Manager] los usuarios los permisos adecuados basados en roles, un administrador de la **organización** del cliente debe crear nuevos perfiles de producto en el contexto [!UICONTROL AEM Managed Services] de producto.

Para proporcionar a los usuarios los permisos adecuados basados en roles, como administrador debe crear cuatro nuevos perfiles de producto en el contexto [!UICONTROL Cloud Manager] de producto correspondientes a cada una de las cuatro [!UICONTROL AEM Managed Services] [!UICONTROL Cloud Manager] funciones:

* Propietario del negocio
* Administrador de implementación
* Desarrollador
* Administrador de programas

Puede crear o agregar usuarios o grupos a estos perfiles de producto con la Consola [de](https://adminconsole.adobe.com/) administración de [!UICONTROL Cloud Manager], como se muestra en la figura siguiente:

1. Inicie sesión en Admin Console y haga clic en **Nuevo perfil** para agregar un nuevo perfil.

   ![](assets/admin_console_roles-1.png)

1. Rellene los campos para configurar una nueva función [!UICONTROL Cloud Manager].

   Introduzca el nombre **** del perfil y **el nombre** para crear un nuevo perfil. Además, puede seleccionar un grupo **de** permisos para el perfil.

   Haga clic en **Listo** para completar el paso de creación del perfil.

   >[!NOTE]
   >
   >Al crear estos perfiles de producto, el **nombre** para mostrar debe ser el valor técnico definido por [!UICONTROL Cloud Manager] (consulte la tabla siguiente). El nombre **del** perfil puede ser cualquier cosa, aunque para evitar confusiones, se recomienda usar los valores de la columna Nombre *del perfil* recomendado que aparece a continuación. Para ello, al crear el perfil de producto, desactive la casilla **Igual que el nombre** de perfil y especifique el valor correspondiente como nombre **de** visualización.

   | **Función** | **Nombre para mostrar (obligatorio)** | **Nombre de perfil recomendado** |
   |---|---|---|
   | Propietario del negocio | CM_BUSINESS_OWNER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Función de propietario del negocio |
   | Administrador de implementación | CM_DEPLOYMENT_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Función de administrador de implementación |
   | Desarrollador | CM_DEVELOPER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Función de desarrollador |
   | Administrador de programas | CM_PROGRAM_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - Función de administrador de programas |

   ![](assets/screen_shot_2018-05-04at171819.png)

1. Una vez creado el perfil de producto, puede agregar usuarios (o grupos) a estos perfiles de producto.

   ![](assets/image2018-4-9_15-19-26.png)

   ![](assets/image2018-4-9_15-16-47.png)

