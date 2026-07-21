---
title: Incorporación del usuario
description: Obtenga información acerca de los diferentes escenarios de incorporación y la introducción a Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
TQID: https://experienceleague.adobe.com/EnNaMZzu5bLUD3Jjsp6ovqFvoFM30ju4FOQJfmySLEk
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 2cd89edca1c1dfac7f1b7b68eccdf1416efb4724
workflow-type: tm+mt
source-wordcount: 567
ht-degree: 62%

---

# Incorporación del usuario {#user-journey}

Como usuario de AEM (Adobe Experience Manager), se puede dar una de las siguientes situaciones:

* Es su primera vez en AEM.
* Está usando actualmente AEM 6.x.
* Necesita actualizar a la versión de AEM 6.5 para poder usar [!UICONTROL Cloud Manager].

Este documento describe estos tres escenarios y explica el proceso para comenzar con [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] solo está disponible para los clientes de Adobe Managed Services (AMS) que utilizan AEM 6.4 o superior.

## Incorporación {#onboarding}

El proceso de incorporación difiere según si es su primera vez en AMS o ya es cliente.

### Primera vez en Adobe Managed Services {#new-to-ams}

Como cliente nuevo, se le ha incorporado a [!UICONTROL Cloud Manager] como parte del proceso de incorporación a Adobe Managed Services.

Como parte del proceso de incorporación, recibirá un correo electrónico de bienvenida que incluye lo siguiente:

* La URL para acceder a [!UICONTROL Cloud Manager].
* Instrucciones para iniciar sesión en [!UICONTROL Experience Cloud].
* Instrucciones para utilizar Admin Console para administrar los usuarios y sus respectivos permisos de modo que puedan acceder a Cloud Manager si es necesario.

### Cliente existente de Adobe Managed Services {#existing-customer}

Como cliente de AMS, primero deberá actualizar los entornos de producción y de no producción existentes a AEM 6.4 o superior.

A medida que lleve a cabo la actualización, se incorporará a Cloud Manager y se le proporcionará la URL para acceder a [!UICONTROL Cloud Manager]. Además, tendrá que empezar a utilizar Admin Console para administrar los usuarios que necesitan acceder a [!UICONTROL Cloud Manager] y sus respectivos permisos.

El proyecto de AEM existente también debe ajustarse a las prácticas recomendadas, ya que empezará a usar [!UICONTROL Cloud Manager] para implementar cambios en el código en los entornos de AEM.

Para obtener información adicional sobre las ventajas de actualizar a AEM 6.5, consulte el documento [Actualización a AEM 6.5](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade).

## Acceso a [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Inicie sesión en la página de destino de [!UICONTROL Experience Cloud] con sus credenciales de Identity Management de Adobe. Seleccione AEM del conmutador de soluciones para acceder a [!UICONTROL Cloud Manager] y a sus entornos de AEM.

Tras iniciar sesión en [!UICONTROL Cloud Manager] por primera vez, tendrá acceso a los entornos de AEM directamente desde la IU de [!UICONTROL Cloud Manager]. En este punto, ya puede usar todas las características de [!UICONTROL Cloud Manager] y preparar su primera rama de código para implementarla en los entornos de ensayo y producción.

Para empezar con [!UICONTROL Cloud Manager], consulte el documento [Primer inicio de sesión](/help/getting-started/first-time-login.md).

Para obtener información adicional acerca de AEM, consulte [Implementación y mantenimiento](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/implementing/deploying/deploying/deploy).

## Introducción a [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Una vez que haya iniciado sesión en [!UICONTROL Cloud Manager], para comenzar con su proyecto de AEM, debe considerar lo siguiente:

1. Configuración del entorno del repositorio de código.
1. Configuración de su equipo y funciones. Las suscripciones a funciones se asignan añadiendo el usuario a un perfil de [!UICONTROL Cloud Manager] mediante Admin Console.
1. Configuración de las ramas del código fuente en el repositorio de Git.
1. Defina los indicadores clave de rendimiento (KPI) y de carga.
1. Definición de escenarios de prueba para implementar correctamente el código en los entornos de ensayo y producción una vez que todas las comprobaciones de calidad hayan resultado correctas.

## Resumen del proceso {#end-to-end-journey}

El diagrama siguiente resume el proceso al usar la canalización de CD/CI de [!UICONTROL Cloud Manager] para implementar los cambios de código en los entornos de ensayo y producción.

![recorrido del cliente para la incorporación a Cloud Manager, que muestra la ruta para los clientes nuevos y existentes a través del aprovisionamiento o las actualizaciones del entorno, la administración de usuarios y funciones, la implementación de proyectos y la canalización de CI/CD.](/help/assets/screen_shot_2018-05-15at124004pm.png)
