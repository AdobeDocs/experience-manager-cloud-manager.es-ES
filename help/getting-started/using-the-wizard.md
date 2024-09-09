---
title: Uso del Asistente para nuevo proyecto
description: AEM Siga esta página para aprender a utilizar el asistente con el fin de crear un proyecto de aplicación para la creación de un proyecto de aplicación para la creación de un proyecto de aplicación de la.
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: 7bc874a8dd14544c22201ef2c470faab84d31f8b
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 25%

---


# Uso del asistente Nuevo proyecto {#using-the-wizard}

Cuando se incorporó a Cloud Manager como nuevo cliente, se le proporcionó un repositorio de Git vacío. Para ayudarle a empezar, Cloud Manager ofrece un asistente para crear un proyecto de AEM mínimo basado en el [Arquetipo de proyecto de AEM](https://github.com/adobe/aem-project-archetype) como punto de partida.

Siga estos pasos para crear un proyecto de AEM con el asistente.

1. Inicie sesión en Cloud Manager en [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) y seleccione la organización adecuada.

1. Si todavía no lo ha hecho, [cree el programa](program-setup.md). Cuando se crea el programa, Cloud Manager detecta que los repositorios aún no están configurados. Aparecerá una tarjeta de llamada a acción especial en la pantalla **Información general**.

   ![Creación de llamada a acción del proyecto](/help/assets/image2018-10-3_14-29-44.png)

1. Haga clic en **Crear** para iniciar el asistente y proporcionar valores importantes.

   * **Título** - El título del proyecto. De forma predeterminada, se establece en el nombre del programa.
   * **Nuevo nombre de rama**: la rama inicial de sus repositorios Git. De manera predeterminada, es `main`.

   ![Valores del proyecto](/help/assets/screen_shot_2018-10-08at55825am.png)

1. El cuadro de diálogo tiene un cajón que se puede abrir haciendo clic en el controlador situado hacia la parte inferior. AEM En su forma expandida, el cuadro de diálogo muestra todos los parámetros de configuración para el arquetipo de proyecto de la. Estos parámetros tienen valores predeterminados que se generan en función del **Título** que ya ha proporcionado y no requieren modificación. Se explican aquí para mayor información.

   ![Parámetros detallados del arquetipo](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Haga clic en **Crear** para crear el proyecto de inicio utilizando el tipo de archivo y confirmar en la rama Git con nombre.

Ahora tiene un proyecto base. Es hora de configurar sus canalizaciones.

## Clientes existentes o que migran {#existing-migrating}

Si es cliente actual de Adobe Managed Services AEM (AMS) o cliente local de que está migrando, es probable que ya tenga código de proyecto en Git o en otro sistema de control de versiones.

En estos casos, puede importar el proyecto en el repositorio Git de Cloud Manager.
