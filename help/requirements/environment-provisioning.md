---
title: Aprovisionamiento del entorno
description: Descubra cómo se aprovisionan los entornos como parte del proceso de incorporación de Cloud Manager.
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: ht
source-wordcount: '297'
ht-degree: 100%

---


# Aprovisionamiento del entorno {#environments-provisioning}

Descubra cómo se aprovisionan los entornos como parte del proceso de incorporación de Cloud Manager.

## Aprovisionamiento {#provisioning}

Durante el proceso de incorporación, Adobe aprovisionará automáticamente todos los entornos de nube de AEM que haya adquirido y los vinculará a su programa en [!UICONTROL Cloud Manager]. Cada suscripción a Managed Services de Adobe incluye entornos de nube de AEM. Normalmente incluyen al menos un entorno de producción y un entorno de ensayo. Opcionalmente, también pueden incluir uno o más entornos de desarrollo o prueba.

## Correo electrónico de bienvenida {#welcome-email}

Una vez completado el proceso de aprovisionamiento del entorno, el administrador del cliente designado recibe un correo electrónico de bienvenida con la confirmación de que se les ha concedido acceso [!UICONTROL Experience Cloud] de Adobe. El correo electrónico de bienvenida contiene información detallada sobre cómo empezar a usar los servicios de [!UICONTROL Experience Cloud], los entornos de nube de [!UICONTROL AEM Managed Services], así como el portal de autoservicio [!UICONTROL Cloud Manager]. Además, el correo electrónico contiene información importante, como la información de contacto del ingeniero de éxito del cliente (CSE), dónde buscar recursos de soporte, foros, preguntas frecuentes y mucho más. En la lista de recursos que se proporciona en el correo electrónico, también encontrará detalles sobre cómo acceder a [!UICONTROL Cloud Manager] para los entornos de nube de AEM.

## Pasos siguientes {#next-steps}

Después de recibir el correo electrónico de bienvenida, está listo para iniciar sesión en [!UICONTROL Cloud Manager] como administrador del sistema con sus credenciales de Adobe IMS. Después de iniciar sesión, puede comprobar que los entornos de producción y no producción de la nube de están disponibles y se ejecutan sin problemas.

[!UICONTROL Cloud Manager] usa estos entornos de nube de AEM para ejecutar la canalización de CI/CD. Implementa código desde su repositorio de Git en el entorno de ensayo. A continuación, implementa el código en el entorno de producción de AEM. También podrá acceder a los entornos de nube de AEM directamente desde [!UICONTROL Cloud Manager] cuando esté listo para empezar a crear experiencias digitales para sus propiedades web.
