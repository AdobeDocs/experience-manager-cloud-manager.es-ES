---
title: Añadir repositorios externos en Cloud Manager (primeros usuarios)
description: Obtenga información sobre cómo añadir un repositorio administrado a Adobe en Cloud Manager. Cloud Manager admite la integración con repositorios de GitHub, GitLab y Bitbucket.
exl-id: 4500cacc-5e27-4bbb-b8f6-5144dac7e6da
source-git-commit: e7e2268f866105970e02d4bc54c46613749e5ac0
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Añadir repositorios privados en Cloud Manager {#external-repositories}

Obtenga información sobre cómo añadir un repositorio administrado a Adobe en Cloud Manager. Cloud Manager admite la integración con repositorios de GitHub, GitLab y Bitbucket.

>[!NOTE]
>
>Esta funcionalidad solo está disponible para [el programa de clientes pioneros](/help/release-notes/current.md#early-adoption).

## Configurar un repositorio externo

La configuración de un repositorio externo en Cloud Manager consta de tres pasos:

1. [Añada un repositorio externo](#add-external-repo) a un programa seleccionado.
1. Proporcione un token de acceso al repositorio externo.
1. Valide la propiedad del repositorio externo.


## Añadir un repositorio externo {#add-ext-repo}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización adecuada.

1. En la consola **[Mis programas](/help/getting-started/navigation.md#my-programs-console), seleccione el programa al que desea vincular un repositorio externo.


1. En el menú lateral, en **Servicios**, seleccione ![Icono de carpeta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Repositorios**.

   ![La página Repositorios](/help/managing-code/assets/repositories-tab.png)

1. Cerca de la esquina superior derecha de la página **Repositorios**, haga clic en **Añadir repositorio**.

1. En el cuadro de diálogo **Añadir repositorio**, seleccione **Repositorio privado** para vincular un repositorio de Git externo a su programa.

   ![Añadir su propio repositorio](/help/managing-code/assets/repositories-private-repo-type.png)

1. En cada campo respectivo, proporcione los siguientes detalles sobre el repositorio:

   | Campo | Descripción |
   | --- | --- |
   | **Nombre del repositorio** | Obligatorio. Un nombre expresivo para el nuevo repositorio. |
   | **URL del repositorio** | Obligatorio. La URL del repositorio.<br><br> Si utiliza un repositorio alojado en GitHub, la ruta debe finalizar en `.git`.<br>Por ejemplo, *`https://github.com/org-name/repo-name.git`* (la ruta de URL es solo para fines ilustrativos).<br><br>Si va a usar un repositorio externo, éste debe usar el siguiente formato de ruta de URL: <br>`https://git-vendor-name.com/org-name/repo-name.git`<br> o <br>`https://self-hosted-domain/org-name/repo-name.git`<br> Y coincidir con su proveedor Git. |
   | **Seleccionar tipo de repositorio** | Obligatorio. Seleccione el tipo de repositorio que va a usar: **GitHub**, **GitLab** o **BitBucket**. Si la ruta de URL del repositorio anterior incluye el nombre del proveedor de Git, como GitLab o Bitbucket, el tipo de repositorio ya estará preseleccionado. |
   | **Descripción** | Opcional. Breve descripción del repositorio. |

1. Seleccione **Guardar** para añadir el repositorio. 

1. En el cuadro de diálogo **Validación de la propiedad del repositorio privado**, proporcione un token de acceso para validar la propiedad del repositorio externo afín de poder acceder a él.

   ![Selección de un token de acceso existente para un repositorio](/help/managing-code/assets/repositories-exisiting-access-token.png)
   *Selección de un token de acceso existente para un repositorio de BitBucket.*

   | Tipo de token | Descripción |
   | --- | --- |
   | **Usar token de acceso existente** | Si ya ha proporcionado un token de acceso al repositorio para su organización y tiene acceso a varios repositorios, puede seleccionar un token existente. Utilice la lista desplegable **Nombre de token** para elegir el token que desea aplicar al repositorio. De lo contrario, añada un nuevo token de acceso. |
   | **Añadir nuevo token de acceso** | **Tipo de repositorio: GitHub**<br>• En el campo de texto **Nombre de token**, escriba un nombre para el token de acceso que va a crear.<br>• Cree un token de acceso personal siguiendo las instrucciones de la [documentación de GitHub](https://docs.github.com/es/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).<br>• Permisos necesarios:<br> •  `Read access to metadata`.<br>  • `Read and write access to code and pull requests`.<br>• En el campo **Token de acceso**, pegue el token que acaba de crear. |
   |  | **Tipo de repositorio: GitLab**<br>•  En el campo de texto **Nombre de token**, escriba un nombre para el token de acceso que va a crear.<br>• Cree un token de acceso personal siguiendo las instrucciones de la [documentación de GitLab](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html?lang=es).<br>• Permisos necesarios:<br>  • `api`<br>  • `read_api`<br>  • `read_repository`<br>  • `write_repository`<br>• En el campo **Token de acceso**, pegue el token que acaba de crear. |
   |  | **Tipo de repositorio: Bitbucket**<br>· En el campo de texto **Nombre de token**, escriba un nombre para el token de acceso que va a crear.<br>• Cree un token de acceso al repositorio mediante la [documentación de Bitbucket](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<br>• Permisos necesarios:<br>• `Read and write access to code and pull requests`. |

   >[!NOTE]
   >
   >La característica **Añadir nuevo token de acceso** se encuentra actualmente en la fase para primeros usuarios. Se están planificando funciones adicionales. Como resultado, los permisos necesarios para los tokens de acceso pueden cambiar. Además, la interfaz de usuario para administrar tokens se puede actualizar, lo que incluye potencialmente características como las fechas de caducidad de los tokens. Y comprobaciones automatizadas para garantizar que los tokens vinculados a repositorios siguen siendo válidos.

1. Haga clic en **Validar**.

Después de la validación, el repositorio externo estará listo para usarse y vincularse a una canalización.

## Vincular un repositorio externo validado a una canalización {#validate-ext-repo}

1. Añada o edite una canalización:
   * [Añadir una canalización de producción](/help/using/production-pipelines.md)
   * [Añadir canalizaciones que no son de producción](/help/using/non-production-pipelines.md)
   * [Editar una canalización](/help/using/managing-pipelines.md#editing-pipelines)

   ![Repositorio de código fuente de la canalización y rama Git](/help/managing-code/assets/pipeline-repo-gitbranch.png)
   *Cuadro de diálogo Añadir canalización que no es de producción con el repositorio seleccionado y la rama Git.*

1. Cuando añada o edite una canalización, para especificar la ubicación del **Código fuente** para su nueva canalización o una existente, elija el repositorio externo que desee utilizar en la lista desplegable **Repositorio**.

1. En la lista desplegable **Rama Git**, seleccione la rama como origen de la canalización.

1. Haga clic en **Guardar**.


>[!TIP]
>
>Para obtener más información sobre la administración de repositorios en Cloud Manager, consulte el documento [Repositorios de Cloud Manager](/help/managing-code/managing-repositories.md).


## Limitaciones

Los repositorios externos no se pueden vincular a las canalizaciones de configuración.

<!-- THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY

* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started. -->

