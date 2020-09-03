---
title: Uso del Asistente
description: Siga esta página para aprender a utilizar el asistente para crear un proyecto de aplicación AEM
translation-type: tm+mt
source-git-commit: 7146a41d64365c9de03d32f4fc4c33f9e366c244
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 9%

---


# Uso del Asistente {#using-wizard-to-create-an-aem-application-project}

Cuando los clientes se incorporan a Cloud Manager, se les proporciona un repositorio de Git vacío. Los clientes actuales de Adobe Managed Services (AMS) (o los clientes internos AEM que están migrando a AMS) generalmente ya tendrán su código de proyecto en git (u otro sistema de control de versiones) e importarán su proyecto en el repositorio de Git Cloud Manager. Sin embargo, los nuevos clientes no tienen proyectos existentes.

Para ayudar a que los nuevos clientes se inicien, Cloud Manager ahora puede crear un proyecto de AEM mínimo como punto de partida. Este proceso se basa en el [**AEM Arquetipo**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)del Proyecto.


Siga los pasos a continuación para crear un proyecto de aplicación AEM en Cloud Manager:

1. Una vez que inicie sesión en Cloud Manager y se complete la configuración básica del programa, se mostrará una tarjeta de llamada a la acción especial en la pantalla **Información general**, si el repositorio está vacío.

   ![](assets/image2018-10-3_14-29-44.png)

1. Haga clic en **Crear para** abrir un cuadro de diálogo que permite al usuario proporcionar los parámetros requeridos por el arquetipo de proyecto AEM. En su forma predeterminada, el cuadro de diálogo solicita dos valores:

   * **Título** : de forma predeterminada, se establece en el nombre del *Programa*

   * **Nuevo nombre** de rama: de forma predeterminada es *maestro*

   ![](assets/screen_shot_2018-10-08at55825am.png)

   El cuadro de diálogo tiene un cajón que se puede abrir haciendo clic en el control hacia la parte inferior del cuadro de diálogo. En su forma expandida, el cuadro de diálogo muestra todos los parámetros de configuración para el arquetipo. Muchos de estos parámetros tienen valores predeterminados que se generan en función del **Título**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Por ejemplo, si el **Título** es ***We.Finance***, el parámetro de ID de artefacto de la base se genera como ***com.wefinance***. Estos valores se pueden cambiar, si se desea.
   >
   >
   >Por ejemplo, puede cambiar del ***valor generado com.wefinance*** a ***net.weFinance***.

1. Haga clic en **Crear** en el paso anterior para crear el proyecto de inicio mediante el arquetipo y confirmarlo con la rama de git con nombre. Una vez hecho esto, puede configurar la canalización.