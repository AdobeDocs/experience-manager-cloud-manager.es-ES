---
title: Explicación de conceptos antes de utilizar el Administrador de nube
seo-title: Explicación de conceptos antes de utilizar el Administrador de nube
description: nulo
seo-description: nulo
page-status-flag: no activado nunca
uuid: 55 cc 551 a-e 812-4102-96 c 8-13 d 2 cdd 79 c 84
contentOwner: jsyal
discoiquuid: c 3 fd 3 f 4 e -0 b 57-4377-b 923-a 440 c 74773 d 8
preview: verdadero
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Explicación de conceptos antes de utilizar el Administrador de nube{#understanding-concepts-before-using-cloud-manager}

Esta sección proporciona conceptos y terminologías que es bueno saber antes de trabajar en Cloud Manager y abarca los siguientes temas:

* **Entorno de implementación**
* **Repositorio de código fuente**
* **Seguridad y privacidad**
* **Información general de Pipeline**
* **Recursos de ayuda**

## Entorno de implementación {#deployment-environment}

Puede ser nuevo en Adobe Experience Manager (AEM) 6.4 o necesitar una actualización a la versión de AEM 6.4.

Si es una novedad de AEM 6.4, ya tiene acceso a Cloud Manager.

Si es cliente existente, debe actualizar a AEM 6.4 para tener acceso a Cloud Manager. Puede empezar a utilizar Cloud Manager, una vez que reciba la dirección URL y las credenciales de los ingenieros de éxito del cliente (CSE).

<!-- 

Comment Type: annotation
Last Modified By: ptager
Last Modified Date: 2018-05-02T17:19:24.147-0400

Section is redundant with the section in the Overview topic

 -->

## Repositorio de código fuente {#source-code-repository}

**Varios servidores GIT**: En algunos casos, los clientes tendrán un repositorio de git existente y desean seguir usándolo.

Para estos casos, puede utilizar la compatibilidad de git con varios repositorios remotos. El desarrollo día a día seguirá produciéndose en el repositorio de git. Cuando se desee una implementación, simplemente puede insertar el código más reciente en el repositorio de git de Cloud Manager.

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

## Información general de Pipeline {#pipeline-overview}

El Administrador de nube admite un único flujo por programa (definición más arriba) que gestiona las implementaciones en fase y producción. ****

La ramificación de git utilizada para las implementaciones de fase y producción es maestra.

>[!NOTE]
>
>Se recomienda utilizar la maestra como rama git para el escenario y la producción, pero puede utilizar cualquier rama al configurar la canalización.

A continuación se muestra el proceso de flujo único:

![](assets/screen_shot_2018-04-30at30318pm.png)

### Explicación del flujo {#understanding-the-flow}

Puede configurar su flujo desde [!UICONTROL Pipeline Settings] el mosaico desde la interfaz de usuario de Cloud Manager.

Consulte [Uso de Experience Cloud Manager](hhttps://helpx.adobe.com/experience-manager/cloud-manager/using/using-cloud-manager.html) para obtener más información.

El Administrador de implementación es responsable de configurar la canalización, es decir:

* asignar rama de aplicación
* asignar entornos de implementación
* definir opciones de prueba

Al hacerlo, primero selecciona una rama en su repositorio de git. A continuación, defina el activador que iniciará la canalización.

A continuación, puede definir los parámetros que controlan la implementación de producción.

Finalmente, podrá configurar los parámetros de prueba de rendimiento.

>[!NOTE]
>
>Para obtener información sobre cómo configurar el comportamiento y las preferencias para su flujo, consulte **la sección de** configuración de Pipeline en [Uso de Cloud Manager](using-cloud-manager.md).

### Recursos de ayuda {#help-resources}

Póngase en contacto con el ingeniero de éxito del cliente de servicios gestionados de Adobe para obtener soporte.

### Pasos siguientes {#the-next-steps}

Ahora tiene mejor comprensión de los conceptos de Cloud Manager.

Para configurar el proyecto, el entorno y el equipo (usuario y funciones), consulte [Configuración general configuraciones para el Administrador de nube](setting-configurations-for-cloud-manager.md).
