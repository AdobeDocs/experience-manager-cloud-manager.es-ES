---
title: Uso del Asistente para nuevos proyectos
description: Siga esta página para aprender a utilizar el asistente con el fin de crear un proyecto de aplicación de AEM
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: cb791a4f148ba394687b5e824b75fe1386d83c18
workflow-type: ht
source-wordcount: '330'
ht-degree: 100%

---


# Uso del Asistente para nuevos proyectos {#using-the-wizard}

Cuando se incorpora a Cloud Manager como nuevo cliente, se le proporciona un repositorio de Git vacío. Para ayudarle a empezar, Cloud Manager ofrece un asistente para crear un proyecto de AEM mínimo basado en el [Arquetipo de proyecto de AEM](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype) como punto de partida.

Siga estos pasos para crear un proyecto de AEM con el asistente.

1. Inicie sesión en Cloud Manager en [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) y seleccione la organización adecuada.

1. Si todavía no lo ha hecho, [cree el programa.](program-setup.md) Una vez hecho esto, Cloud Manager reconocerá que los repositorios aún no están configurados y se mostrará una tarjeta de llamada a acción especial en la pantalla **Información general**.

   ![Creación de llamada a acción del proyecto](/help/assets/image2018-10-3_14-29-44.png)

1. Haga clic en **Crear** para iniciar el asistente y proporcionar valores importantes.

   * **Título**: este es el título del proyecto y se establece en el nombre del programa de forma predeterminada.
   * **Nuevo nombre de rama**: esta es la rama inicial de sus repositorios de Git y, de forma predeterminada, será `main`.

   ![Valores del proyecto](/help/assets/screen_shot_2018-10-08at55825am.png)

1. El cuadro de diálogo tiene un cajón que se puede abrir haciendo clic en el controlador situado hacia la parte inferior. En su forma expandida, el cuadro de diálogo muestra todos los parámetros de configuración para el arquetipo de proyecto de AEM. Estos parámetros tienen valores predeterminados que se generan en función del **Título** que ya ha proporcionado y no requieren modificación. Se explican aquí para mayor información.

   ![Parámetros detallados del arquetipo](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Haga clic en **Crear** para crear el proyecto de inicio utilizando el arquetipo y confirmar en la rama de Git con nombre.

Ahora tiene un proyecto base. Ya puede configurar sus canalizaciones.

## Clientes existentes o que migran {#existing-migrating}

Si es cliente actual de Adobe Managed Services (AMS) o cliente On-Ppremise de AEM que está migrando, es probable que ya tenga código de proyecto en Git u otro sistema de control de versiones.

En estos casos, importará el proyecto en el repositorio de Git de Cloud Manager.
