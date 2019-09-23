---
title: Seguridad y privacidad
seo-title: Seguridad y privacidad de AEM Cloud Manager
description: Siga esta página para conocer la seguridad y privacidad de sus recursos (código/artefactos).
seo-description: Siga esta página para conocer la seguridad y privacidad de sus recursos (código/artefactos) mediante AEM Cloud Manager.
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introducción
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: 949d3cf0239a02875ba4ad1888e081f104dec2e2

---


# Seguridad y privacidad {#security-and-privacy}

[!UICONTROL Cloud Manager] tiene funciones preconfiguradas con los permisos adecuados. Por ejemplo, un desarrollador desarrolla código y tiene permiso para insertar el código en el repositorio **Git**. Como alternativa, un propietario de una empresa tiene permisos diferentes que les permiten definir los Indicadores de rendimiento clave (KPI) y aprobar implementaciones.

## Permisos basados en roles {#role-based-permissions}

### Roles del usuario {#user-roles}

La administración de funciones para [!UICONTROL Cloud Manager] se realiza dentro de la Consola [de administración de](https://helpx.adobe.com/enterprise/using/admin-console.html)Adobe. Cualquier usuario de [!UICONTROL Cloud Manager] debe ser miembro de la organización IMS del cliente y tener el contexto de producto de los servicios gestionados de Adobe. Los miembros específicos de funciones se proporcionan agregando el usuario a un perfil [!UICONTROL Cloud Manager] de producto en la Consola de administración.

Para obtener más información sobre cómo configurar las funciones, consulte [Configuración de usuarios y funciones](setting-up-users-and-roles.md).

La siguiente lista de tabla define las posibles funciones que puede asignar en la Consola de administración.

| **[!UICONTROL Cloud Manager]Función** | **Descripción** |
|---|---|
| Propietario del negocio | Usuario principal que completa la [!UICONTROL Cloud Manager] configuración inicial. Responsable de definir KPI, aprobar implementaciones de producción y anular errores importantes de tres niveles. |
| Administrador de programas | Utiliza [!UICONTROL Cloud Manager] para realizar la configuración del equipo, revisar el estado y ver KPI. Puede aprobar errores importantes de tres niveles. |
| Administrador de implementación | Gestiona las operaciones de implementación. Utiliza [!UICONTROL Cloud Manager] para ejecutar implementaciones de fase y producción. Puede aprobar errores importantes de tres niveles. Tiene acceso al repositorio Git. |
| Desarrollador | Desarrolla y prueba el código de aplicación personalizado. Se utiliza principalmente [!UICONTROL Cloud Manager] para ver el estado. Tiene acceso de confirmación al repositorio Git. |
| Ingeniero de éxito del cliente | Generalmente admite el éxito del cliente para los clientes de AMS. Interactúa con [!UICONTROL Cloud Manager] el fin de ejecutar implementaciones que requieren la supervisión del consultor técnico de éxito del cliente (CSE). |
| Autor de contenido | Generalmente no interactúa con [!UICONTROL Cloud Manager]. Este usuario puede utilizar el [!UICONTROL Cloud Manager] conmutador de programas (tras haber navegado desde [!UICONTROL Experience Cloud]) para acceder a Adobe Experience Manager (AEM). |

### Permisos de usuario {#user-permissions}

Cada función tiene permisos específicos, tareas preconfiguradas o permisos asociados a cada función. Esta tabla enumera las funciones disponibles y las funciones que pueden ejecutar la función.

Para obtener más información sobre cómo configurar los usuarios, consulte [Configuración de usuarios y funciones](setting-up-users-and-roles.md).

| Permiso | Descripción | Propietario del negocio | Administrador de implementación | Administrador de programas | Desarrollador | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Leer aplicación | Ver detalles del programa. | x | x | x | x | x |
| Escribir aplicación | Configure el programa (incluidos los KPI). | x |  |  |  |  |
| Entorno de lectura | Consulte Detalles del entorno. | x | x | x | x | x |
| Crear ejecución | Iniciar canalización. | x | x | x |  |  |
| Leer ejecución | Consulte el estado de la ejecución. | x | x | x | x | x |
| Reanudar ejecución | Puede reanudar la ejecución cuando esté en pausa. | x | x | x |  | x |
| Ejecución Aprobar implementación en producción | Proporcione la aprobación de GoLive. | x | x | x |  |  |
| Implementación de programación de ejecución en producción | Programar la implementación de producción. | x | x | x |  | x |
| Implementación de ejecución en producción | Implemente la aplicación en producción cuando esté en pausa para la supervisión de CSE. |  |  |  |  | x |
| Cancelación de ejecución | Cancelar la ejecución actual. | x | x | x |  |  |
| Errores de control de calidad de anulación de ejecución | Aprobar Errores Importantes De Puerta De Calidad. | x | x | x |  |  |
| Creación de tubería | Configurar / Editar tubería. |  | x |  |  |  |
| Lectura de tubería | Consulte Detalles de canalización. | x | x | x | x | x |
| Escritura de tubería | Configurar / Editar tubería. |  | x |  |  |  |
| Aprobación de modificación de tubería | Permite editar la opción Propietario de la empresa. |  | x |  |  |  |
| Implementación administrada de modificación de tubería | Permite editar la opción Supervisión de CSE. |  | x |  |  |  |
| Lectura de la solución | Lea los KPI del programa. | x | x | x | x | x |
| Escritura de solución | Configurar el programa (incluidos los KPI) y editar la canalización. | x |  |  |  |  |
| Lectura del paso | Consulte los resultados de las métricas de calidad de los pasos. | x | x | x | x | x |

## Aislamiento de recursos {#resource-isolation}

Los clientes que utilicen [!UICONTROL Cloud Manager] sus credenciales de IMS deberán autenticarse, ya que todos los permisos vinculados a [!UICONTROL Cloud Manager] se configurarán y se vincularán a su organización de IMS. Durante el proceso de integración, el equipo de aprovisionamiento garantiza que se aplique el aislamiento de recursos en [!UICONTROL Cloud Manager].

## Seguridad de datos {#data-security}

El código en [!UICONTROL Cloud Manager] se cifra en tránsito. Los binarios que crea Coud Manager también se cifran en tránsito y se cifran cuando se almacenan.

Cada cliente obtiene su propio **repositorio** Git y su código es seguro y no se comparte con ninguna otra **organización**.

## Privacidad de datos {#data-privacy}

[!UICONTROL Cloud Manager] cumple los principios de privacidad definidos por Adobe. Los desarrolladores insertan código de forma segura en el repositorio **** Git a través de HTTPS.

La interfaz de usuario (UI) de [!DNL para [!UICONTROL Cloud Manager]] se basa en los servicios que cumplen con un marco de control común definido por Adobe. [!Interfaz de usuario DNL (IU) para [!UICONTROL Cloud Manager]] usa servicios seguros de varios proveedores de nube.
