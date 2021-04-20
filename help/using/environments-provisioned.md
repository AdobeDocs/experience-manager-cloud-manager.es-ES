---
title: Entornos aprovisionados
seo-title: Entornos aprovisionados en AEM Cloud Manager
description: Siga esta página para ver los entornos aprovisionados disponibles en Cloud Manager
seo-description: Siga esta página para ver los entornos aprovisionados disponibles en AEM Cloud Manager.
uuid: d04ee39c-7112-4adc-ad4e-56f91cc4ecfa
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: 7d32ba78-4ded-4656-aac2-c3e7cc0518de
feature: Environments, Provisioning
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 1%

---


# Entornos aprovisionados {#environments-provisioned}

## Aprovisionamiento {#provisioning}

Durante el proceso de incorporación del cliente, todos los entornos de la nube AEM adquiridos por un cliente se aprovisionan automáticamente mediante Adobe y se vinculan de nuevo a su programa en [!UICONTROL Cloud Manager]. Estos entornos de nube de AEM **** se incluyen en cada suscripción a Adobe Managed Services y normalmente están compuestos por al menos un entorno de producción, un entorno de fase y, opcionalmente, uno o más entornos de desarrollo o prueba.

## Correo electrónico de bienvenida {#welcome-email}

Una vez completado el proceso de aprovisionamiento del entorno, el administrador del cliente designado recibe un **correo electrónico de bienvenida** con la confirmación de que se les ha concedido acceso al Adobe [!UICONTROL Experience Cloud]. El correo electrónico contiene información detallada sobre cómo empezar a utilizar los servicios [!UICONTROL Experience Cloud], los entornos de nube [!UICONTROL AEM Managed Services], así como el portal de autoservicio [!UICONTROL Cloud Manager]. Además, el correo electrónico contiene información importante, como la información de contacto del ingeniero de éxito del cliente, adónde ir para obtener recursos de asistencia, foros o preguntas frecuentes, y mucho más. En la lista de recursos que se proporciona en el correo electrónico, también obtendrá detalles sobre cómo acceder a [!UICONTROL Cloud Manager] o a los entornos de la nube de AEM.

## Pasos siguientes {#next-steps}

Después de recibir el correo electrónico de bienvenida, está listo para iniciar sesión en [!UICONTROL Cloud Manager] como administrador, con sus credenciales de Adobe IMS. Una vez que haya iniciado sesión, podrá comprobar que los entornos de producción y no producción de la nube de AEM están disponibles y se ejecutan correctamente.

[!UICONTROL Cloud Manager] usará estos entornos de nube de AEM para ejecutar la canalización de CI/CD al implementar el código, empezando por el repositorio Git de [!UICONTROL Cloud Manager], a través del entorno de ensayo **Environment** y hasta su entorno de producción de AEM. También podrá acceder a sus entornos de nube de AEM directamente desde [!UICONTROL Cloud Manager], cuando esté listo para empezar a crear experiencias digitales para sus propiedades web.
