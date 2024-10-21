---
title: Permisos basados en funciones
description: Obtenga información sobre los permisos preconfigurados basados en funciones de Cloud Manager para administrar el acceso a los recursos de la nube.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 682b142f35bc233bad82b0ddfa69bc0f2d5b5fdb
workflow-type: ht
source-wordcount: '616'
ht-degree: 100%

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
| Ingeniero de éxito del cliente (Customer Success Engineer) | El usuario admite principalmente el éxito de los clientes de AMS y se involucra con [!UICONTROL Cloud Manager] para ejecutar implementaciones. Estas implementaciones requieren la supervisión de un ingeniero de éxito del cliente (Customer Success Engineer, CSE) de Adobe. |
| Administrador de implementación | Este usuario gestiona las operaciones de implementación mediante [!UICONTROL Cloud Manager] para ejecutar implementaciones de fase y producción, puede aprobar errores importantes de tres niveles cuando sea necesario y tiene acceso al repositorio de Git. |
| Desarrollador | Este usuario desarrolla y prueba el código de aplicación personalizado, que utiliza principalmente [!UICONTROL Cloud Manager] para ver el estado de implementación y tiene acceso de confirmación al repositorio de Git. |
| Administrador de programa | Este usuario utiliza [!UICONTROL Cloud Manager] para realizar la configuración del equipo, revisar el estado, ver los indicadores clave de rendimiento (KPI) y aprobar errores importantes de tres niveles cuando sea necesario. |

## Permisos de usuario {#user-permissions}

Cada una de las funciones tiene permisos preconfigurados específicos asociados. Esta tabla enumera los permisos disponibles y las funciones que pueden ejecutarlos.

| Permiso | Descripción | Propietario del negocio | Administrador de implementación | Administrador de programa | Desarrollador | CSE |
| --- | --- | --- | --- | --- | --- | --- |
| Leer la aplicación | Leer indicadores clave de rendimiento (KPI) de programa | x | x | x | x | x |
| Escribir aplicación | Configuración o edición del programa | x | | | | |
| Agregar programa | Agregar programa nuevo | x |  |  |  |  |
| Entorno de lectura | Consulte los detalles del entorno | x | x | x | x | x |
| Crear ejecución | Iniciar canalización | x | x | x | | |
| Leer ejecución | Consulte Estado de ejecución | x | x | x | x | x |
| Reanudar ejecución | Capacidad para reanudar la ejecución cuando está en pausa | x | x | x | | x |
| Implementación de ejecución aprobada en producción | Proporcionar aprobación de lanzamiento | x | x | x | | |
| Implementación de programación de ejecución en producción | Programar implementación de producción | x | x | x | | x |
| Implementación de ejecución en producción | Implementar la aplicación en producción cuando está en pausa para la supervisión de CSE |  |  |  |  | x |
| Cancelación de ejecución | Cancelar ejecución actual |  |  | x |  |  |
| Errores de portal de calidad de anulación de ejecución | Aprobar errores importantes de la puerta de acceso de calidad | x | x | x |  |  |
| Creación de canalización | Configurar/editar canalización |  | x |  |  |  |
| Lectura de canalización | Consulte detalles de canalización | x | x | x | x | x |
| Escritura de canalización | Configurar/editar canalización |  | x |  |  |  |
| Aprobación de modificación de canalización | Permite editar la opción Propietario empresarial |  | x |  |  |  |
| Implementación administrada de modificación de canalización | Permite editar la opción de supervisión de CSE |  | x |  |  |  |
| Eliminación de canalización | Permite la eliminación de la canalización |  | x |  |  |  |
| Lectura de paso | Consulte los resultados de las métricas de calidad de los pasos | x | x | x | x | x |
| Generar token de acceso personal | Acceder a Git |  | x |  | x |  |

<!-- CQDOC-22080 | Download log files  |  |  | x |  | x |  | -->

Para obtener más información sobre cómo configurar sus usuarios, consulte [Configuración de usuarios y funciones](/help/requirements/users-and-roles.md).

>[!TIP]
>
>También hay disponibles perfiles de permisos personalizados y configurables. Consulte [Permisos personalizados](/help/using/custom-permissions.md) para obtener más información.
