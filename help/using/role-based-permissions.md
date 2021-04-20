---
title: Permisos basados en roles
description: Siga esta página para obtener más información sobre los permisos basados en roles.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
feature: User Roles
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 19%

---


# Permisos basados en roles {#role-based-permissions}

[!UICONTROL Cloud Manager] tiene funciones preconfiguradas con los permisos adecuados. Por ejemplo, un desarrollador desarrolla código y tiene permiso para insertar el código en el **Repositorio de Git**. Alternativamente, un propietario de una empresa tiene diferentes permisos que les permiten definir los indicadores de rendimiento clave (KPI) y aprobar las implementaciones.

## Roles del usuario {#user-roles}

La administración de funciones para [!UICONTROL Cloud Manager] se realiza dentro de [Adobe Admin Console](https://helpx.adobe.com/es/enterprise/using/admin-console.html). Cualquier usuario de [!UICONTROL Cloud Manager] debe ser miembro de la organización IMS del cliente y tener el contexto de producto de Adobe Managed Services. Las suscripciones a funciones específicas se proporcionan añadiendo el usuario a un [!UICONTROL Cloud Manager] Perfil de producto en el Admin Console.

Para obtener más información sobre cómo configurar las funciones, consulte [Configuración de usuarios y funciones](setting-up-users-and-roles.md).

La siguiente lista de tabla define las posibles funciones que puede asignar en el Admin Console.

| **[!UICONTROL Cloud Manager]Función** | **Descripción** |
|---|---|
| Propietario del negocio | Usuario principal que completa la configuración inicial [!UICONTROL Cloud Manager]. Responsable de definir KPI, aprobar implementaciones de producción y anular errores importantes de tres niveles. |
| Administrador de programa | Utiliza [!UICONTROL Cloud Manager] para realizar la configuración del equipo, revisar el estado y ver los KPI. Puede aprobar errores importantes de tres niveles. |
| Administrador de implementación | Gestiona las operaciones de implementación. Utiliza [!UICONTROL Cloud Manager] para ejecutar implementaciones de fase y producción. Puede aprobar errores importantes de tres niveles. Tiene acceso al repositorio de Git. |
| Desarrollador | Desarrolla y prueba el código de aplicación personalizado. Principalmente utiliza [!UICONTROL Cloud Manager] para ver el estado. Tiene acceso de confirmación al repositorio de Git. |
| Ingeniero de éxito del cliente | Generalmente admite el éxito de los clientes para los clientes de AMS. Interactúa con [!UICONTROL Cloud Manager] con el fin de ejecutar implementaciones que requieren la supervisión del ingeniero de éxito del cliente (CSE). |
| Autor de contenido | Generalmente no interactúa con [!UICONTROL Cloud Manager]. Este usuario puede utilizar el [!UICONTROL Cloud Manager] conmutador de programas (habiendo navegado desde [!UICONTROL Experience Cloud]) para acceder a Adobe Experience Manager (AEM). |

## Permisos de usuario {#user-permissions}

Cada una de las funciones tiene permisos específicos, tareas preconfiguradas o permisos asociados a cada función. En esta tabla se enumeran las funciones disponibles y las funciones que pueden ejecutar la función.

Para obtener más información sobre cómo configurar los usuarios, consulte [Configuración de usuarios y funciones](setting-up-users-and-roles.md).

| Permiso | Descripción | Propietario del negocio | Administrador de implementación | Administrador de programa | Desarrollador | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Leer aplicación | Lea KPI de programa. | x | x | x | x | x |
| Escribir aplicación | Configuración o edición del programa. | x |  |  |  |  |
| Agregar programa | Agregar nuevo programa. | x |  |  |  |  |
| Entorno de lectura | Consulte Detalles de entorno . | x | x | x | x | x |
| Crear ejecución | Iniciar canalización. | x | x | x |  |  |
| Leer ejecución | Consulte Estado de ejecución. | x | x | x | x | x |
| Reanudar ejecución | Se puede reanudar la ejecución cuando se pone en pausa. | x | x | x |  | x |
| Ejecución Aprobar implementación en producción | Proporcionar aprobación de GoLive. | x | x | x |  |  |
| Implementación de programación de ejecución en producción | Programar la implementación de producción. | x | x | x |  | x |
| Implementación de ejecución en producción | Implemente la aplicación en producción cuando esté en pausa para la supervisión de CSE. |  |  |  |  | x |
| Cancelación de ejecución | Cancelar ejecución actual. |  |  | x |  |  |
| Errores de portal de calidad de anulación de ejecución | Aprobar Errores Importantes De Puerta De Calidad. | x | x | x |  |  |
| Creación de canalización | Configurar / Editar canalización. |  | x |  |  |  |
| Lectura de canalización | Consulte Detalles de canalización. | x | x | x | x | x |
| Escritura de canalización | Configurar / Editar canalización. |  | x |  |  |  |
| Aprobación de modificación de canalización | Permite editar la opción Propietario empresarial . |  | x |  |  |  |
| Implementación administrada de modificación de canalización | Permite editar la opción Supervisión de CSE. |  | x |  |  |  |
| Eliminación de canalización | Permite eliminar una canalización. |  | x |  |  |  |
| Lectura de paso | Consulte los resultados de las métricas de calidad de los pasos. | x | x | x | x | x |
| Generar token de acceso personal | Acceda a Git. |  | x |  | x |  |

