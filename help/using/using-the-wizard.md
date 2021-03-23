---
title: Uso del asistente
description: Siga esta página para aprender a utilizar el asistente para crear un proyecto de aplicación AEM
feature: Introducción
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 10%

---


# Uso del asistente {#using-wizard-to-create-an-aem-application-project}

Cuando los clientes están incorporados a Cloud Manager, se les proporciona un repositorio de Git vacío. Los clientes actuales de Adobe Managed Services (AMS) (o los clientes locales AEM que migran a AMS) generalmente ya tendrán su código de proyecto en git (u otro sistema de control de versiones) e importarán su proyecto al repositorio de Git de Cloud Manager. Sin embargo, los clientes nuevos no tienen proyectos existentes.

Para ayudar a poner en marcha nuevos clientes, Cloud Manager ahora puede crear un proyecto de AEM mínimo como punto de partida. Este proceso se basa en el [**AEM tipo de archivo del proyecto**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).


Siga los pasos a continuación para crear un proyecto de aplicación de AEM en Cloud Manager:

1. Una vez que inicie sesión en Cloud Manager y se complete la configuración básica del programa, se mostrará una tarjeta de llamada a la acción especial en la pantalla **Información general**, si el repositorio está vacío.

   ![](assets/image2018-10-3_14-29-44.png)

1. Haga clic en **Crear para** abrir un cuadro de diálogo que permite al usuario proporcionar los parámetros requeridos por el tipo de archivo del proyecto AEM. En su forma predeterminada, el cuadro de diálogo solicita dos valores:

   * **Título** : de forma predeterminada, se establece en el Nombre  *del programa.*

   * **Nuevo nombre**  de rama: de forma predeterminada, es  *maestro*

   ![](assets/screen_shot_2018-10-08at55825am.png)

   El cuadro de diálogo tiene un cajón que se puede abrir haciendo clic en el control hacia la parte inferior del cuadro de diálogo. En su forma expandida, el cuadro de diálogo muestra todos los parámetros de configuración del tipo de archivo. Muchos de estos parámetros tienen valores predeterminados que se generan en función del **Título**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Por ejemplo, si el **Título** es ***We.Finance***, el parámetro de identificación de artefactos de Maven base se genera como ***com.wefinance***. Si lo desea, puede cambiar estos valores.
   >
   >
   >Por ejemplo, puede cambiar del ***valor com.wefinance*** generado a ***net.wefinance***.

1. Haga clic en **Crear** en el paso anterior para crear el proyecto de inicio utilizando el tipo de archivo y confirme la rama de git con nombre. Una vez hecho esto, puede configurar la canalización.