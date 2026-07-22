---
title: Aprovisionamiento del entorno
description: Descubra cómo se aprovisionan los entornos como parte del proceso de incorporación de Cloud Manager.
exl-id: eade4255-89b5-4c65-a498-1c6d4e8c73ff
TQID: https://experienceleague.adobe.com/xLjZdRZeCiqF0KxHQ1nBI4IBBsh4BDTqETv79lrypR0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 02ecd16a1735fe37ac606d275da0f61406841f56
workflow-type: tm+mt
source-wordcount: 287
ht-degree: 66%

---

# Aprovisionamiento del entorno {#environments-provisioning}

Descubra cómo se aprovisionan los entornos como parte del proceso de incorporación de Cloud Manager.

## Aprovisionamiento {#provisioning}

Durante el proceso de incorporación, Adobe aprovisionará automáticamente todos los entornos de nube de AEM que haya adquirido y los vinculará a su programa en [!UICONTROL Cloud Manager]. Cada suscripción a Managed Services de Adobe incluye entornos de nube de AEM. Normalmente incluyen al menos un entorno de producción y un entorno de ensayo. Opcionalmente, también pueden incluir uno o más entornos de desarrollo o prueba.

## Correo electrónico de bienvenida {#welcome-email}

Una vez completado el proceso de aprovisionamiento del entorno, el administrador de clientes designado recibe un correo electrónico de bienvenida con la confirmación de que se les ha concedido acceso a Adobe [!UICONTROL Experience Cloud]. El correo electrónico de bienvenida contiene información detallada sobre cómo empezar a usar los servicios de [!UICONTROL Experience Cloud], los entornos de nube de [!UICONTROL AEM Managed Services], así como el portal de autoservicio [!UICONTROL Cloud Manager]. Además, el correo electrónico proporciona al ingeniero de éxito del cliente (Customer Success Engineer, CSE) información de contacto, recursos de asistencia, foros y preguntas comunes. En la lista de recursos que se proporciona en el correo electrónico, también encontrará detalles sobre cómo acceder a [!UICONTROL Cloud Manager] para los entornos de nube de AEM.

## Pasos siguientes {#next-steps}

Después de recibir el correo electrónico de bienvenida, puede iniciar sesión en [!UICONTROL Cloud Manager] como administrador del sistema con sus credenciales de Adobe IMS. Después de iniciar sesión, puede comprobar que los entornos de producción y no producción de la nube de AEM están disponibles y funcionan correctamente.

[!UICONTROL Cloud Manager] usa estos entornos de nube de AEM para ejecutar la canalización de CI/CD. Implementa código desde su repositorio de Git en el entorno de ensayo. A continuación, implementa el código en el entorno de producción de AEM. También podrá acceder a los entornos de nube de AEM directamente desde [!UICONTROL Cloud Manager] cuando esté listo para empezar a crear experiencias digitales para sus propiedades web.
