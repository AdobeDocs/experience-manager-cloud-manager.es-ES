---
title: Permisos basados en funciones
description: Obtenga información sobre los permisos preconfigurados basados en funciones de Cloud Manager para administrar el acceso a los recursos de la nube.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 522e5fbc650a8159602eb1aeaf42d64f4e23e8b4
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 16%

---


# Permisos basados en roles {#role-based-permissions}

[!UICONTROL Cloud Manager] tiene funciones preconfiguradas con los permisos adecuados. Por ejemplo, un desarrollador desarrolla código y tiene permiso para insertar el código en el repositorio de Git. Un propietario de una empresa tiene diferentes permisos que les permiten definir los indicadores de rendimiento clave (KPI) y aprobar implementaciones.

## Roles del usuario {#user-roles}

Administración de funciones para [!UICONTROL Cloud Manager] se realiza utilizando la variable [Admin Console.](https://helpx.adobe.com/es/enterprise/using/admin-console.html) Cualquier usuario de [!UICONTROL Cloud Manager] debe ser miembro de la organización IMS del cliente y tener el contexto del producto de Adobe Managed Services. Las suscripciones a funciones específicas se proporcionan añadiendo el usuario a un [!UICONTROL Cloud Manager] perfil de producto en el Admin Console.

Para obtener más información sobre cómo configurar las funciones, consulte el documento [Configuración de usuarios y funciones.](/help/requirements/users-and-roles.md)

Esta tabla enumera las funciones que puede asignar en el Admin Console.

| [!UICONTROL Cloud Manager] Función | Descripción |
|---|---|
| Propietario del negocio | Este es el usuario principal que completa la [!UICONTROL Cloud Manager] configure y es responsable de definir los KPI, aprobar implementaciones de producción y anular errores importantes de 3 niveles cuando sea necesario. |
| Administrador de programa | Este usuario utiliza [!UICONTROL Cloud Manager] para realizar la configuración del equipo, revise el estado, vea los KPI y apruebe errores importantes de 3 niveles cuando sea necesario. |
| Administrador de implementación | Este usuario gestiona las operaciones de implementación mediante [!UICONTROL Cloud Manager] para ejecutar implementaciones de fase y producción, puede aprobar errores importantes de 3 niveles cuando sea necesario y tiene acceso al repositorio de Git. |
| Desarrollador | Este usuario desarrolla y prueba el código de aplicación personalizado, que utiliza principalmente [!UICONTROL Cloud Manager] para ver el estado de implementación y tiene acceso de confirmación al repositorio de Git. |
| Ingeniero de éxito del cliente | Este usuario suele admitir el éxito de los clientes para los clientes de AMS e interactúa con [!UICONTROL Cloud Manager] con el fin de ejecutar implementaciones que requieren la supervisión del ingeniero de éxito del cliente (CSE). |
| Autor de contenido | Este usuario generalmente no interactúa con [!UICONTROL Cloud Manager], pero puede usar la variable [!UICONTROL Cloud Manager] programa wwitcher (con navegación desde [!UICONTROL Experience Cloud]) para acceder a Adobe Experience Manager (AEM). |

## Permisos de usuario {#user-permissions}

Cada una de las funciones tiene permisos preconfigurados específicos asociados. Esta tabla enumera los permisos disponibles y las funciones que pueden ejecutarlos.


| Permiso | Descripción | Propietario del negocio | Administrador de implementación | Administrador de programa | Desarrollador | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Leer aplicación | Leer KPI de programa | x | x | x | x | x |
| Escribir aplicación | Configuración o edición del programa | x |  |  |  |  |
| Agregar programa | Agregar nuevo programa | x |  |  |  |  |
| Entorno de lectura | Consulte los detalles del entorno | x | x | x | x | x |
| Crear ejecución | Iniciar canalización | x | x | x |  |  |
| Leer ejecución | Consulte Estado de ejecución | x | x | x | x | x |
| Reanudar ejecución | Puede reanudar la ejecución cuando esté en pausa | x | x | x |  | x |
| Ejecución Aprobar implementación en producción | Proporcionar aprobación de lanzamiento | x | x | x |  |  |
| Implementación de programación de ejecución en producción | Programar implementación de producción | x | x | x |  | x |
| Implementación de ejecución en producción | Implementar la aplicación en producción cuando está en pausa para la supervisión de CSE |  |  |  |  | x |
| Cancelación de ejecución | Cancelar ejecución actual |  |  | x |  |  |
| Errores de portal de calidad de anulación de ejecución | Aprobar errores importantes de la puerta de acceso de calidad | x | x | x |  |  |
| Creación de canalización | Configurar/editar canalización |  | x |  |  |  |
| Lectura de canalización | Consulte detalles de canalización | x | x | x | x | x |
| Escritura de canalización | Configurar/editar canalización. |  | x |  |  |  |
| Aprobación de modificación de canalización | Permite editar la opción Propietario empresarial |  | x |  |  |  |
| Implementación administrada de modificación de canalización | Permite editar la opción de supervisión de CSE |  | x |  |  |  |
| Eliminación de canalización | Permite la eliminación de la canalización |  | x |  |  |  |
| Lectura de paso | Consulte los resultados de las métricas de calidad de los pasos | x | x | x | x | x |
| Generar token de acceso personal | Acceso a Git |  | x |  | x |  |

Para obtener más información sobre cómo configurar los usuarios, consulte el documento [Configuración de usuarios y funciones.](/help/requirements/users-and-roles.md)
