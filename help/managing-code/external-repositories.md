---
title: Adición de repositorios externos en Cloud Manager
description: Obtenga información sobre cómo añadir un repositorio administrado a Adobe en Cloud Manager. Cloud Manager admite la integración con repositorios de GitHub Enterprise, GitLab, Bitbucket y Azure DevOps.
exl-id: 4500cacc-5e27-4bbb-b8f6-5144dac7e6da
source-git-commit: ee49b0732fdb870c4f768764aa75b240fd101b59
workflow-type: tm+mt
source-wordcount: '2560'
ht-degree: 28%

---

# Añadir repositorios privados en Cloud Manager {#external-repositories}

<!-- badge: label="Beta - Azure DevOps only" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket" -->

Obtenga información sobre cómo añadir un repositorio administrado a Adobe en Cloud Manager. Cloud Manager admite la integración con repositorios de GitHub Enterprise, GitLab y Bitbucket.

Los clientes ahora también pueden incorporar sus repositorios Git de DevOps de Azure en Cloud Manager, con compatibilidad tanto con los repositorios modernos de DevOps de Azure como con los repositorios VSTS heredados (Visual Studio Team Services).

* Para los usuarios de Edge Delivery Services, el repositorio incorporado se puede utilizar para sincronizar e implementar el código del sitio.
* Para los usuarios de AEM as a Cloud Service y Adobe Managed Services (AMS), el repositorio se puede vincular a canalizaciones de pila completa y de front-end.



## Configurar un repositorio externo

La configuración de un repositorio externo en Cloud Manager consta de tres pasos:

