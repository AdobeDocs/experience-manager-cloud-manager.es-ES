---
title: Seguridad y privacidad
seo-title: Seguridad y privacidad para AEM Cloud Manager
description: Siga esta página para conocer la seguridad y privacidad de sus recursos (código/artefactos).
seo-description: Siga esta página para obtener información sobre la seguridad y privacidad de sus recursos (código/artefactos) mediante AEM Cloud Manager.
uuid: 68 bc 2330-a 62 c -4 c 2 c -925 c-daa 6788 b 143 a
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introducción
discoiquuid: 67 a 54 bae -99 a 9-4405-91 e 3-9 a 0 a 8 b 3 ccc 98
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Seguridad y privacidad {#security-and-privacy}

[!UICONTROL Cloud Manager] tiene funciones preconfiguradas con permisos adecuados. Por ejemplo, un desarrollador desarrolla código y tiene permiso para insertar el código en el repositorio **de Git**. Como alternativa, un propietario comercial tiene permisos diferentes que les permiten definir los indicadores de rendimiento clave (KPI) y aprobar implementaciones.

## Permisos basados en roles {#role-based-permissions}

### Roles del usuario {#user-roles}

La administración de funciones se [!UICONTROL Cloud Manager] realiza dentro de [Adobe Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html). Cualquier usuario de [!UICONTROL Cloud Manager] debe ser miembro de la organización IMS del cliente y tener el Contexto de producto de los servicios gestionados de Adobe. Las membresías de función específicas se proporcionan agregando el usuario a un perfil [!UICONTROL Cloud Manager] de producto en Admin Console.

Para obtener más información sobre cómo configurar sus funciones, consulte [Configuración de usuarios y funciones](setting-up-users-and-roles.md).

La siguiente lista de tabla define las posibles funciones que puede asignar en la Consola de administración.

| **[!UICONTROL Cloud Manager]Función** | **Descripción** |
|---|---|
| Propietario comercial | Usuario principal que completa la [!UICONTROL Cloud Manager] configuración inicial. Responsable de definir KPI, aprobar implementaciones de producción y anular errores importantes de 3 niveles. |
| Administrador de programas | Utiliza [!UICONTROL Cloud Manager] para realizar configuraciones de equipo, revisar el estado y ver KPI. Puede aprobar errores importantes de 3 niveles. |
| Administrador de implementación | Gestiona las operaciones de implementación. Utiliza [!UICONTROL Cloud Manager] para ejecutar implementaciones de fase e producción. Puede aprobar errores importantes de 3 niveles. Tiene acceso al repositorio Git. |
| Desarrollador | Desarrolla y prueba el código de aplicación personalizado. Utiliza principalmente [!UICONTROL Cloud Manager] para ver el estado. Has commit access to Git repositorio. |
| Ingeniero de éxito del cliente | Generalmente admite el éxito de los clientes para los clientes de AMS. Interactúa con [!UICONTROL Cloud Manager] el objetivo de ejecutar implementaciones que requieran la supervisión de ingenieros de éxito de clientes (CSE). |
| Autor de contenido | Generalmente no interactúa [!UICONTROL Cloud Manager]con. Este usuario puede utilizar el conmutador [!UICONTROL Cloud Manager] de programa (desde [!UICONTROL Experience Cloud]) para acceder a Adobe Experience Manager (AEM). |

### Permisos de usuario {#user-permissions}

Cada una de las funciones tiene permisos específicos, tareas preconfiguradas o permisos, asociados con cada función. Esta tabla enumera las funciones disponibles y las funciones que pueden ejecutar la función.

Para obtener más información sobre cómo configurar los usuarios, consulte [Configuración de usuarios y funciones](setting-up-users-and-roles.md).

| Permiso | Descripción | Propietario comercial | Administrador de implementación | Administrador de programas | Desarrollador | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Leer aplicación | Consulte los detalles del programa. | x | x | x | x | x |
| Escribir aplicación | Configurar programa (incluidos KPI). | x |
| Leer entorno | Consulte Detalles del entorno. | x | x | x | x | x |
| Crear ejecución | Inicie Pipeline. | x | x | x |
| Ejecución de lectura | Consulte Estado de ejecución. | x | x | x | x | x |
| Reanudar ejecución | Puede reanudar la ejecución cuando se pause. | x | x | x | x |
| Implementación Aprobar implementación en producción | Proporcione aprobación de golive. | x | x | x |
| Programación de programación de ejecución en producción | Programar la implementación de producción. | x | x | x | x |
| Implementación de ejecución en producción | Implemente la aplicación en producción cuando se ponga en pausa para la supervisión de CSE. | x |
| Cancelación de ejecución | Cancelar la ejecución actual. | x | x | x |
| Errores de apertura de la calidad de anulación de ejecución | Aprobar errores importantes de Gate Gate. | x | x | x |
| Crear Pipeline | Configuración/Editar Pipeline. | x |
| Lectura de Pipeline | Consulte Detalles de Pipeline. | x | x | x | x | x |
| Escritura de Pipeline | Configuración/Editar Pipeline. | x |
| Modify Modify Approval | Permite editar la opción Propietario de empresa. | x |
| Pipeline Modify Managed Deployment | Permite editar la opción de supervisión de CSE. | x |
| Lectura de la solución | Lea los KPI del programa. | x | x | x | x | x |
| Escritura de solución | Configure la configuración o Editar pipeline del programa (incluidos KPI). | x |
| Paso leído | Ver los resultados de las métricas de calidad del paso. | x | x | x | x | x |

## Aislamiento de recursos {#resource-isolation}

Los clientes que usen [!UICONTROL Cloud Manager] sus credenciales de IMS necesitarán la autenticación, ya que todos los permisos asociados se [!UICONTROL Cloud Manager] configurarán y vincularán a su organización de IMS. Durante el proceso de integración, el equipo de aprovisionamiento garantiza que se aplique el aislamiento de recursos [!UICONTROL Cloud Manager].

## Seguridad de datos {#data-security}

El código incluido [!UICONTROL Cloud Manager] está cifrado en tránsito. Los binarios que compila Coud Manager también están cifrados en tránsito y cifrados cuando se almacenan.

Cada cliente obtiene su propio **repositorio** de Git y su código es seguro y no se comparte con ninguna otra **organización**.

## Privacidad de datos {#data-privacy}

[!UICONTROL Cloud Manager] cumple los principios de privacidad definidos por Adobe. Los desarrolladores insertan código de forma segura en el repositorio **de Git** a través de HTTPS.

El [! La interfaz de usuario de DNL para [!UICONTROL Cloud Manager]] se basa en la parte superior de servicios que cumplen con un marco de control común definido por Adobe. [! La interfaz de usuario DNL para [!UICONTROL Cloud Manager]] utiliza servicios seguros de varios proveedores de nube.
