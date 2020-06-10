---
title: Recorrido del cliente
seo-title: Viaje del cliente de Adobe AEM Cloud Manager
description: Siga esta página para conocer su viaje como cliente y empezar a trabajar con Cloud Manager.
seo-description: Siga esta página para conocer su viaje como cliente y empezar a utilizar Adobe AEM Cloud Manager.
uuid: d4468eb6-5bde-48dd-b96e-0cc61e046f96
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: bc9a0d63-ae6b-4fe9-81e5-bf9844f04e54
translation-type: tm+mt
source-git-commit: 77b7e2fc81880a7f1878fa9553ce2ae8078d1b78
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---


# Recorrido del cliente {#customer-journey}

Como cliente, es posible que sea nuevo en Adobe Experience Manager (AEM), que actualmente utiliza AEM 6.4, o que necesite actualizar a la versión AEM 6.4 para poder utilizarla [!UICONTROL Cloud Manager]. Los siguientes escenarios explican su viaje como cliente nuevo o existente con el que comenzar [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] solo está disponible para los clientes de servicios gestionados de Adobe que utilicen AEM 6.4 o superior.

## Incorporación a [!UICONTROL Cloud Manager]{#on-boarding-to-cloud-manager}

1. **Nuevo cliente de AEM en los servicios gestionados de Adobe**

   Como cliente nuevo, se le incorporará [!UICONTROL Cloud Manager] como parte del proceso de integración en el servicio en la nube gestionado por Adobe.

   La dirección URL a la que se accede [!UICONTROL Cloud Manager] se incluirá en el mensaje de correo electrónico de bienvenida, junto con las instrucciones para iniciar sesión en [!UICONTROL Experience Cloud]Adobe Admin Console y usar la misma para administrar los usuarios y sus permisos respectivos, para aquellos usuarios que necesiten acceder a [!UICONTROL Cloud Manager].

1. **Cliente existente de AEM en los servicios gestionados de Adobe**

   Como cliente existente, primero deberá actualizar sus entornos de producción y no producción existentes a la versión AEM 6.4. Al mismo tiempo que realizará la actualización, se le proporcionará la dirección URL para acceder [!UICONTROL Cloud Manager]. Además, deberá usar la Consola de administración de Adobe para administrar los usuarios y sus permisos respectivos, para aquellos usuarios que necesiten acceder a ellos [!UICONTROL Cloud Manager].

   El proyecto de AEM existente también tendrá que ajustarse a las prácticas recomendadas, ya que tendrá que usar el inicio [!UICONTROL Cloud Manager] para implementar nuevos cambios de código en sus entornos de AEM.

   Para obtener información adicional sobre las ventajas de la actualización a AEM 6.4, consulte [Actualización a AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

## Acceso [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Para obtener acceso a [!UICONTROL Cloud Manager] y a sus entornos de AEM, solo tiene que iniciar sesión en la [!UICONTROL Experience Cloud] página de aterrizaje, utilizar las credenciales de Adobe Identity Management y seleccionar AEM en la interfaz del conmutador de soluciones.

Tras iniciar sesión [!UICONTROL Cloud Manager] por primera vez, tendrá acceso a sus entornos de AEM directamente desde la [!UICONTROL Cloud Manager] interfaz de usuario. En este punto, está listo para explorar todas las posibilidades de [!UICONTROL Cloud Manager], una vez que tenga su primera rama de código lista para ser implementada en su etapa y entornos de producción.

Para explorar y comenzar con [!UICONTROL Cloud Manager], consulte Inicio de sesión [por](first-time-login.md)primera vez. Para obtener más información sobre AEM, consulte [Introducción a AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/deploy.html). Además, consulte Recursos [](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&amp;mv=other) AEM para obtener más información.

## Getting Started with [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Una vez que haya iniciado sesión en [!UICONTROL Cloud Manager], lo primero que debe hacer será configurar el entorno del repositorio de código, luego el equipo y las funciones. En concreto, las pertenencias a funciones se asignan agregando el usuario a un [!UICONTROL Cloud Manager] perfil mediante la interfaz de usuario de la Consola de administración.

A continuación, debe configurar sus ramas de código fuente en el repositorio **** Git, definir sus objetivos en términos de KPI de carga y rendimiento y probar los escenarios para implementar correctamente su código en los entornos de fase y producción una vez que todas las comprobaciones de calidad se hayan superado correctamente.

## Trayecto de final a final {#end-to-end-journey}

El diagrama siguiente ilustra el viaje del cliente a un nivel elevado, al utilizar la canalización [!UICONTROL Cloud Manager] CI/CD para implementar los cambios de código en los entornos de fase y producción.

![](assets/screen_shot_2018-05-15at124004pm.png)

