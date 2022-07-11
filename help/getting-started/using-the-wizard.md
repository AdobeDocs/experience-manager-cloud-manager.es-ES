---
title: Uso del Asistente para nuevo proyecto
description: Siga esta página para aprender a utilizar el asistente para crear un proyecto de aplicación AEM
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: cb791a4f148ba394687b5e824b75fe1386d83c18
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# Uso del Asistente para nuevo proyecto {#using-the-wizard}

Cuando se incorpora a Cloud Manager como nuevo cliente, se le proporciona un repositorio de Git vacío. Para ayudarle a empezar, Cloud Manager ofrece un asistente para crear un proyecto de AEM mínimo basado en la variable [Tipo de archivo del proyecto AEM](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype) como punto de partida.

Siga estos pasos para crear un proyecto AEM con el asistente.

1. Inicie sesión en Cloud Manager en [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) y seleccione la organización adecuada.

1. Si todavía no lo ha hecho, [cree el programa.](program-setup.md) Una vez creado el programa, Cloud Manager reconocerá que los repositorios aún no están configurados y que se muestra una tarjeta de llamada a la acción especial en la **Información general** en el Navegador.

   ![Crear llamada a acción del proyecto](/help/assets/image2018-10-3_14-29-44.png)

1. Haga clic en **Crear** para iniciar el asistente y proporcionar valores importantes.

   * **Título** - Este es el título del proyecto y de forma predeterminada se establece en el nombre del programa.
   * **Nuevo nombre de rama** - Esta es la rama inicial de sus repositorios Git y de forma predeterminada será `main`.

   ![Valores del proyecto](/help/assets/screen_shot_2018-10-08at55825am.png)

1. El cuadro de diálogo tiene un cajón que se puede abrir haciendo clic en el control hacia la parte inferior. En su formulario expandido, el cuadro de diálogo muestra todos los parámetros de configuración para el tipo de archivo del proyecto AEM. Estos parámetros tienen valores predeterminados que se generan en función de la variable **Título** ya ha proporcionado y no requiere modificación. Se explican aquí para su información.

   ![Parámetros detallados del tipo de archivo](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Haga clic en **Crear** para crear el proyecto de inicio, utilice el tipo de archivo y confirme la rama de git con nombre.

¡Ahora tiene un proyecto base! Ahora puede configurar sus canalizaciones.

## Clientes existentes o que migran {#existing-migrating}

Si es cliente actual de Adobe Managed Services (AMS) o cliente local AEM que está migrando, es probable que ya tenga código de proyecto en Git u otro sistema de control de versiones.

En estos casos, importará el proyecto en el repositorio de Git de Cloud Manager.
