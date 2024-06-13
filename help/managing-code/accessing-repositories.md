---
title: Información de acceso al repositorio
description: Obtenga información sobre cómo acceder y gestionar sus repositorios de Git administrados por Adobe mediante la administración de cuentas de Git de autoservicio desde Cloud Manager.
source-git-commit: b15ef71ae24f51811798d2d25c8f75320e21c01f
workflow-type: ht
source-wordcount: '400'
ht-degree: 100%

---


# Información de acceso al repositorio {#accessing-repos}

Obtenga información sobre cómo acceder y gestionar sus repositorios de Git administrados por Adobe mediante la administración de cuentas de Git de autoservicio desde Cloud Manager.

## Acceso a la información del repositorio desde la página de información general {#overview-page}

Cloud Manager facilita la recuperación de la información de acceso al repositorio para los repositorios administrados por Adobe mediante el botón **Acceder a la info del repositorio** disponible de forma destacada en la tarjeta de canalizaciones.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Vaya a la tarjeta de **Canalizaciones** desde la página **Información general del programa**.

   ![Botón Información de acceso al repositorio en la tarjeta Entornos](assets/pipelines-card.png)

1. Pulse o haga clic en el botón **Información de acceso al repositorio** para abrir el cuadro de diálogo **Información del repositorio** y ver lo siguiente:

   * El nombre de usuario de Git.
   * La contraseña de Git.
   * La dirección URL del repositorio de Git de Cloud Manager.
   * Comandos de Git prediseñados para añadir rápidamente un remoto a su repositorio Git y enviar códigos.

   ![Ventana Información del repositorio](assets/access-repo-info.png)

1. Para acceder a la contraseña, debe generar una nueva. Para ello, pulse o haga clic en el botón **Generar contraseña**.

1. Confirme la generación de la contraseña en el cuadro de diálogo **¿Seguro?** pulsando o haciendo clic en **Generar contraseña**.

   ![Confirmar generación de contraseña](assets/confirm-password-generation.png)

1. La contraseña se genera y es visible para copiarla en el campo **Contraseña**.

   * La generación de la contraseña invalida la anterior.
   * Cloud Manager no guarda la contraseña. Es su responsabilidad guardarla de forma segura.
   * Ya que Cloud Manager no guarda la contraseña, si la olvida, deberá generar una nueva.

   ![Ejemplo de una contraseña generada](assets/generated-password.png)

Con estas credenciales, puede clonar una copia local del repositorio, realizar cambios en ese repositorio local y, luego, confirmar cualquier cambio de código en el repositorio remoto de códigos en Cloud Manager.

>[!NOTE]
>
>* La opción **Información de acceso al repositorio** es visible para los usuarios con las funciones **Desarrollador** o **Administrador de implementación**.
>* El botón **Información de acceso al repositorio** solo muestra la información de acceso al repositorio para los repositorios administrados por Adobe. La información de acceso de los [repositorios privados](private-repositories.md) no está disponible en Cloud Manager.

## Información de acceso al repositorio desde la ventana Repositorios {#repositories-window}

El botón **Información de acceso al repositorio** también está disponible en la barra de herramientas de la ventana [**Repositorios**.](managing-repositories.md) muestra la misma información sobre el acceso a los repositorios administrados por Adobe.

## Revocar una contraseña de acceso {#revoke-password}

Puede revocar una contraseña de acceso en cualquier momento. Para ello, [cree un ticket de asistencia para esta solicitud.](https://experienceleague.adobe.com/es?support-solution=Experience+Manager&amp;support-tab=home&amp;lang=es#support)

El ticket tiene prioridad y debería revocarse en un día.