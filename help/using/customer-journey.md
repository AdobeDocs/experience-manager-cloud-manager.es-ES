---
title: Recorrido del cliente
seo-title: Recorrido del cliente de Adobe AEM Cloud Manager
description: Siga esta página para obtener más información sobre su recorrido como cliente y comenzar a usar Cloud Manager.
seo-description: Siga esta página para obtener más información sobre su recorrido como cliente y comenzar a usar Adobe AEM Cloud Manager.
uuid: d4468eb6-5bde-48dd-b96e-0cc61e046f96
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: bc9a0d63-ae6b-4fe9-81e5-bf9844f04e54
feature: Introducción
level: Principiante
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 2%

---


# Recorrido del cliente {#customer-journey}

Como cliente, puede que sea nuevo en Adobe Experience Manager (AEM), que actualmente utiliza AEM 6.4, o que necesite actualizar a la versión AEM 6.4 para poder utilizar [!UICONTROL Cloud Manager]. Los siguientes escenarios explican su recorrido como cliente nuevo o existente para comenzar con [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] solo está disponible para los clientes de Adobe Managed Services que utilizan AEM 6.4 o superior.

## Incorporación a [!UICONTROL Cloud Manager]{#on-boarding-to-cloud-manager}

1. **Cliente nuevo AEM en Adobe Managed Services**

   Como cliente nuevo, estará incorporado a [!UICONTROL Cloud Manager] como parte del proceso de incorporación a los servicios administrados de Adobe.

   La dirección URL para acceder a [!UICONTROL Cloud Manager] se incluirá en el mensaje de correo electrónico de bienvenida, junto con las instrucciones para iniciar sesión en [!UICONTROL Experience Cloud] y usar Adobe Admin Console para administrar los usuarios y sus respectivos permisos, para los usuarios que necesiten acceder a [!UICONTROL Cloud Manager].

1. **Cliente AEM existente en Adobe Managed Services**

   Como cliente existente, primero deberá actualizar los entornos de producción y no producción existentes a la versión AEM 6.4. Al mismo tiempo que realizará la actualización, estará incorporado y se le proporcionará la URL para acceder a [!UICONTROL Cloud Manager]. Además, tendrá que empezar a usar Adobe Admin Console para administrar los usuarios y sus respectivos permisos, para aquellos usuarios que necesiten acceder a [!UICONTROL Cloud Manager].

   El proyecto de AEM existente también tendrá que ajustarse a las prácticas recomendadas, ya que comenzará a utilizar [!UICONTROL Cloud Manager] para implementar nuevos cambios de código en los entornos de AEM.

   Para obtener información adicional sobre las ventajas de actualizar a AEM 6.4, consulte [Actualización a AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

## Acceso a [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Para obtener acceso a [!UICONTROL Cloud Manager] y a los entornos de AEM, solo tiene que iniciar sesión en la página de aterrizaje [!UICONTROL Experience Cloud], usar las credenciales de Identity Management de Adobe y seleccionar AEM en la interfaz del conmutador de soluciones.

Después de iniciar sesión en [!UICONTROL Cloud Manager] por primera vez, tendrá acceso a los entornos de AEM directamente desde la interfaz de usuario de [!UICONTROL Cloud Manager]. En este punto, está listo para explorar todas las posibilidades de [!UICONTROL Cloud Manager], una vez que tenga la primera rama de código lista para implementarse en los entornos de ensayo y producción.

Para explorar y comenzar con [!UICONTROL Cloud Manager], consulte [Primer inicio de sesión](first-time-login.md). Para obtener más información sobre AEM, consulte [Introducción a AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/deploy.html). Además, consulte [AEM Resources](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&amp;mv=other) para obtener más información.

## Introducción a [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Una vez que haya iniciado sesión en [!UICONTROL Cloud Manager], lo primero que debe hacer será configurar el entorno del repositorio de código, luego su equipo y funciones. Específicamente, las suscripciones a funciones se asignan agregando el usuario a un perfil [!UICONTROL Cloud Manager] mediante la interfaz de usuario del Admin Console.

A continuación, debe configurar las ramas de código fuente en el **Repositorio Git**, definir los objetivos en términos de KPI de carga y rendimiento y probar escenarios para implementar correctamente el código en los entornos de ensayo y producción una vez que todas las comprobaciones de calidad hayan pasado correctamente.

## Recorrido de extremo a extremo {#end-to-end-journey}

El diagrama siguiente ilustra el recorrido del cliente en un nivel superior al utilizar la canalización [!UICONTROL Cloud Manager] CI/CD para implementar los cambios de código en los entornos de ensayo y producción.

![](assets/screen_shot_2018-05-15at124004pm.png)

