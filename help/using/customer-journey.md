---
title: Recorrido del cliente
seo-title: Recorrido del cliente de Adobe AEM Cloud Manager
description: Siga esta página para conocer su recorrido como cliente y empezar a usar Cloud Manager.
seo-description: Siga esta página para conocer su recorrido como cliente y empezar a usar Adobe AEM Cloud Manager.
uuid: d4468eb6-5bde-48dd-b96e-0cc61e046f96
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: bc9a0d63-ae6b-4fe9-81e5-bf9844f04e54
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---


# Recorrido del cliente {#customer-journey}

Como cliente, puede que sea nuevo en Adobe Experience Manager (AEM), que actualmente utiliza AEM 6.4, o que necesite actualizar a la versión AEM 6.4 para poder utilizar [!UICONTROL Cloud Manager]. Los siguientes escenarios explican su recorrido como cliente nuevo o existente para comenzar con [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] solo está disponible para los clientes de servicios gestionados de Adobe que utilicen AEM 6.4 o superior.

## Al realizar la carga a [!UICONTROL Cloud Manager]{#on-boarding-to-cloud-manager}

1. **Cliente nuevo AEM en los servicios administrados de Adobe**

   Como cliente nuevo, se incorporará a [!UICONTROL Cloud Manager] como parte del proceso de integración de los servicios administrados de Adobe.

   La dirección URL para acceder a [!UICONTROL Cloud Manager] se incluirá en el correo electrónico de bienvenida, junto con las instrucciones para iniciar sesión en [!UICONTROL Experience Cloud], y usar el Adobe Admin Console para administrar sus usuarios y sus respectivos permisos, para aquellos usuarios que necesiten acceder a [!UICONTROL Cloud Manager].

1. **Cliente AEM existente en los servicios administrados de Adobe**

   Como cliente existente, primero deberá actualizar sus entornos de producción y no producción existentes a la versión AEM 6.4. Al mismo tiempo que realizará la actualización, se le proporcionará la dirección URL para acceder a [!UICONTROL Cloud Manager]. Además, deberá usar el inicio de Adobe Admin Console para administrar sus usuarios y sus permisos respectivos, para aquellos usuarios que necesiten acceder a [!UICONTROL Cloud Manager].

   El proyecto de AEM existente también deberá cumplir con las optimizaciones recomendadas, ya que se le dará inicio de utilizar [!UICONTROL Cloud Manager] para implementar nuevos cambios de código en sus entornos de AEM.

   Para obtener información adicional sobre los beneficios de la actualización a AEM 6.4, consulte [Actualización a AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

## Acceso a [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Para obtener acceso a [!UICONTROL Cloud Manager] y sus entornos de AEM, simplemente inicie sesión en la página de aterrizaje [!UICONTROL Experience Cloud], utilice las credenciales de Identity Management de Adobe y seleccione AEM en la interfaz del conmutador de soluciones.

Después de iniciar sesión [!UICONTROL Cloud Manager] por primera vez, tendrá acceso a sus entornos de AEM directamente desde la [!UICONTROL Cloud Manager] interfaz de usuario. En este punto, estará listo para explorar todas las posibilidades de [!UICONTROL Cloud Manager], una vez que tenga su primera rama de código lista para implementarse en su etapa y entornos de producción.

Para explorar y comenzar con [!UICONTROL Cloud Manager], consulte [Inicio de sesión por primera vez](first-time-login.md). Para obtener información adicional sobre AEM, consulte [Introducción a AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/deploy.html). Además, consulte [Recursos AEM](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&amp;mv=other) para obtener más información.

## Introducción a [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Una vez que haya iniciado sesión en [!UICONTROL Cloud Manager], lo primero que debe hacer será configurar el entorno del repositorio de código, luego el equipo y las funciones. Específicamente, las pertenencias a funciones se asignan agregando el usuario a un perfil [!UICONTROL Cloud Manager] mediante la interfaz de usuario del Admin Console.

A continuación, debe configurar sus ramas de código fuente en el **Repositorio de Git**, definir sus objetivos en términos de KPI de carga y rendimiento y probar los escenarios para implementar correctamente su código en los entornos de etapa y producción una vez que todas las comprobaciones de calidad se hayan superado correctamente.

## Recorrido de extremo a extremo {#end-to-end-journey}

El diagrama siguiente ilustra el recorrido del cliente en un nivel alto, al utilizar [!UICONTROL Cloud Manager] flujo de CD/CI para implementar los cambios de código en los entornos de etapa y producción.

![](assets/screen_shot_2018-05-15at124004pm.png)

