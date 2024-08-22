---
title: Información de acceso al repositorio
description: Obtenga información sobre cómo acceder y administrar sus repositorios de Git administrados por Adobe mediante la administración de cuentas de Git de autoservicio desde Cloud Manager.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 31%

---

# Información de acceso al repositorio {#accessing-repos}

Obtenga información sobre cómo acceder y administrar sus repositorios de Git administrados por Adobe mediante la administración de cuentas de Git de autoservicio en Cloud Manager.

## Acceder a la información del repositorio desde la página Información general {#overview-page}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Vaya a la tarjeta **Canalizaciones** desde su página de **Resumen del programa**.

   ![Botón Información de acceso al repositorio en la tarjeta Entornos](assets/pipelines-card.png)

1. Haga clic en **Acceder a la info del repositorio**. En el cuadro de diálogo **Información del repositorio para...**, puede ver lo siguiente:

   * El nombre de usuario de Git.
   * La contraseña de Git.
   * La URL del repositorio de Git de Cloud Manager.
   * Comandos Git creados previamente para añadir un remoto a su repositorio Git rápidamente y enviar código.

   ![Ventana Información del repositorio](assets/access-repo-info.png)

1. Para acceder a la contraseña, debe generar una nueva. Haga clic en **`Generate password`**.

1. En el cuadro de diálogo **¿Está seguro?**, confirme la generación de contraseñas haciendo clic en **Generar contraseña**.

   ![Confirmar generación de contraseña](assets/confirm-password-generation.png)

1. En el campo **Contraseña**, se genera la contraseña. Haga clic en el icono Copiar para copiarlo en el portapapeles.

   * La generación de una contraseña invalida la contraseña anterior.
   * Cloud Manager no guarda la contraseña de acceso. Asegúrese de guardar esta contraseña de forma segura.
   * Si pierde la contraseña, debe generar una nueva.

   ![Ejemplo de una contraseña generada](assets/generated-password.png)

Con estas credenciales, puede clonar una copia local del repositorio, realizar cambios en ese repositorio local y, luego, confirmar cualquier cambio de código en el repositorio remoto de códigos en Cloud Manager.

>[!NOTE]
>
>* La opción **Acceder a la info del repositorio** está visible para los usuarios con el rol **Desarrollador**, el rol **Administrador de implementación** o ambos.
>* El botón **Información de acceso al repositorio** solo muestra la información de acceso al repositorio para los repositorios administrados por Adobe. La información de acceso de los [repositorios privados](private-repositories.md) no está disponible en Cloud Manager.

## Acceder a la información del repositorio desde la ventana Repositorios {#repositories-window}

El botón **Acceder a la info del repositorio** también está disponible en la barra de herramientas de la ventana [**Repositorios**](managing-repositories.md). Muestra la misma información sobre el acceso a repositorios administrados por Adobe.

## Revocar una contraseña de acceso {#revoke-password}

Puede revocar una contraseña de acceso en cualquier momento. [Crear un ticket de soporte para tal solicitud](https://experienceleague.adobe.com/es?support-solution=Experience+Manager&amp;support-tab=home&amp;lang=es#support).

El ticket se trata con alta prioridad y generalmente se revoca dentro de un día.
