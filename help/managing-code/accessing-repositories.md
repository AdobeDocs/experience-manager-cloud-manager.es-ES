---
title: Información de acceso al repositorio
description: Obtenga información sobre cómo acceder y administrar sus repositorios de Git administrados por Adobe mediante la administración de cuentas de Git de autoservicio desde Cloud Manager.
source-git-commit: b15ef71ae24f51811798d2d25c8f75320e21c01f
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 11%

---


# Información de acceso al repositorio {#accessing-repos}

Obtenga información sobre cómo acceder y administrar sus repositorios de Git administrados por Adobe mediante la administración de cuentas de Git de autoservicio desde Cloud Manager.

## Acceso a Información de Repositorio desde la Página Información General {#overview-page}

Cloud Manager facilita la recuperación de la información de acceso al repositorio para repositorios administrados por el Adobe mediante **Acceder a info del repositorio** disponible de forma destacada en la tarjeta de canalización.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Vaya a **Canalizaciones** Tarjeta de su **Resumen del programa** página.

   ![Botón Acceder a la info del repositorio en la tarjeta Entornos](assets/pipelines-card.png)

1. Haga clic o pulse en **Acceder a info del repositorio** para abrir el **Información del repositorio** Cuadro de diálogo y vista:

   * El nombre de usuario de Git.
   * La contraseña de Git.
   * La dirección URL del repositorio de Git de Cloud Manager.
   * Comandos Git pregenerados para añadir rápidamente un remoto a su repositorio de Git y código push.

   ![Ventana Información del repositorio](assets/access-repo-info.png)

1. Para acceder a la contraseña, se debe generar una nueva contraseña. Para ello, toque o haga clic en **Generar contraseña** botón.

1. Confirme la generación de contraseñas en **¿Seguro que...?** al tocar o hacer clic en **Generar contraseña**.

   ![Confirmar generación de contraseñas](assets/confirm-password-generation.png)

1. La contraseña se genera y es visible para copiarla en **Contraseña** field.

   * La generación de una contraseña invalidará la contraseña anterior.
   * Cloud Manager no guardará la contraseña. Es su responsabilidad guardar esta contraseña de forma segura.
   * Como Cloud Manager no guarda la contraseña, si la pierde, debe volver a generar una nueva.

   ![Ejemplo de contraseña generada](assets/generated-password.png)

Con estas credenciales, puede clonar una copia local del repositorio, realizar cambios en ese repositorio local y, cuando esté listo, volver a enviar cualquier cambio de código al repositorio de código remoto en Cloud Manager.

>[!NOTE]
>
>* La opción **Acceder a la info del repositorio** es visible para los usuarios con funciones **Desarrollador** o **Administrador de implementación**.
>* El **Acceder a info del repositorio** El botón solo muestra la información de acceso al repositorio para repositorios administrados por Adobe. Acceder a información sobre [repositorios privados](private-repositories.md) no está disponible en Cloud Manager.

## Acceder a la información del repositorio desde la ventana Repositorios {#repositories-window}

Un **Acceder a info del repositorio** también está disponible en la barra de herramientas del [**Repositorios** ventana.](managing-repositories.md) muestra la misma información sobre el acceso a repositorios administrados por Adobe.

## Revocar una contraseña de acceso {#revoke-password}

Puede revocar una contraseña de acceso en cualquier momento. Para ello, por favor [cree un ticket de asistencia para esta solicitud.](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home#support)

El billete se tratará con alta prioridad y debe ser revocado en el plazo de un día.