1. [Añada un repositorio externo](#add-external-repo) a un programa seleccionado.
1. [Vincule un repositorio externo validado a una canalización](#validate-ext-repo).
<!--
1. Provide an access token to the external repository.
1. Validate ownership of the private GitHub repository.
-->
1. [Configurar un webhook](#configure-webhook) en un repositorio externo.


## Añadir un repositorio externo {#add-ext-repo}

>[!NOTE]
>
>Los repositorios externos no se pueden vincular a las canalizaciones de configuración.

<!--
THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY>
* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started.
-->


1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización adecuada.

1. En la consola **[Mis programas](/help/getting-started/navigation.md#my-programs-console)**, seleccione el programa al que desea vincular un repositorio externo.

1. En el menú lateral, en **Programa**, haga clic en ![Icono de esquema de carpeta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositorios**.

   ![La página Repositorios](/help/managing-code/assets/repositories-tab.png)

1. Cerca de la esquina superior derecha de la página **Repositorios**, haga clic en **Añadir repositorio**.

1. En el cuadro de diálogo **Añadir repositorio**, seleccione **Repositorio privado** para vincular un repositorio de Git externo a su programa.

   ![Añadir su propio repositorio](/help/managing-code/assets/repository-add-private-dialogbox2.png)

1. En cada campo respectivo, proporcione los siguientes detalles sobre el repositorio:

   | Campo | Descripción |
   | --- | --- |
   | **Nombre del repositorio** | Obligatorio. Un nombre expresivo para el nuevo repositorio. |
   | **URL del repositorio** | Obligatorio. La dirección URL del repositorio.<br><br>Si usa un repositorio alojado en GitHub, la ruta debe finalizar en `.git`.<br>Por ejemplo, *`https://github.com/org-name/repo-name.git`* (la ruta de URL es solo para ilustración).<br><br>Si usa un repositorio externo, debe usar el siguiente formato de ruta de URL:<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> o<br>`https://self-hosted-domain/org-name/repo-name.git`<br>Y coincidir con el proveedor de Git. |
   | **Seleccionar tipo de repositorio** | Obligatorio. Seleccione el tipo de repositorio que está utilizando:<ul><li>**GitHub** (GitHub Enterprise y la versión autoalojada de GitHub)</li><li>**GitLab** (tanto `gitlab.com` como la versión autoalojada de GitLab) </li><li>**Bitbucket** (solo `bitbucket.org` (versión en la nube) es compatible. La versión autoalojada de Bitbucket quedó obsoleta a partir del 15 de febrero de 2024).</li><li>**DevOps de Azure** (`dev.azure.com`)</ul>Si la ruta de URL del repositorio anterior incluye el nombre del proveedor de Git, como GitLab o Bitbucket, el tipo de repositorio ya estará preseleccionado.</li> </ul> |
   | **Descripción** | Opcional. Breve descripción del repositorio. |

1. Seleccione **Guardar** para añadir el repositorio.

   Ahora, proporcione un token de acceso para validar la propiedad del repositorio externo.

1. En el cuadro de diálogo **Validación de propiedad de repositorio privado**, proporcione un token de acceso para validar la propiedad del repositorio externo y así poder acceder a él y, a continuación, haga clic en **Validar**.

   ![Selección de un token de acceso existente para un repositorio](/help/managing-code/assets/repositories-exisiting-access-token.png)
   *Seleccionar un token de acceso existente para un repositorio de bloque de bits (solo para ilustración).*

>[!BEGINTABS]

>[!TAB GitHub Enterprise]

<!--
https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/github 
-->

| Opción de token de acceso | Descripción |
| --- | --- |
| **Usar token de acceso existente** | Si ya ha proporcionado un token de acceso al repositorio para su organización y tiene acceso a varios repositorios, puede seleccionar un token existente. Utilice la lista desplegable **Nombre de token** para elegir el token que desea aplicar al repositorio. De lo contrario, añada un nuevo token de acceso. |
| **Añadir nuevo token de acceso** | <ul><li> En el campo de texto **Nombre de token**, escriba un nombre para el token de acceso que está creando.<li>Cree un token de acceso personal siguiendo las instrucciones de la [documentación de GitHub](https://docs.github.com/es/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).<li>Permisos necesarios para el token de acceso personal (PAT) de GitHub Enterprise<br>Estos permisos garantizan que Cloud Manager pueda validar las solicitudes de extracción, administrar las comprobaciones de estado de las confirmaciones y acceder a los detalles necesarios del repositorio.<br>Cuando genere el PAT en GitHub Enterprise, asegúrese de que incluya los siguientes permisos de repositorio:<ul><li>Solicitud de extracción (lectura y escritura)<li>Confirmar estados (lectura y escritura)<li>Metadatos del repositorio (solo lectura)</li></li></ul></li></ul></ul></ul><ul><li>En el campo **Token de acceso**, pegue el token que acaba de crear. |

Después de la validación, el repositorio externo estará listo para usarse y vincularse a una canalización.

Consulte también [Administrar tokens de acceso](/help/managing-code/manage-access-tokens.md).

>[!TAB GitLab]

<!--
https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/gitlab 
-->

| Opción de token de acceso | Descripción |
| --- | --- |
| **Usar token de acceso existente** | Si ya ha proporcionado un token de acceso al repositorio para su organización y tiene acceso a varios repositorios, puede seleccionar un token existente. Utilice la lista desplegable **Nombre de token** para elegir el token que desea aplicar al repositorio. De lo contrario, añada un nuevo token de acceso. |
| **Añadir nuevo token de acceso** | <ul><li>En el campo de texto **Nombre de token**, escriba un nombre para el token de acceso que está creando.<li>Cree un token de acceso personal siguiendo las instrucciones de la [documentación de GitLab](https://docs.gitlab.com/user/profile/personal_access_tokens/).<li>Permisos necesarios para el token de acceso personal (PAT) de GitLab<br>Estos ámbitos permiten a Cloud Manager acceder a los datos del repositorio y a la información de usuario según sea necesario para la validación y la integración de ganchos web.<br>Cuando genere el PAT en GitLab, asegúrese de que incluya los siguientes ámbitos de token:<ul><li>api<li>read_user</li></li></ul></li></li></ul></ul></ul><ul><li>En el campo **Token de acceso**, pegue el token que acaba de crear. |

Después de la validación, el repositorio externo estará listo para usarse y vincularse a una canalización.

Consulte también [Administrar tokens de acceso](/help/managing-code/manage-access-tokens.md).


>[!TAB Bits]

<!--
https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/bitbucket 
-->

| Opción de token de acceso | Descripción |
| --- | --- |
| **Usar token de acceso existente** | Si ya ha proporcionado un token de acceso al repositorio para su organización y tiene acceso a varios repositorios, puede seleccionar un token existente. Utilice la lista desplegable **Nombre de token** para elegir el token que desea aplicar al repositorio. De lo contrario, añada un nuevo token de acceso. |
| **Añadir nuevo token de acceso** | <ul><li>En el campo de texto **Nombre de token**, escriba un nombre para el token de acceso que está creando.<li>Cree un token de acceso al repositorio mediante la [documentación de Bitbucket](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<li>Permisos necesarios para el token de acceso personal (PAT) de Bitbucket<br>Estos permisos permiten a Cloud Manager acceder al contenido del repositorio, administrar solicitudes de extracción y configurar eventos de webhook o reaccionar a ellos.<br>Cuando cree la contraseña de la aplicación en Bitbucket, asegúrese de que incluya los siguientes permisos de contraseña de aplicación necesarios:<ul><li>Repositorio (solo lectura)<li>Solicitudes de extracción (lectura y escritura)<li>Webhooks (leer y escribir)</li></li></ul></li></li></ul></ul></ul><ul><li>En el campo **Token de acceso**, pegue el token que acaba de crear. |

Después de la validación, el repositorio externo estará listo para usarse y vincularse a una canalización.

See also [Manage Access Tokens](/help/managing-code/manage-access-tokens.md).

>[!TAB Azure DevOps]

<!--
https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/azure_devops
-->

| Access token option | Descripción |
| --- | --- |
| **Usar token de acceso existente** | Si ya ha proporcionado un token de acceso al repositorio para su organización y tiene acceso a varios repositorios, puede seleccionar un token existente. Utilice la lista desplegable **Nombre de token** para elegir el token que desea aplicar al repositorio. De lo contrario, añada un nuevo token de acceso. |
| **Añadir nuevo token de acceso** | <ul><li>In the **Token Name** text field, type a name for the access token you are creating.<li>Create a repository access token using the [Azure DevOps documentation](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=Windows).<li>Required permissions for the Azure DevOps Personal Access Token (PAT).<br>These permissions allow Cloud Manager to access repository content, manage pull requests, and configure or react to webhook events.<br>When you create the app password in Azure DevOps, make sure it includes the following required app password permissions:<ul><li>Code (Read)</li><li>Code (Status)</li><li>Pull Request Threads (Read &amp; write)</li></ul></li></li></ul></ul></ul><ul><li>In the **Access Token** field, paste the token you just created. |

Después de la validación, el repositorio externo estará listo para usarse y vincularse a una canalización.

See also [Manage Access Tokens](/help/managing-code/manage-access-tokens.md).

>[!ENDTABS]


## Vincular un repositorio externo validado a una canalización {#validate-ext-repo}

1. Añada o edite una canalización:
   * [Añadir una canalización de producción](/help/using/production-pipelines.md#adding-production-pipeline)
   * [Añadir canalizaciones que no son de producción](/help/using/non-production-pipelines.md#add-non-production-pipeline)
   * [Editar una canalización](/help/using/managing-pipelines.md#editing-pipelines)

   ![Repositorio de código fuente de la canalización y rama Git](/help/managing-code/assets/pipeline-repo-gitbranch.png)
   *Cuadro de diálogo Añadir canalización que no es de producción con el repositorio seleccionado y la rama Git.*

1. Cuando añada o edite una canalización, para especificar la ubicación del **Código fuente** para su nueva canalización o una existente, elija el repositorio externo que desee utilizar en la lista desplegable **Repositorio**.

1. En la lista desplegable **Rama Git**, seleccione la rama como origen de la canalización.

1. Haga clic en **Guardar**.


>[!TIP]
>
>Para obtener más información sobre la administración de repositorios en Cloud Manager, consulte el documento [Repositorios de Cloud Manager](/help/managing-code/managing-repositories.md).


## Configure a webhook for an external repository {#configure-webhook}

Cloud Manager lets you configure webhooks for external Git repositories that you have added. See [Add an external repository](#add-ext-repo). These webhooks permit Cloud Manager to receive events that are related to different actions within your Git vendor solution.

For example, webhooks allow Cloud Manager to trigger actions based on events such as the following:

* Pull request (PR) creation – Initiates PR validation functionality.
* Push events – Starts pipelines when the &quot;On Git Commit&quot; trigger is turned on (enabled).
* Future comment-based actions – Allows workflows, such as direct deployment from a PR, to a Rapid Development Environment (RDE).

Webhook configuration is not required for repositories hosted on `GitHub.com` because Cloud Manager integrates directly through the GitHub app.

For all other external repositories that are onboarded with an access token – such as GitHub Enterprise, GitLab, Bitbucket, and Azure DevOps – webhook configuration is available and must be set up manually.

**To configure a webhook for an external repository:**

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización adecuada.

1. On the **[My Programs](/help/getting-started/navigation.md#my-programs-console)** console, select the program to which you want to configure a webhook for an external Git repository.

1. En la esquina superior izquierda de la página, haga clic en ![Mostrar icono de menú](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para mostrar el menú de la izquierda.

1. In the left side menu, Under the **Program** heading, click ![Folder outline icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositories**.

1. On the **Repositories** page, using the **Type** column to guide you in your selection, locate the repository you want, then click ![Ellipsis - More icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) next to it.

   ![Config Webhook option on drop-down menu for a selected repository](/help/managing-code/assets/repository-config-webhook.png)

1. From the drop-down menu, click **Config Webhook**.

   ![Configure Webhook dialog box](/help/managing-code/assets/config-webhook.png)

1. In the **Config Webhook** dialog box, do the following:

   1. Next to the **Webhook URL** field, click ![Copy icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).
Paste the URL in a plain text file. The copied URL is required for your Git vendor&#39;s Webhook settings.
   1. Next to the **Webhook Secret** token/key field, click **Generate**, then click ![Copy icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).
Paste the secret in a plain text file. The copied secret is required for your Git vendor&#39;s Webhook settings.
1. Haga clic en **Cerrar**.
1. Navigate to your Git vendor solution (GitHub Enterprise, GitLab, Bitbucket, or Azure DevOps).

   All the details on the webhook configuration and the events that are required for each vendor are available in [Add an external repository](#add-ext-repo). Under step 8, see the tabbed table.

1. Locate the solution&#39;s **Webhook** Settings section.
1. Paste the Webhook URL that you copied earlier into the URL text field.
   1. Replace the `api_key` query parameter in the Webhook URL with your own real API key.

      To generate an API key, you must create an integration project in Adobe Developer Console. See [Creating an API Integration Project](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) for full details.

1. Paste the Webhook Secret that you copied earlier into the **Secret** (or **Secret key**, or **Secret token**) text field.
1. Configure the webhook to send the events that Cloud Manager requires. Use the following table to determine the correct events for your Git provider.

>[!BEGINTABS]

>[!TAB GitHub Enterprise]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/github -->

| Required webhook events |
| --- |
| These events allow Cloud Manager to respond to GitHub activity, such as pull request validation, push-based triggers for pipelines, or Edge Delivery Services code sync.<br>Make sure that the webhook is set up to trigger on the following required webhook events:<ul><li>Solicitudes de extracción<li>Pushes<li>Comentarios sobre problemas</li></li></li></ul></ul></ul> |

>[!TAB GitLab]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/gitlab -->

| Eventos de gancho web requeridos |
| --- |
| Estos eventos de gancho web permiten a Cloud Manager almacenar en déclencheur las canalizaciones cuando se inserta código o se envía una solicitud de combinación. También hacen un seguimiento de los comentarios relacionados con la validación de solicitudes de extracción (mediante eventos de notas).<br>Asegúrese de que el webhook esté configurado para el déclencheur en los siguientes eventos de webhook necesarios<ul><li>Eventos push<li>Combinar eventos de solicitud<li>Eventos de nota</li></li></li></ul></ul></ul> |

>[!TAB Bits]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/bitbucket -->

| Eventos de gancho web requeridos |
| --- |
| Estos eventos garantizan que Cloud Manager pueda validar las solicitudes de extracción, responder a inserciones de código e interactuar con comentarios para la coordinación de la canalización.<br>Asegúrese de que el webhook esté configurado para el déclencheur en los siguientes eventos de webhook necesarios<ul><li>Solicitud de extracción: creada<li>Solicitud de extracción: actualizada<li>Solicitudes de extracción: combinadas<li>Solicitud de extracción: comentario<li>Repositorio: push</li></li></li></ul></ul></ul> |

>[!TAB DevOps de Azure]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/azure_devops -->

| Eventos y autenticación de gancho web requeridos |
| --- |
| Estos eventos garantizan que Cloud Manager pueda validar las solicitudes de extracción, responder a inserciones de código e interactuar con comentarios para la coordinación de la canalización.<br>Asegúrese de que el webhook esté configurado para el déclencheur en los siguientes eventos de webhook necesarios<ul><li>Código insertado</li><li>La solicitud de extracción agregó un comentario sobre</li><li>Solicitud de extracción creada</li><li>Solicitud de extracción actualizada</li></ul>Establecer autenticación:<br>1. En el campo **Nombre de usuario de autenticación básica**, escriba `cloudmanager`.<br>2. En el campo **Contraseña de autenticación básica**, escriba el Secreto de webhook generado desde la interfaz de usuario de Cloud Manager. |

>[!ENDTABS]


### Validación de solicitudes de extracción con webhooks

Una vez configurados correctamente los enlaces web, Cloud Manager déclencheur automáticamente las ejecuciones de canalización o las comprobaciones de validación de solicitudes de extracción (PR) de su repositorio.

El comportamiento varía según el proveedor de Git que utilice, como se describe a continuación.


>[!BEGINTABS]

>[!TAB GitHub Enterprise]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/github -->

Cuando se crea la comprobación, aparece como la siguiente captura de pantalla a continuación. La diferencia clave de `GitHub.com` es que `GitHub.com` usa una ejecución de comprobación, mientras que GitHub Enterprise (que usa tokens de acceso personal) genera un estado de confirmación:

![Confirmar estado para indicar el proceso de validación de PR en GitHub Enterprise](/help/managing-code/assets/repository-webhook-github-pr-validation.png)

>[!TAB GitLab]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/gitlab -->

Las interacciones de GitLab se basan únicamente en comentarios. Cuando comienza la validación, se agrega un comentario. Cuando finaliza la validación (ya sea correcta o errónea), el comentario inicial se elimina y se reemplaza por un nuevo comentario que contiene los resultados de validación o los detalles del error.

Cuando se ejecuta la validación de calidad del código:

![Cuando se está ejecutando la validación de calidad del código](/help/managing-code/assets/repository-webhook-gitlab1.png)

Cuando finalice la validación de calidad en frío:

![Cuando finalice la validación de la calidad en frío](/help/managing-code/assets/repository-webhook-gitlab2.png)

Cuando la validación de calidad del código falla con un error:

![Cuando la validación de la calidad del código falla con un error](/help/managing-code/assets/repository-webhook-gitlab3.png)

Cuando falla la validación de calidad del código debido a problemas con los clientes:

![Cuando falla la validación de calidad del código debido a problemas con el cliente](/help/managing-code/assets/repository-webhook-gitlab4.png)

>[!TAB Bits]

<!-- https://git.corp.adobe.com/pages/experience-platform/cloud-manager-repository-service/#/./git-vendors/bitbucket -->

Cuando se ejecuta la validación de calidad del código:

![Estado mientras se ejecuta la validación de calidad del código](/help/managing-code/assets/repository-webhook-bitbucket1.png)

Utiliza el estado de confirmación para rastrear el progreso de validación de PR. En el siguiente caso, la captura de pantalla muestra qué sucede cuando una validación de calidad de código falla debido a un problema con el cliente. Se agrega un comentario con información detallada del error y se crea una comprobación de compromiso, que muestra el error (visible a la derecha):

![Estado de validación de solicitud de extracción para Bitbucket](/help/managing-code/assets/repository-webhook-bitbucket2.png)

>[!TAB DevOps de Azure]

Azure DevOps realiza un seguimiento de la validación de solicitudes de extracción mediante comprobaciones de estado. Cuando Cloud Manager ejecuta la validación de solicitudes de extracción, agrega comprobaciones de estado que aparecen en la interfaz de solicitudes de extracción de Azure DevOps.

Durante la validación de la calidad del código, una comprobación de estado muestra que el proceso está en curso:

![Validación de DevOps de Azure de solicitudes de extracción con webhooks-1](/help/managing-code/assets/azure-devops-validation-of-pull-requests-with-webhooks-1.png)

Cuando se complete la validación de calidad del código, la comprobación de estado se actualiza para reflejar los resultados:

![Validación de DevOps de Azure de solicitudes de extracción con webhooks-2](/help/managing-code/assets/azure-devops-validation-of-pull-requests-with-webhooks-2.png)

Si la validación falla, se proporciona información detallada sobre el error en los detalles de la comprobación de estado. Puede hacer clic en la comprobación de estado para ver los resultados de validación completos en Cloud Manager.

![Validación de DevOps de Azure de solicitudes de extracción con webhooks-3](/help/managing-code/assets/azure-devops-validation-of-pull-requests-with-webhooks-3.png)

Para comentarios y sugerencias sobre solicitudes de extracción, Cloud Manager agrega comentarios directamente a la solicitud de extracción en las oficinas de desarrollo de Azure con detalles de validación y las acciones necesarias.

![Validación de DevOps de Azure de solicitudes de extracción con webhooks-4](/help/managing-code/assets/azure-devops-validation-of-pull-requests-with-webhooks-4.png)


>[!ENDTABS]

## Solucionar problemas de webhook

* Asegúrese de que la dirección URL del webhook incluya una clave de API válida.
* Compruebe que los eventos de gancho web estén correctamente configurados en la configuración del proveedor de Git.
* Si los déclencheur de validación de PR o canalización no funcionan, compruebe que el secreto de webhook esté actualizado tanto en Cloud Manager como en el proveedor de Git.