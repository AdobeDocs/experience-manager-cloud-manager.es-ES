---
title: Agregar usuarios y funciones
seo-title: Agregar usuarios y funciones
description: Obtenga información sobre los usuarios y las funciones y cómo usar Admin Console para crear un perfil
seo-description: Puede asignar funciones específicas agregando el usuario a un Perfil de producto de Cloud Manager en el Admin Console. Siga esta sección para obtener más información.
uuid: fa204c28-83df-48bb-8360-e158f080dee7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: 1b421993-22c3-4de0-ba64-c1080d07ad5e
translation-type: tm+mt
source-git-commit: 2dda85baa5e7ed9bfd8933df3580ec6fc3c210fd
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 32%

---


# Agregar usuarios y funciones {#add-users-and-roles}

Muchas funciones de [!UICONTROL Cloud Manager] requieren permisos específicos para funcionar. Por ejemplo, solo algunos usuarios pueden establecer los Indicadores de rendimiento clave (KPI) para un programa. Estos permisos se agrupan lógicamente en funciones.

[!UICONTROL Cloud Manager] actualmente define cuatro funciones para los usuarios que rigen la disponibilidad de funciones específicas:

* Propietario del negocio
* Administrador de programa
* Administrador de implementación
* Desarrollador

>[!CAUTION]
>
>Para utilizar [!UICONTROL Cloud Manager], debe tener un Adobe ID y el contexto de producto de los servicios administrados de Adobe.

## Definiciones de roles {#role-definitions}

>[!NOTE]
>
>La persona desarrolladora en Admin Console no está relacionada con la función de desarrollador en [!UICONTROL Cloud Manager].

La siguiente tabla resume los roles:

| [!UICONTROL Cloud Manager] Funciones | Descripción |
|--- |--- |
| Propietario del negocio | Responsable de definir KPI, aprobar implementaciones de producción y anular errores importantes de tres niveles. |
| Administrador de programa | Utiliza [!UICONTROL Cloud Manager] para realizar la configuración del equipo, revisar los KPI de estado y vista. Puede aprobar errores importantes de tres niveles. |
| Administrador de implementación | Gestiona las operaciones de implementación. Utiliza [!UICONTROL Cloud Manager] para ejecutar implementaciones de etapa/producción. Puede editar las tuberías de CD/CI. Puede aprobar errores importantes de tres niveles. Puede obtener acceso al repositorio Git. |
| Desarrollador | Desarrolla y prueba el código de aplicación personalizado. Principalmente utiliza [!UICONTROL Cloud Manager] para el estado de vista. Puede obtener acceso al repositorio Git para la confirmación de código. |
| Ingeniero de éxito del cliente | Generalmente admite el éxito del cliente para los clientes de AMS. Interactúa con [!UICONTROL Cloud Manager] para ejecutar implementaciones que requieren supervisión de CSE. |
| Autor de contenido | Generalmente no interactúa con [!UICONTROL Cloud Manager]. Puede utilizar [!UICONTROL Cloud Manager] Programa Switcher (habiendo navegado desde [!UICONTROL Experience Cloud]) para acceder a AEM. |

## Uso de Admin Console para crear un Perfil {#using-admin-console-to-create-a-profile}

Las funciones se administran para [!UICONTROL Cloud Manager] desde el Adobe Admin Console. Los miembros de roles específicos se proporcionan agregando el usuario a un [!UICONTROL Cloud Manager] Perfil de productos en Admin Console.

Puede asignar miembros de funciones específicas agregando el usuario a un perfil de producto[!UICONTROL Cloud Manager] de **** en Adobe Admin Console, una ubicación central para administrar las autorizaciones de Adobe en toda la organización. Para obtener más información sobre Adobe Admin Console, consulte la documentación de [Admin Console](https://helpx.adobe.com/es/enterprise/using/admin-console.html).

>[!NOTE]
>
>Para acceder a la consola de administración y configurar su equipo (usuarios y funciones), abra un navegador y visite [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

Para proporcionar los permisos adecuados basados en funciones a los usuarios de [!UICONTROL Cloud Manager], un administrador de la **organización** del cliente debe crear nuevos perfiles de producto en el contexto de producto de [!UICONTROL AEM Managed Services].

Para proporcionar a los usuarios [!UICONTROL Cloud Manager] los permisos adecuados basados en roles, como administrador debe crear cuatro nuevos Perfiles de producto en el contexto de producto [!UICONTROL AEM Managed Services] correspondiente a cada una de las cuatro funciones [!UICONTROL Cloud Manager]:

* Propietario del negocio
* Administrador de implementación
* Desarrollador
* Administrador de programa

Puede crear o agregar usuarios o grupos a estos Perfiles de producto con el [Admin Console](https://adminconsole.adobe.com/) para [!UICONTROL Cloud Manager], como se muestra en la figura siguiente:

1. Inicie sesión en Admin Console y haga clic en **Nuevo Perfil** para agregar un nuevo perfil.

   ![](assets/admin_console_roles-1.png)

1. Rellene los campos para configurar una nueva función para [!UICONTROL Cloud Manager].

   Introduzca el **Nombre del perfil** y **Nombre para mostrar** para crear un nuevo perfil. Además, puede seleccionar un **grupo de permisos** para el perfil.

   Haga clic en **Listo** para completar el paso de creación de perfil.

   >[!NOTE]
   >
   >Al crear estos perfiles de producto, el **Nombre para mostrar** debe ser el valor técnico definido por [!UICONTROL Cloud Manager] (consulte la tabla siguiente). El **nombre del perfil** puede ser cualquier cosa, aunque para evitar confusiones, se recomienda usar los valores de la columna *Nombre del perfil* recomendado que aparece a continuación. Para ello, al crear el perfil de producto, desactive la casilla **Igual que el nombre de perfil** y especifique el valor correspondiente como **Nombre para mostrar**.

   | **Función** | **Nombre para mostrar (obligatorio)** | **Nombre de Perfil recomendado** |
   |---|---|---|
   | Propietario del negocio | CM_BUSINESS_OWNER_ROLE_PERFIL | [!UICONTROL Cloud Manager] - Función de propietario del negocio |
   | Administrador de implementación | CM_DEPLOYMENT_MANAGER_ROLE_PERFIL | [!UICONTROL Cloud Manager] - Función de administrador de implementación |
   | Desarrollador | CM_DEVELOPER_ROLE_PERFIL | [!UICONTROL Cloud Manager] - Función de desarrollador |
   | Administrador de programa | CM_PROGRAMA_MANAGER_ROLE_PERFIL | [!UICONTROL Cloud Manager] - Función de administrador de Programas |

   ![](assets/screen_shot_2018-05-04at171819.png)

1. Una vez creado el perfil del producto, puede agregar usuarios (o grupos) a estos Perfiles del producto.

   ![](assets/image2018-4-9_15-19-26.png)

   ![](assets/image2018-4-9_15-16-47.png)

