---
title: Agregar usuarios y funciones
seo-title: Agregar usuarios y funciones
description: nulo
seo-description: Puede asignar grupos de funciones específicos agregando el usuario a un perfil de producto de Cloud Manager en Admin Console. Siga esta sección para obtener más información.
uuid: fa 204 c 28-83 df -48 bb -8360-e 158 f 080 dee 7
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requisitos
discoiquuid: 1 b 421993-22 c 3-4 de 0-ba 64-c 1080 d 07 ad 5 e
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Agregar usuarios y funciones{#add-users-and-roles}

Muchas funciones en [!UICONTROL Cloud Manager] requieren permisos específicos para funcionar. Por ejemplo, sólo determinados usuarios pueden establecer los indicadores de rendimiento clave (KPI) de un programa. Estos permisos se agrupan lógicamente en funciones.

[!UICONTROL Cloud Manager] actualmente define cuatro roles para los usuarios que rigen la disponibilidad de características específicas:

* Propietario comercial
* Administrador de programas
* Administrador de implementación
* Desarrollador

>[!CAUTION]
>
>Para usar [!UICONTROL Cloud Manager], debe tener un Adobe ID y el contexto de producto de los servicios gestionados de Adobe.

## Definiciones de función {#role-definitions}

>[!NOTE]
>
>La persona Programador de Admin Console no está relacionada con la función para desarrolladores en [!UICONTROL Cloud Manager].

En la tabla siguiente se resumen las funciones:

| [!UICONTROL Cloud Manager] Funciones | Descripción |
|--- |--- |
| Propietario comercial | Responsable de definir KPI, aprobar implementaciones de producción y anular errores importantes de 3 niveles. |
| Administrador de programas | Utiliza [!UICONTROL Cloud Manager] para realizar configuraciones de equipo, revisar el estado y ver KPI. Puede aprobar errores importantes de 3 niveles. |
| Administrador de implementación | Gestiona las operaciones de implementación. Utiliza [!UICONTROL Cloud Manager] para ejecutar implementaciones de etapas y producción. Puede editar los canales de CI/CD. Puede aprobar errores importantes de 3 niveles. Puede obtener acceso al repositorio de Git. Comuníquese con el representante de CSE/AMS para solicitarlo. |
| Desarrollador | Desarrolla y prueba el código de aplicación personalizado. Utiliza principalmente [!UICONTROL Cloud Manager] para ver el estado. Debe obtener acceso al repositorio de Git para la transferencia de código. Comuníquese con el representante de CSE/AMS al agregar un usuario con esta función para otorgar acceso al repositorio de Git. |
| Ingeniero de éxito del cliente | Generalmente admite el éxito de los clientes para los clientes de AMS. Interactúa con [!UICONTROL Cloud Manager] el objetivo de ejecutar implementaciones que requieran supervisión CSE. |
| Autor de contenido | Generalmente no interactúa [!UICONTROL Cloud Manager]con. Puede utilizar [!UICONTROL Cloud Manager] el Conmutador de programa (que ha navegado de [!UICONTROL Experience Cloud]) para acceder a AEM. |

>[!NOTE]
>
>El CSE administra el repositorio [!UICONTROL Cloud Manager] de Git. Póngase en contacto con ellos para agregar y eliminar usuarios.
>
>Si un usuario recién agregado requiere acceso al repositorio de Git, deberá ponerse en contacto con su representante de CSE/AMS para que tenga acceso. Estas funciones no proporcionan acceso automático al repositorio de Git. Solo puede tener un máximo de 3 usuarios con acceso al repositorio Git.

## Uso de la Consola de administración para crear un perfil {#using-admin-console-to-create-a-profile}

Las funciones se administran desde [!UICONTROL Cloud Manager] Adobe Admin Console. Las membresías de función específicas se proporcionan agregando el usuario a un perfil [!UICONTROL Cloud Manager] de producto en la Consola de administración.

Puede asignar grupos de funciones específicos agregando el usuario a un [!UICONTROL Cloud Manager]**perfil** de producto en Adobe Admin Console, una ubicación central para gestionar sus autorizaciones de Adobe en toda la organización. Para obtener más información sobre Adobe Admin Console, consulte la documentación de [Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html).

>[!NOTE]
>
>Para acceder a la consola de administración y configurar su equipo (usuarios y funciones), abra un navegador y visite [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

Para proporcionar los permisos adecuados basados en roles a [!UICONTROL Cloud Manager] los usuarios, un administrador de **la organización** del cliente, debe crear nuevos perfiles de producto bajo el contexto [!UICONTROL AEM Managed Services] de producto.

Para proporcionar los permisos adecuados basados en roles a [!UICONTROL Cloud Manager] los usuarios, como administrador debe crear cuatro nuevos perfiles de producto en el contexto [!UICONTROL AEM Managed Services] de producto correspondiente a cada una de [!UICONTROL Cloud Manager] las cuatro funciones:

* Propietario comercial
* Administrador de implementación
* Desarrollador
* Administrador de programas

Puede crear o agregar usuarios o grupos a estos perfiles de producto con [Admin Console](https://adminconsole.adobe.com/) para [!UICONTROL Cloud Manager], como se muestra en la figura siguiente:

1. Inicie sesión en la Consola de administración y haga clic **en Nuevo perfil** para agregar un nuevo perfil.

   ![](assets/admin_console_roles-1.png)

1. Complete los campos para configurar una nueva función para [!UICONTROL Cloud Manager].

   Introduzca **Nombre de perfil**, **Nombre para mostrar** para crear un nuevo perfil. Además, puede seleccionar un **grupo de permisos** para el perfil.

   Haga clic **en Hecho** para completar el paso de creación de perfiles.

   >[!NOTE]
   >
   >Al crear estos perfiles de producto, el nombre **para mostrar** debe ser el valor técnico definido por [!UICONTROL Cloud Manager] (consulte la tabla siguiente). El nombre **del perfil** puede ser cualquiera, aunque para evitar confusiones se recomienda utilizar los valores en la columna Nombre de perfil *recomendado* a continuación. Para ello, al crear el perfil de producto, desmarque la **opción Igual que el nombre del perfil** y especifique el valor correspondiente como nombre **para mostrar**.

   | **Función** | **Nombre para mostrar (obligatorio)** | **Nombre de perfil recomendado** |
   |---|---|---|
   | Propietario comercial | CM_ BUSINESS_ OWNER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] - Rol del propietario comercial |
   | Administrador de implementación | CM_ DEPLOYMENT_ MANAGER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] - Función Administrador de implementación |
   | Desarrollador | CM_ DEVELOPER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] - Función de desarrollador |
   | Administrador de programas | CM_ PROGRAM_ MANAGER_ ROLE_ PROFILE | [!UICONTROL Cloud Manager] - Rol del Administrador de programa |

   ![](assets/screen_shot_2018-05-04at171819.png)

1. Una vez creado el perfil de producto, puede agregar usuarios (o grupos) a estos perfiles de producto.

   ![](assets/image2018-4-9_15-19-26.png)

   ![](assets/image2018-4-9_15-16-47.png)

