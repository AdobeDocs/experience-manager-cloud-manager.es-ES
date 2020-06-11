---
title: Derechos de acceso concedidos
seo-title: Derechos de acceso concedidos en AEM Cloud Manager
description: Obtenga más información sobre Adobe ID y los recursos de Experience Cloud.
seo-description: Siga esta página para obtener más información sobre Adobe ID y los recursos de AEM Experience Cloud.
uuid: 9aa90a99-f049-422e-9e06-b00b843ed98b
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: 072dbc1b-e608-4b1f-b0e8-0e4f88c8ad12
translation-type: tm+mt
source-git-commit: e48f9121423f46f4cf858c4951ad412582020bdb
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 21%

---


# Derechos de acceso concedidos {#access-rights-granted}

## Tipos de identidad de usuario {#user-identity-types}

Como parte del proceso de integración, Adobe creará un identificador de **organización** para su compañía en Adobe Identity Management System (IMS), donde se pueden administrar todos sus usuarios y sus permisos. Cada usuario, que debe ser miembro de esta organización y se le concederá acceso a cualquiera de los [!UICONTROL Experience Cloud] servicios, deberá tener su propio ID **de** Adobe.

Para empezar a usar un Adobe ID, visite [Administrar tipos](https://helpx.adobe.com/enterprise/using/identity.html) de identidad de Adobe para obtener instrucciones detalladas sobre cómo obtener un Adobe ID mediante uno de los tipos de identidad disponibles.

### Usuarios y funciones {#users-and-roles}

Una vez que Adobe haya creado una organización para su empresa, el administrador designado se añadirá como el primer miembro de esta organización. The administrator will be granted the administrator permissions by default, and assigned the [!UICONTROL AEM Managed Services] Product, and one or more [!UICONTROL Cloud Manager] Product Profiles. Visite [Agregar usuarios y funciones](setting-up-users-and-roles.md) para obtener más información sobre cómo configurar y administrar los usuarios de su equipo mediante Admin Console.

Con estos derechos concedidos, el administrador se ha configurado con un inicio de sesión único (con Adobe ID) para acceder a los [!UICONTROL Experience Cloud] servicios, iniciar sesión en los entornos de AEM Cloud y usar [!UICONTROL Cloud Manager].
