---
title: Administración de tokens de acceso en Cloud Manager
description: Obtenga información sobre cómo ver, editar y eliminar los tokens de acceso utilizados para Traer su propio Git en Cloud Manager en Adobe Managed Services.
exl-id: 873aad0b-d7c6-4bc3-a70d-bbfdc1e02193
source-git-commit: 651d9fc9964d599cb51556f7b6ba255fe8092d7f
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 3%

---

# Administración de tokens de acceso para repositorios externos {#manage-access-tokens}

Cloud Manager utiliza tokens de acceso para administrar repositorios alojados en plataformas Git externas. Anteriormente, si un token caducaba, el repositorio asociado tenía que volver a incorporarse para permanecer operativo.

Ahora, **Administrar tokens de acceso** le permite administrar los tokens de manera más eficiente. Puede ver, cambiar el nombre o quitar tokens conectados a proveedores de Git externos admitidos, como GitHub Enterprise, GitLab, Bitbucket y Azure DevOps.

Consulte también [Agregar repositorios externos en Cloud Manager](/help/managing-code/external-repositories.md).

## Ver tokens de acceso {#view-access-tokens}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización adecuada.
1. En la consola **[Mis programas](/help/getting-started/navigation.md#my-programs-console)**, seleccione el programa cuyo token de acceso Traer su propio Git desee administrar.
1. En el menú lateral, en **Programa**, haga clic en ![Icono de esquema de carpeta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositorios**.
1. Cerca de la esquina superior derecha de la página, haga clic en **Administrar tokens de acceso**.

   El botón **Administrar tokens de acceso** solo está visible si su programa usa la función Traer su propio Git.

   ![En el cuadro de diálogo Administrar tokens de acceso se muestra un token activo y un token inactivo](/help/managing-code/assets/access-tokens-manage.png)

1. En el cuadro de diálogo **Administrar tokens de acceso**:
   * Se muestran todos los tokens de acceso.
   * Puede **editar** cualquier token.
   * Solo puede **eliminar** los tokens que *no están en uso*. Si un token está en uso, el botón ![Eliminar icono de esquema](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) está deshabilitado.

## Edición de un token de acceso {#edit-access-tokens}

1. En el cuadro de diálogo **Administrar tokens de acceso**, a la derecha del nombre de un token, haga clic en ![Editar icono](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).
1. En el cuadro de diálogo **Editar token de acceso**, actualice el valor **Nombre de token**, el **Token de acceso** o ambos.

   ![Cuadro de diálogo Editar token de acceso](/help/managing-code/assets/access-tokens-edit.png)

1. Si el **Token de acceso** está en uso, aparece una notificación avisándole de que todos los repositorios asociados se vuelven a validar automáticamente después de la actualización.

1. Haga clic en **Actualizar** para guardar los cambios.

## Eliminación de un token de acceso {#delete-access-token}

1. En el cuadro de diálogo **Administrar tokens de acceso**, a la derecha del nombre de un token, haga clic en ![Eliminar icono](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)

   El icono está deshabilitado (![Eliminar icono de esquema](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)) para los tokens que se están utilizando en ese momento.

1. En **Eliminar token de acceso**, haga clic en **Eliminar** para quitar el token de forma permanente.
