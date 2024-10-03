---
title: Adición de repositorios externos en Cloud Manager (usuario que los adoptó por primera vez)
description: Obtenga información sobre cómo añadir un repositorio externo a Cloud Manager. Cloud Manager admite la integración con repositorios de GitHub, GitLab y Bitbucket.
source-git-commit: 054c214be3c8c6e8a8bd4691b70ae2098263ef5b
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 6%

---


# Adición de repositorios externos en Cloud Manager {#external-repositories}

Obtenga información sobre cómo añadir un repositorio externo a Cloud Manager. Cloud Manager admite la integración con repositorios de GitHub, GitLab y Bitbucket.

>[!NOTE]
>
>Esta funcionalidad solo está disponible para [el programa de clientes pioneros](/help/release-notes/current.md#early-adoption).

## Configuración de un repositorio externo

La configuración de un repositorio externo en Cloud Manager consta de tres pasos:

1. [Agregar un repositorio externo](#add-external-repo) a un programa seleccionado.
1. Proporcione un token de acceso al repositorio externo.
1. Valide la propiedad del repositorio externo.


## Añadir un repositorio externo {#add-ext-repo}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización adecuada.

1. En la consola **[Mis programas](/help/getting-started/navigation.md#my-programs-console), seleccione el programa al que desea vincular un repositorio externo.


1. En el menú lateral, en **Servicios**, seleccione ![Icono de carpeta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Repositorios**.

   ![La página de repositorios](/help/managing-code/assets/repositories-tab.png)

1. Cerca de la esquina superior derecha de la página **Repositorios**, haga clic en **Agregar repositorio**.

1. En el cuadro de diálogo **Agregar repositorio**, seleccione **Repositorio privado** para vincular un repositorio Git externo a su programa.

   ![Añadir su propio repositorio](/help/managing-code/assets/repositories-private-repo-type.png)

1. En cada campo respectivo, proporcione los siguientes detalles sobre el repositorio:

   | Campo | Descripción |
   | --- | --- |
   | **Nombre de repositorio** | Requerido. Un nombre expresivo para el nuevo repositorio. |
   | **URL del repositorio** | Requerido. La URL del repositorio.<br><br> Si utiliza un repositorio alojado en GitHub, la ruta debe finalizar en `.git`.<br>Por ejemplo, *`https://github.com/org-name/repo-name.git`* (la ruta de URL es solo para fines ilustrativos).<br><br>Si está usando un repositorio externo, debe usar el siguiente formato de ruta de URL:<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> o<br>`https://self-hosted-domain/org-name/repo-name.git`<br>Y coincidir con su proveedor Git. |
   | **Seleccionar tipo de repositorio** | Requerido. Seleccione el tipo de repositorio que está usando: **GitHub**, **GitLab** o **BitBucket**. Si la ruta de URL del repositorio anterior incluye el nombre del proveedor de Git, como GitLab o Bitbucket, el tipo de repositorio ya estará preseleccionado. |
   | **Descripción** | Opcional. Una descripción detallada del repositorio. |

1. Seleccione **Guardar** para agregar el repositorio.

1. En el cuadro de diálogo **Validación de propiedad del repositorio privado**, proporcione un token de acceso para validar la propiedad del repositorio externo y poder obtener acceso a él.

   ![Seleccionar un token de acceso existente para un repositorio](/help/managing-code/assets/repositories-exisiting-access-token.png)
   *Seleccionando un token de acceso existente para un repositorio BitBucket.*

   | Tipo de token | Descripción |
   | --- | --- |
   | **Usar token de acceso existente** | Si ya ha proporcionado un token de acceso al repositorio para su organización y tiene acceso a varios repositorios, puede seleccionar un token existente. Utilice la lista desplegable **Nombre de token** para elegir el token que desea aplicar al repositorio. De lo contrario, agregue un nuevo token de acceso. |
   | **Agregar nuevo token de acceso** | **Tipo de repositorio: GitHub**<br>· En el campo de texto **Nombre de token**, escriba un nombre para el token de acceso que está creando.<br>· Cree un token de acceso personal siguiendo las instrucciones de la [documentación de GitHub](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).<br>· Permisos necesarios:<br>  · `Read access to metadata`.<br>  · `Read and write access to code and pull requests`.<br>· En el campo **Token de acceso**, pegue el token que acaba de crear. |
   |  | **Tipo de repositorio: GitLab**<br>· En el campo de texto **Nombre de token**, escriba un nombre para el token de acceso que está creando.<br>· Cree un token de acceso personal siguiendo las instrucciones de la [documentación de GitLab](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html).<br>· Permisos necesarios:<br>  · `api`<br>  · `read_api`<br>  · `read_repository`<br>  · `write_repository`<br>· En el campo **Token de acceso**, pegue el token que acaba de crear. |
   |  | **Tipo de repositorio: Bitbucket**<br>· En el campo de texto **Nombre de token**, escriba un nombre para el token de acceso que está creando.<br>· Cree un token de acceso al repositorio con la [documentación de Bitbucket](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<br>· Permisos necesarios:<br>  · `Read and write access to code and pull requests`. |

   >[!NOTE]
   >
   >La característica **Agregar nuevo token de acceso** se encuentra actualmente en la fase de adopción anticipada. Se están planificando funciones adicionales. Como resultado, los permisos necesarios para los tokens de acceso pueden cambiar. Además, la interfaz de usuario para administrar tokens se puede actualizar, lo que incluye potencialmente características como las fechas de caducidad de los tokens. Además, realiza comprobaciones automatizadas para garantizar que los tokens vinculados a repositorios siguen siendo válidos.

1. Haga clic en **Validar**.

Después de la validación, el repositorio externo está listo para usarse y se vinculará a una canalización.

## Vinculación de un repositorio externo validado a una canalización {#validate-ext-repo}

1. Agregar o editar una canalización:
   * [Agregar una canalización de producción](/help/using/production-pipelines.md)
   * [Agregar canalizaciones que no sean de producción](/help/using/non-production-pipelines.md)
   * [Edición de una canalización](/help/using/managing-pipelines.md#editing-pipelines)

   ![Repositorio de código fuente de la canalización y rama Git](/help/managing-code/assets/pipeline-repo-gitbranch.png)
   *Agregar cuadro de diálogo Canalización que no sea de producción con el repositorio seleccionado y la rama Git,*

1. Al agregar o editar una canalización, para especificar la ubicación de **Source Code** para su canalización nueva o existente, elija el repositorio externo que desee utilizar en la lista desplegable **Repositorio**.

1. En la lista desplegable **Rama de Git**, seleccione la rama como origen de la canalización.

1. Haga clic en **Guardar**.


>[!TIP]
>
>Para obtener más información sobre la administración de repositorios en Cloud Manager, consulte el documento [Repositorios de Cloud Manager](/help/managing-code/managing-repositories.md).


## Limitaciones

* Los repositorios externos no se pueden vincular a las canalizaciones de configuración.
* Las canalizaciones que usan repositorios externos (excepto los repositorios alojados en GitHub) y la opción **Déclencheur de implementación** [!UICONTROL **En los cambios de Git**], las déclencheur no se inician automáticamente. Se deben iniciar manualmente.
