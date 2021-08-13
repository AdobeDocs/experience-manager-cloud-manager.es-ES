---
title: Acceso a repositorios
seo-title: Acceso a repositorios
description: Esta página describe cómo puede acceder y administrar el repositorio Git.
seo-description: Siga esta página para aprender a acceder y administrar su repositorio de Git.
feature: Repositorios de Git
exl-id: 403fc93d-60fc-4439-8c9d-0a512ca34458
source-git-commit: 5bbe76a46b7a15ccbab85c4487d2a20aaf59a4e7
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 4%

---

# Acceso a repositorios {#accessing-repos}

Puede acceder a su repositorio Git y administrarlo mediante la administración de cuentas Git de autoservicio desde la interfaz de usuario de Cloud Manager.

## Uso de la administración de cuentas de Git de autoservicio {#self-service-git}

Utilice el botón **Access Repo Info** disponible en la interfaz de usuario de Cloud Manager, de forma más destacada en la tarjeta de canalización.

1. Vaya a la tarjeta **Canalizaciones** desde la página **Información general del programa**.

1. Verá la opción **Access Repo Info** para acceder y administrar su repositorio Git.

   ![](assets/access-repo1.png)

   Además, si selecciona la pestaña **Non-Production** canalización, también verá la opción **Access Repo Info**.

   ![](assets/access-repo-nonprod.png)


   >[!NOTE]
   >La opción **Access Repo Info** es visible para los usuarios con la función de Desarrollador o Administrador de implementación. Al hacer clic en este botón, se abre un cuadro de diálogo que permite al usuario encontrar la URL de su repositorio Git de Cloud Manager junto con su nombre de usuario y contraseña.

   ![](assets/access-repo-create.png)

   Las consideraciones importantes para administrar su Git en Cloud Manager son:

   * **URL**: La URL del repositorio
   * **Nombre de usuario**: El nombre de usuario
   * **Contraseña**: Valor que se muestra cuando se hace clic en el botón **Generar contraseña**.


      >[!NOTE]
      >Un usuario puede extraer una copia de su código y realizar cambios en el repositorio de código local. Cuando esté listo, el usuario puede devolver los cambios de código al repositorio de código remoto en Cloud Manager.
