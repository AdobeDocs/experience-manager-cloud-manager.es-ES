---
title: Permisos basados en roles
description: Siga esta página para conocer los permisos basados en roles.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: 9cbe8f58cf04001ba9851ba321f03c7687e58014
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 16%

---


# Permisos basados en roles {#role-based-permissions}

[!UICONTROL Cloud Manager] tiene funciones preconfiguradas con los permisos adecuados. Por ejemplo, un desarrollador desarrolla código y tiene permiso para insertar el código en el **Repositorio de Git**. Como alternativa, un propietario de una empresa tiene permisos diferentes que les permiten definir los Indicadores de rendimiento clave (KPI) y aprobar las implementaciones.

## Roles del usuario {#user-roles}

La administración de roles para [!UICONTROL Cloud Manager] se realiza dentro de [Adobe Admin Console](https://helpx.adobe.com/es/enterprise/using/admin-console.html). Cualquier usuario de [!UICONTROL Cloud Manager] debe ser miembro de la organización IMS del cliente y tener el contexto de producto de los servicios administrados de Adobe. Los miembros específicos del rol se proporcionan agregando al usuario a un [!UICONTROL Cloud Manager] Perfil del producto en el Admin Console.

Para obtener más información sobre cómo configurar sus funciones, consulte [Configuración de usuarios y funciones](setting-up-users-and-roles.md).

La siguiente lista de tabla define las posibles funciones que puede asignar en el Admin Console.

| **[!UICONTROL Cloud Manager]Función** | **Descripción** |
|---|---|
| Propietario del negocio | Usuario principal que completa la configuración inicial [!UICONTROL Cloud Manager]. Responsable de definir KPI, aprobar implementaciones de producción y anular errores importantes de tres niveles. |
| Administrador de programa | Utiliza [!UICONTROL Cloud Manager] para realizar la configuración del equipo, revisar los KPI de estado y vista. Puede aprobar errores importantes de tres niveles. |
| Administrador de implementación | Gestiona las operaciones de implementación. Utiliza [!UICONTROL Cloud Manager] para ejecutar implementaciones de etapa y producción. Puede aprobar errores importantes de tres niveles. Tiene acceso al repositorio Git. |
| Desarrollador | Desarrolla y prueba el código de aplicación personalizado. Principalmente utiliza [!UICONTROL Cloud Manager] para el estado de vista. Tiene acceso de confirmación al repositorio Git. |
| Ingeniero de éxito del cliente | Generalmente admite el éxito del cliente para los clientes de AMS. Interactúa con [!UICONTROL Cloud Manager] con el fin de ejecutar implementaciones que requieren la supervisión del ingeniero de éxito del cliente (CSE). |
| Autor de contenido | Generalmente no interactúa con [!UICONTROL Cloud Manager]. Este usuario puede utilizar el conmutador de Programa [!UICONTROL Cloud Manager] (después de haber navegado desde [!UICONTROL Experience Cloud]) para acceder a Adobe Experience Manager (AEM). |

## Permisos de usuario {#user-permissions}

Cada una de las funciones tiene permisos específicos, tareas preconfiguradas o permisos asociados a cada función. Esta tabla lista las funciones disponibles y las funciones que pueden ejecutar la función.

Para obtener más información sobre cómo configurar los usuarios, consulte [Configuración de usuarios y roles](setting-up-users-and-roles.md).

| Permiso | Descripción | Propietario del negocio | Administrador de implementación | Administrador de programa | Desarrollador | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Leer aplicación | Lea KPI de Programa. | x | x | x | x | x |
| Escribir aplicación | Configuración o edición de programa. | x |  |  |  |  |
| Añadir Programa | Añadir nuevo Programa. | x |  |  |  |  |
| Leer Entorno | Consulte los detalles del Entorno. | x | x | x | x | x |
| Crear ejecución | Canalización de inicio. | x | x | x |  |  |
| Leer ejecución | Consulte el estado de la ejecución. | x | x | x | x | x |
| Reanudar ejecución | Puede reanudar la ejecución cuando esté en pausa. | x | x | x |  | x |
| Ejecución Aprobar implementación en producción | Proporcionar aprobación de GoLive. | x | x | x |  |  |
| Implementación de programación de ejecución en producción | Programar la implementación de producción. | x | x | x |  | x |
| Implementación de ejecución en producción | Implemente la aplicación en producción cuando esté en pausa para la supervisión de CSE. |  |  |  |  | x |
| Cancelación de ejecución | Cancelar la ejecución actual. |  |  | x |  |  |
| Errores de control de calidad de anulación de ejecución | Aprobar Errores Importantes De Puerta De Calidad. | x | x | x |  |  |
| Creación de tubería | Configurar / Editar tubería. |  | x |  |  |  |
| Lectura de tubería | Consulte Detalles de canalización. | x | x | x | x | x |
| Escritura de tubería | Configurar / Editar tubería. |  | x |  |  |  |
| Aprobación de modificación de tubería | Permite editar la opción Propietario de la empresa. |  | x |  |  |  |
| Implementación administrada de modificación de tubería | Permite editar la opción Supervisión de CSE. |  | x |  |  |  |
| Eliminación de tubería | Permite la eliminación de una canalización. |  | x |  |  |  |
| Lectura del paso | Consulte los resultados de las métricas de calidad de los pasos. | x | x | x | x | x |
| Generar Token de acceso personal | Acceso a Git. |  | x |  | x |  |

