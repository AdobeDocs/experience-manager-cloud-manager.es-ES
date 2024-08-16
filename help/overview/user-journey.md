---
title: Recorrido del usuario
description: Obtenga información acerca de los diferentes escenarios de incorporación y la introducción a Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 6a5615c0db91c62fc8858b967021b46c7b383aa0
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 21%

---


# Recorrido del usuario {#user-journey}

AEM Como usuario de (Adobe Experience Manager), es probable que se ajuste a uno de los siguientes escenarios:

* AEM Eres nuevo en el mundo de la.
* AEM Actualmente está utilizando la versión 6.x de.
* AEM Debe actualizar a la versión 6.5 de la para usar [!UICONTROL Cloud Manager].

En este documento se exponen estos tres escenarios y se explica el recorrido para comenzar a usar [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] solo está disponible para los clientes de Adobe Managed Services (AMS) que utilizan AEM 6.4 o superior.

## Incorporación {#onboarding}

El proceso de incorporación difiere según si es su primera vez en AMS o ya es cliente.

### Primera vez en Adobe Managed Services {#new-to-ams}

Como cliente nuevo, se te incorporará a [!UICONTROL Cloud Manager] como parte del proceso de incorporación a Adobe Managed Services.

Como parte del proceso de incorporación, recibe un correo electrónico de bienvenida que incluye lo siguiente:

* Dirección URL para obtener acceso a [!UICONTROL Cloud Manager].
* Instrucciones para iniciar sesión en [!UICONTROL Experience Cloud].
* Instrucciones para utilizar Admin Console para administrar los usuarios y sus respectivos permisos de modo que puedan acceder a [!UICONTROL Cloud Manager] si es necesario.

### Adobe actual del cliente de Managed Services {#existing-customer}

AEM Como cliente de AMS, primero debe actualizar los entornos de producción y de no producción existentes a la versión 6.4 o superior de la.

Durante la actualización, se incorporará a Cloud Manager y se le proporcionará la URL para acceder a [!UICONTROL Cloud Manager]. Además, debe empezar a usar el Admin Console para administrar los usuarios que necesitan acceder a [!UICONTROL Cloud Manager] y sus respectivos permisos.

AEM El proyecto existente de también debe ajustarse a las prácticas recomendadas, ya que empezará a usar [!UICONTROL Cloud Manager AEM] para implementar cambios en el código en los entornos de la.

AEM AEM Para obtener información adicional sobre las ventajas de actualizar a la versión 6.5 de la versión, consulte [Actualización a la versión 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade) de la versión de.

## Acceder a [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Inicie sesión en la página de aterrizaje de [!UICONTROL Experience Cloud] con sus credenciales de Identity Management de Adobe. AEM Desde allí, seleccione el conmutador de soluciones para acceder a [!UICONTROL Cloud Manager AEM] y a sus entornos de.

Después de iniciar sesión en [!UICONTROL Cloud Manager AEM] por primera vez, tendrá acceso a los entornos de su directamente desde la interfaz de [!UICONTROL Cloud Manager]. En este punto, ya puede explorar todas las posibilidades de [!UICONTROL Cloud Manager] y preparar su primera rama de código para implementarla en los entornos de ensayo y producción.

Para empezar a usar [!UICONTROL Cloud Manager], consulte [Primer inicio de sesión](/help/getting-started/first-time-login.md).

AEM Para obtener más información acerca de la implementación, consulte [Implementación y mantenimiento](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/implementing/deploying/deploying/deploy).

## Introducción a [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Después de iniciar sesión en [!UICONTROL Cloud Manager AEM], puede comenzar con su proyecto de haciendo lo siguiente:

1. Configure el entorno del repositorio de código.
1. Configure su equipo y sus funciones. Las suscripciones a funciones se asignan agregando el usuario a un perfil de [!UICONTROL Cloud Manager] mediante Admin Console.
1. Configure las ramas del código fuente en el repositorio de Git.
1. Defina sus objetivos en términos de KPI de carga y rendimiento (indicadores de rendimiento clave).
1. Defina escenarios de prueba para implementar el código correctamente en los entornos de ensayo y producción después de pasar todas las comprobaciones de calidad.

## Recorrido de extremo a extremo {#end-to-end-journey}

Este diagrama ilustra el recorrido del cliente en un nivel superior al usar la canalización de CD/CI de [!UICONTROL Cloud Manager] para implementar los cambios de código en los entornos de ensayo y producción.

![Recorrido de extremo a extremo](/help/assets/screen_shot_2018-05-15at124004pm.png)
