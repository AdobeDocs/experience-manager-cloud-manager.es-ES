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

## Repositorio de códigos de origen {#source-code-repository}

**Varios Servidores** Git: En algunos casos, los clientes tendrán un repositorio Git existente y desean seguir usándolo.

En estos casos, puede utilizar la compatibilidad de git para varios repositorios remotos. El desarrollo diario continuaría ocurriendo en el repositorio de Git. Cuando desee una implementación, simplemente puede insertar el código más reciente en el repositorio de Git Cloud Manager.

<!-- 

Comment Type: annotation
Last Modified By: ptager
Last Modified Date: 2018-05-02T17:20:46.002-0400

Looks like we lost some content, compared to the previous version

 -->

## Seguridad y privacidad {#security-and-privacy}

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-04-21T02:38:21.417-0400

Query for Brad B.

 -->

## Información general de canalización {#pipeline-overview}

Cloud Manager admitirá una sola canalización por programa (definición anterior) que gestiona las implementaciones en fase y producción. ****

La rama git utilizada para las implementaciones de fase y producción es maestra.

>[!NOTE]
>
>Se recomienda utilizar master como rama de git para el escenario y la producción, pero se puede utilizar cualquiera de las ramas al configurar la tubería.

A continuación se ilustra el proceso de canalización única:

![](assets/screen_shot_2018-04-30at30318pm.png)

### Explicación del flujo {#understanding-the-flow}

Puede configurar la canalización desde el [!UICONTROL Pipeline Settings] mosaico desde la interfaz de usuario de Cloud Manager.

Consulte [Uso de Cloud Manager,](hhttps://helpx.adobe.com/experience-manager/cloud-manager/using/using-cloud-manager.html) para obtener más información.

El Administrador de implementación es responsable de configurar la canalización, es decir:

* asignación de rama de aplicación
* asignación de entornos de implementación
* definición de opciones de prueba

Al hacerlo, primero se selecciona una rama del repositorio de Git. A continuación, defina el activador que iniciará la canalización.

A continuación, puede definir los parámetros que controlan la implementación de producción.

Finalmente, podrá configurar los parámetros de prueba de rendimiento.

>[!NOTE]
>
>Para obtener más información sobre la configuración del comportamiento y las preferencias de la canalización, consulte la sección **Configuración de la canalización** en [Uso de Cloud Manager](using-cloud-manager.md).

### Recursos de ayuda {#help-resources}

Póngase en contacto con el consultor de éxito del cliente de los servicios gestionados de Adobe para obtener ayuda.

### Pasos siguientes {#the-next-steps}

Ahora tiene una mejor comprensión de los conceptos de Cloud Manager.

Para configurar el proyecto, el entorno y el equipo (usuario y funciones), consulte [Configuración de configuraciones generales para Cloud Manager](setting-configurations-for-cloud-manager.md).
