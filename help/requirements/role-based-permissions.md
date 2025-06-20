---
title: Permisos basados en funciones
description: Obtenga información sobre los permisos preconfigurados basados en funciones de Cloud Manager para administrar el acceso a los recursos de la nube.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 99%

---


# Permisos basados en funciones {#role-based-permissions}

[!UICONTROL Cloud Manager] tiene funciones preconfiguradas con los permisos adecuados. Por ejemplo, un desarrollador elabora códigos y tiene permiso para insertarlos en el repositorio de Git. Un propietario de una empresa tiene diferentes permisos que les permiten definir los indicadores clave de rendimiento (KPI) y aprobar implementaciones.

>[!NOTE]
>
>En esta documentación se describen los permisos basados en funciones para Cloud Manager para Adobe Managed Services (AMS).
>
>La documentación equivalente para AEM as a Cloud Service se puede encontrar en el documento [Introducción a Cloud Manager](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction#role-based-permissions) en la documentación de AEM as a Cloud Service.

## Funciones de los usuarios {#user-roles}

La administración de funciones para [!UICONTROL Cloud Manager] se realiza utilizando la [Admin Console](https://helpx.adobe.com/es/enterprise/using/admin-console.html). Cualquier usuario de [!UICONTROL Cloud Manager] debe ser miembro de la organización IMS del cliente y tener el contexto del producto de Adobe Managed Services. Las suscripciones a funciones específicas se proporcionan añadiendo el usuario a un perfil de producto de [!UICONTROL Cloud Manager] en Admin Console.

Para obtener más información sobre cómo configurar las funciones, consulte el documento [Configuración de usuarios y funciones](/help/requirements/users-and-roles.md).

La siguiente tabla enumera las funciones que puede asignar en Admin Console.

| Función [!UICONTROL Cloud Manager] | Descripción |
|---|---|
| Propietario del negocio | Este es el usuario principal que completa la configuración inicial de [!UICONTROL Cloud Manager] y es responsable de definir los indicadores clave de rendimiento (KPI), aprobar implementaciones de producción y anular errores importantes de tres niveles cuando sea necesario. |
| Autor de contenido | El usuario generalmente no interactúa con Cloud Manager, pero puede usar el conmutador del programa Cloud Manager (al navegar desde Experience Cloud) para acceder a Adobe Experience Manager (AEM). |
| Ingeniero de éxito del cliente (Customer Success Engineer) | El usuario admite principalmente el éxito del cliente de AMS y se involucra con [!UICONTROL Cloud Manager] para ejecutar implementaciones. Estas implementaciones requieren la supervisión de un ingeniero de éxito del cliente (Customer Success Engineer, CSE) de Adobe. |
| Administrador de implementación | Este usuario gestiona las operaciones de implementación mediante [!UICONTROL Cloud Manager] para ejecutar implementaciones de fase y producción, puede aprobar errores importantes de tres niveles cuando sea necesario y tiene acceso al repositorio de Git. |
| Desarrollador | Este usuario desarrolla y prueba el código de aplicación personalizado, que utiliza principalmente [!UICONTROL Cloud Manager] para ver el estado de implementación y tiene acceso de confirmación al repositorio de Git. |
| Administrador de programa | Este usuario utiliza [!UICONTROL Cloud Manager] para realizar la configuración del equipo, revisar el estado, ver los indicadores clave de rendimiento (KPI) y aprobar errores importantes de tres niveles cuando sea necesario. |

## Permisos de usuario {#user-permissions}

Cada una de las funciones tiene permisos preconfigurados específicos asociados. Esta tabla enumera los permisos disponibles y las funciones que pueden ejecutarlos.

| Permiso | Descripción | Propietario del negocio | Administrador de implementación | Administrador de programa | Desarrollador | CSE |
| --- | --- | --- | --- | --- | --- | --- |
| `Read the Application` | Leer indicadores clave de rendimiento (KPI) de programa | x | x | x | x | x |
| `Write Application` | Configuración o edición del programa | x | | | | |
| `Add Program` | Agregar programa nuevo | x |  |  |  |  |
| `Read Environment` | Consulte los detalles del entorno | x | x | x | x | x |
| `Create Execution` | Iniciar canalización | x | x | x | | |
| `Read Execution` | Consulte Estado de ejecución | x | x | x | x | x |
| `Resume Execution` | Capacidad para reanudar la ejecución cuando está en pausa | x | x | x | | x |
| `Execution Approve Deploy to Production` | Proporcionar aprobación de lanzamiento | x | x | x | | |
| `Execution Schedule Deploy to Production` | Programar implementación de producción | x | x | x | | x |
| `Execution Deploy to Production` | Implementar la aplicación en producción cuando está en pausa para la supervisión de CSE |  |  |  |  | x |
| `Execution Cancel` | Cancelar ejecución actual |  |  | x |  |  |
| `Execution Override Quality Gate Failures` | Aprobar errores importantes de la puerta de acceso de calidad | x | x | x |  |  |
| `Pipeline Create` | Configurar/editar canalización |  | x |  |  |  |
| `Pipeline Read` | Consulte detalles de canalización | x | x | x | x | x |
| `Pipeline Write` | Configurar/editar canalización |  | x |  |  |  |
| P`ipeline Modify Approval` | Permite editar la opción Propietario empresarial |  | x |  |  |  |
| `Pipeline Modify Managed Deployment` | Permite editar la opción de supervisión de CSE |  | x |  |  |  |
| `Pipeline Delete` | Permite la eliminación de la canalización |  | x |  |  |  |
| `Step Read` | Consulte los resultados de las métricas de calidad de los pasos | x | x | x | x | x |
| `Generate Personal Access Token` | Acceder a Git |  | x |  | x |  |

<!-- CQDOC-22080 | Download log files  |  |  | x |  | x |  | -->

Para obtener más información sobre cómo configurar sus usuarios, consulte [Configuración de usuarios y funciones](/help/requirements/users-and-roles.md).

>[!TIP]
>
>También hay disponibles perfiles de permisos personalizados y configurables. Consulte [Permisos personalizados](/help/using/custom-permissions.md) para obtener más información.
