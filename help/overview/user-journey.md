---
title: Recorrido del usuario
description: En este documento se exponen los diferentes escenarios de incorporación y se explica el recorrido de introducción a Cloud Manager.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: ht
source-wordcount: '504'
ht-degree: 100%

---


# Recorrido del usuario {#user-journey}

Como usuario de Adobe Experience Manager, puede estar en una de estas situaciones:

* Es su primera vez en AEM.
* Está usando actualmente AEM 6.x.
* Necesita actualizar a la versión AEM 6.5 para poder usar [!UICONTROL Cloud Manager].

Este documento presenta estos escenarios y le explica el recorrido para comenzar con [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] solo está disponible para los clientes de Adobe Managed Services (AMS) que utilizan AEM 6.4 o superior.

## Incorporación {#onboarding}

El proceso de incorporación difiere según si es su primera vez en AMS o ya es cliente.

### Primera vez en Adobe Managed Services {#new-to-ams}

Como cliente nuevo, se le incorporará a [!UICONTROL Cloud Manager] como parte del proceso de incorporación a Adobe Managed Services.

Como parte del proceso de incorporación, recibirá un correo electrónico de bienvenida que incluye lo siguiente:

* La dirección URL para acceder a [!UICONTROL Cloud Manager]
* Instrucciones para iniciar sesión en [!UICONTROL Experience Cloud]
* Instrucciones para utilizar Admin Console para administrar los usuarios y sus respectivos permisos de modo que puedan acceder a [!UICONTROL Cloud Manager] si es necesario.

### Cliente existente de Adobe Managed Services {#existing-customer}

Como cliente de AMS, primero deberá actualizar los entornos de producción y de no producción existentes a AEM 6.4 o superior.

A medida que lleve a cabo la actualización, se incorporará a Cloud Manager y se le proporcionará la URL para acceder a [!UICONTROL Cloud Manager]. Además, tendrá que empezar a utilizar Admin Console para administrar los usuarios que necesitan acceder a [!UICONTROL Cloud Manager] y sus respectivos permisos.

El proyecto de AEM existente también tendrá que ajustarse a las prácticas recomendadas, ya que empezará a usar [!UICONTROL Cloud Manager] para implementar cambios en el código en los entornos de AEM.

Para obtener información adicional sobre las ventajas de actualizar a AEM 6.5, consulte el documento [Actualización a AEM 6.5.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html?lang=es)

## Acceso a [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Tendrá acceso a [!UICONTROL Cloud Manager] y a sus entornos de AEM simplemente iniciando sesión en la página de aterrizaje de [!UICONTROL Experience Cloud] con las credenciales de Identity Management de Adobe y seleccionando AEM en la interfaz del conmutador de soluciones.

Tras iniciar sesión en [!UICONTROL Cloud Manager] por primera vez, tendrá acceso a los entornos de AEM directamente desde la IU de [!UICONTROL Cloud Manager]. En este punto, ya puede explorar todas las posibilidades de [!UICONTROL Cloud Manager] y preparar su primera rama de código para implementarla en los entornos de ensayo y producción.

Para empezar con [!UICONTROL Cloud Manager], consulte el documento [Primer inicio de sesión](/help/getting-started/first-time-login.md).

Para obtener información adicional acerca de AEM, consulte el documento [Implementación y mantenimiento.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=es)

## Introducción a [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Una vez que haya iniciado sesión en [!UICONTROL Cloud Manager], para comenzar con su proyecto de AEM, debe considerar lo siguiente:

1. Configuración del entorno del repositorio de código.
1. Configuración de su equipo y funciones.
   * Las suscripciones a funciones se asignan agregando el usuario a un perfil de [!UICONTROL Cloud Manager] mediante Admin Console.
1. Configuración de las ramas del código fuente en el repositorio de Git.
1. Definición de los objetivos en términos de los indicadores clave de rendimiento (KPI) de carga y rendimiento.
1. Definición de escenarios de prueba para implementar correctamente el código en los entornos de ensayo y producción una vez que todas las comprobaciones de calidad hayan resultado correctas.

## Recorrido de extremo a extremo {#end-to-end-journey}

Este diagrama ilustra el recorrido del cliente en un nivel superior al utilizar la canalización de CI/CD de [!UICONTROL Cloud Manager] para implementar los cambios de código en los entornos de ensayo y producción.

![Recorrido de extremo a extremo](/help/assets/screen_shot_2018-05-15at124004pm.png)
