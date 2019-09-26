---
title: Conceptos antes de utilizar Cloud Manager
seo-title: Conceptos antes de utilizar Cloud Manager
description: nulo
seo-description: nulo
page-status-flag: nunca activado
uuid: 55cc551a-e812-4102-96c8-13d2cdd79c84
contentOwner: jsyal
discoiquuid: c3fd3f4e-0b57-4377-b923-a440c74773d8
preview: verdadero
translation-type: tm+mt
source-git-commit: f135526c6a47f1502395e6d53f9e286c0f935da5

---


# Conceptos antes de utilizar Cloud Manager{#understanding-concepts-before-using-cloud-manager}

En esta sección se proporcionan conceptos y terminologías que son útiles antes de trabajar en Cloud Manager y se tratan los siguientes temas:

* **Entorno de implementación**
* **Repositorio de códigos de origen**
* **Seguridad y privacidad**
* **Información general de canalización**
* **Recursos de ayuda**

## Entorno de implementación {#deployment-environment}

Es posible que sea nuevo en Adobe Experience Manager (AEM) 6.4 o que necesite actualizar a la versión 6.4 de AEM.

Si es un usuario nuevo de AEM 6.4, ya tiene acceso a Cloud Manager.

Si ya es cliente, debe actualizar a AEM 6.4 para tener acceso a Cloud Manager. Puede empezar a utilizar Cloud Manager, una vez que reciba la dirección URL y las credenciales de los ingenieros de éxito del cliente (CSE).

<!-- 

Comment Type: annotation
Last Modified By: ptager
Last Modified Date: 2018-05-02T17:19:24.147-0400

Section is redundant with the section in the Overview topic

 -->

## Source Code Repository {#source-code-repository}

**Multiple Git Servers: In some cases, customers will have an existing git repository and want to keep using it.**

For these cases, the you can use git's support for multiple remote repositories. Day to day development would continue to happen in the your git repository. When a deployment is desired, you can simply push the latest code to the Cloud Manager git repository.

<!-- 

Comment Type: annotation
Last Modified By: ptager
Last Modified Date: 2018-05-02T17:20:46.002-0400

Looks like we lost some content, compared to the previous version

 -->

## Security and Privacy {#security-and-privacy}

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-04-21T02:38:21.417-0400

Query for Brad B.

 -->

## Pipeline Overview {#pipeline-overview}

Cloud Manager will support a single pipeline per program (definition above) which handles deployments to stage and production. ****

La rama git utilizada para las implementaciones de fase y producción es maestra.

>[!NOTE]
>
>It is a best practice to to use master as a git branch for stage and production, but you can use any of the branch while setting up the pipeline.

The single pipeline process is illustrated below:

![](assets/screen_shot_2018-04-30at30318pm.png)

### Understanding the Flow {#understanding-the-flow}

You can configure your pipeline from the [!UICONTROL Pipeline Settings] tile from Cloud Manager UI.

Consulte [Uso de Cloud Manager,](hhttps://helpx.adobe.com/experience-manager/cloud-manager/using/using-cloud-manager.html) para obtener más información.

El Administrador de implementación es responsable de configurar la canalización, es decir:

* asignación de rama de aplicación
* asignación de entornos de implementación
* defining test options

When doing so, you first select a branch from their git repository. A continuación, defina el activador que iniciará la canalización.

A continuación, puede definir los parámetros que controlan la implementación de producción.

Finalmente, podrá configurar los parámetros de prueba de rendimiento.

>[!NOTE]
>
>Para obtener más información sobre la configuración del comportamiento y las preferencias de la canalización, consulte la sección **Configuración de la canalización** en [Uso de Cloud Manager](using-cloud-manager.md).

### Help Resources {#help-resources}

Póngase en contacto con el consultor de éxito del cliente de los servicios gestionados de Adobe para obtener ayuda.

### Pasos siguientes {#the-next-steps}

Ahora tiene una mejor comprensión de los conceptos de Cloud Manager.

Para configurar el proyecto, el entorno y el equipo (usuario y funciones), consulte [Configuración de configuraciones generales para Cloud Manager](setting-configurations-for-cloud-manager.md).
