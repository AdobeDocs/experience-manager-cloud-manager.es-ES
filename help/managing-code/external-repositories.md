---
title: Adición de repositorios externos en Cloud Manager
description: Obtenga información sobre cómo añadir un repositorio administrado a Adobe en Cloud Manager. Cloud Manager admite la integración con repositorios de GitHub Enterprise, GitLab y Bitbucket.
badge: label="Beta privada" type="Positive" url="/help/release-notes/current.md#gitlab-bitbucket"
exl-id: 4500cacc-5e27-4bbb-b8f6-5144dac7e6da
source-git-commit: a0836dd24dd3b711c9d1b78f28755e2db98b051c
workflow-type: tm+mt
source-wordcount: '2210'
ht-degree: 17%

---

# Añadir repositorios privados en Cloud Manager {#external-repositories}

Obtenga información sobre cómo añadir un repositorio administrado a Adobe en Cloud Manager. Cloud Manager admite la integración con repositorios de GitHub Enterprise, GitLab y Bitbucket.

>[!NOTE]
>
>Las funciones descritas en este artículo solo están disponibles a través del programa beta privado. Para obtener más información y registrarse en la versión beta privada, consulte [Traer su propio Git](/help/release-notes/current.md#gitlab-bitbucket).

## Configurar un repositorio externo

La configuración de un repositorio externo en Cloud Manager consta de tres pasos:

1. [Añada un repositorio externo](#add-external-repo) a un programa seleccionado.
1. [Vincule un repositorio externo validado a una canalización](#validate-ext-repo).
<!-- 1. Provide an access token to the external repository.
1. Validate ownership of the private GitHub repository. -->
1. [Configurar un webhook](#configure-webhook) en un repositorio externo.


## Añadir un repositorio externo {#add-ext-repo}

>[!NOTE]
>
>Los repositorios externos no se pueden vincular a las canalizaciones de configuración.

<!-- THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY>
* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started. -->


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
   | **URL del repositorio** | Obligatorio. La URL del repositorio.<br><br>Si utiliza un repositorio alojado en GitHub, la ruta debe finalizar en `.git`.<br>Por ejemplo, *`https://github.com/org-name/repo-name.git`* (la ruta de URL es solo para ilustración).<br><br>Si va a usar un repositorio externo, éste debe usar el siguiente formato de ruta de URL: <br>`https://git-vendor-name.com/org-name/repo-name.git`<br> o <br>`https://self-hosted-domain/org-name/repo-name.git`<br> Y coincidir con su proveedor Git. |
   | **Seleccionar tipo de repositorio** | Obligatorio. Seleccione el tipo de repositorio que está utilizando:<ul><li>**GitHub** (GitHub Enterprise y la versión autoalojada de GitHub)</li><li>**GitLab** (tanto `gitlab.com` como la versión autoalojada de GitLab) </li><li>**Bitbucket** (solo `bitbucket.org` (versión en la nube) es compatible. La versión autoalojada de Bitbucket quedó obsoleta a partir del 15 de febrero de 2024).</li></ul>Si la ruta de URL del repositorio anterior incluye el nombre del proveedor de Git, como GitLab o Bitbucket, el tipo de repositorio ya estará preseleccionado. |
   | **Descripción** | Opcional. Breve descripción del repositorio. |

1. Seleccione **Guardar** para añadir el repositorio. 

1. En el cuadro de diálogo **Validación de la propiedad del repositorio privado**, proporcione un token de acceso para validar la propiedad del repositorio externo afín de poder acceder a él.

   ![Selección de un token de acceso existente para un repositorio](/help/managing-code/assets/repositories-exisiting-access-token.png)
   *Seleccionar un token de acceso existente para un repositorio de bloque de bits (solo para ilustración).*

>[!BEGINTABS]

>[!TAB GitHub Enterprise]

    | Tipo de token | Descripción |
    | — | — |
    | **Utilice el token de acceso existente** | Si ya ha proporcionado un token de acceso al repositorio para su organización y tiene acceso a varios repositorios, puede seleccionar un token existente. Utilice la lista desplegable **Nombre del token** para elegir el token que desea aplicar al repositorio. De lo contrario, agregue un nuevo token de acceso. |
    | **Agregar nuevo token de acceso** |&lt;ul>&lt;li> En el campo de texto **Nombre del token**, escriba un nombre para el token de acceso que está creando.&lt;li>Cree un token de acceso personal siguiendo las instrucciones de la [documentación de GitHub](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).&lt;li>Permisos necesarios para el token de acceso personal (PAT) de GitHub Enterprise&lt;br>Estos permisos garantizan que Cloud Manager pueda validar solicitudes de extracción, administrar comprobaciones de estado de confirmación y acceder a los detalles de repositorios necesarios.&lt;br>Cuando genere el PAT en GitHub Enterprise, asegúrese de que incluye los siguientes permisos de repositorio:&lt;ul>&lt;li>Solicitud de extracción (lectura y escritura)&lt;li>Estados de confirmación (lectura y escritura)&lt;li>Metadatos de repositorio (solo lectura)&lt;/li>&lt;/li>&lt;/ul>&lt;/li>&lt;/ul>&lt;/ul>&lt;/ul>&lt;ul>&lt;li>En el campo **Token de acceso**, pegue el token que acaba de crear. |
    
    1. Haga clic en **Validar**.
    
    Después de la validación, el repositorio externo está listo para usarse y vincularse a una canalización.
    
    Consulte también [Administrar tokens de acceso](/help/managing-code/manage-access-tokens.md).

>[!TAB GitLab]

    | Tipo de token | Descripción |
    | — | — |
    | **Utilice el token de acceso existente** | Si ya ha proporcionado un token de acceso al repositorio para su organización y tiene acceso a varios repositorios, puede seleccionar un token existente. Utilice la lista desplegable **Nombre del token** para elegir el token que desea aplicar al repositorio. De lo contrario, agregue un nuevo token de acceso. |
    | **Agregar nuevo token de acceso** |&lt;ul>&lt;li>En el campo de texto **Nombre del token**, escriba un nombre para el token de acceso que está creando.&lt;li>Cree un token de acceso personal siguiendo las instrucciones de la [documentación de GitLab](https://docs.gitlab.com/user/profile/personal_access_tokens/).&lt;li>Permisos necesarios para el token de acceso personal (PAT) de GitLab&lt;br>Estos ámbitos permiten a Cloud Manager acceder a los datos del repositorio y a la información de usuario según sea necesario para la validación y la integración de ganchos web.&lt;br>Cuando genere la PAT en GitLab, asegúrese de que incluya los siguientes ámbitos de token:&lt;ul>&lt;li>api&lt;li>read_user&lt;/li>&lt;/li>&lt;/ul>&lt;/li>&lt;/li>&lt;/ul>&lt;/ul>&lt;ul>&lt;li>En el campo **Token de acceso**, pegue el token que acaba de crear. |

1. Haga clic en **Validar**.

   Después de la validación, el repositorio externo estará listo para usarse y vincularse a una canalización.

   Consulte también [Administrar tokens de acceso](/help/managing-code/manage-access-tokens.md).


>[!TAB Bits]

    | Tipo de token | Descripción |
    | — | — |
    | **Utilice el token de acceso existente** | Si ya ha proporcionado un token de acceso al repositorio para su organización y tiene acceso a varios repositorios, puede seleccionar un token existente. Utilice la lista desplegable **Nombre del token** para elegir el token que desea aplicar al repositorio. De lo contrario, agregue un nuevo token de acceso. |
    | **Agregar nuevo token de acceso** |&lt;ul>&lt;li>En el campo de texto **Nombre del token**, escriba un nombre para el token de acceso que está creando.&lt;li>Cree un token de acceso al repositorio con la [documentación de Bitbucket](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).&lt;li>Permisos necesarios para el token de acceso personal (PAT) de Bitbucket&lt;br>Estos permisos permiten a Cloud Manager acceder al contenido del repositorio, administrar solicitudes de extracción y configurar eventos de webhook o reaccionar a ellos.&lt;br>Cuando cree la contraseña de la aplicación en Bitbucket, asegúrese de que incluya los siguientes permisos de contraseña de la aplicación necesarios:&lt;ul>&lt;li>Repositorio (solo lectura)&lt;li>Solicitudes de extracción (lectura y escritura)&lt;li>Webhooks (lectura y escritura)&lt;/li>&lt;/li>&lt;/ul>&lt;/li>&lt;/li>&lt;/ul>&lt;/ul>&lt;ul>&lt;li>En el campo **Token de acceso**, pegue el token que acaba de crear. |
    
    1. Haga clic en **Validar**.
    
    Después de la validación, el repositorio externo está listo para usarse y vincularse a una canalización.
    
    Consulte también [Administrar tokens de acceso](/help/managing-code/manage-access-tokens.md).

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

## Configuración de un webhook para un repositorio externo {#configure-webhook}

Cloud Manager permite configurar los enlaces web para los repositorios Git externos que haya añadido. Consulte [Agregar un repositorio externo](#add-ext-repo). Estos webhooks permiten que Cloud Manager reciba eventos relacionados con diferentes acciones dentro de su solución de proveedor de Git.

Por ejemplo, los enlaces web permiten a Cloud Manager almacenar en déclencheur acciones basadas en eventos como los siguientes:

* Creación de solicitudes de extracción (PR): inicia la funcionalidad de validación PR.
* Eventos push: inicia canalizaciones cuando se activa el déclencheur &quot;En la confirmación de Git&quot; (habilitado).
* Futuras acciones basadas en comentarios: permiten flujos de trabajo, como la implementación directa desde una PR a un entorno de desarrollo rápido (RDE).

La configuración de webhook no es necesaria para los repositorios alojados en `GitHub.com` porque Cloud Manager se integra directamente a través de la aplicación GitHub.

Para todos los demás repositorios externos incorporados con un token de acceso, como GitHub Enterprise, GitLab y Bitbucket, la configuración del webhook está disponible y debe configurarse manualmente.

**Para configurar un webhook para un repositorio externo:**

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización adecuada.

1. En la consola **[Mis programas](/help/getting-started/navigation.md#my-programs-console)**, seleccione el programa en el que desea configurar un webhook para un repositorio Git externo.

1. En la esquina superior izquierda de la página, haga clic en ![Mostrar icono de menú](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para mostrar el menú de la izquierda.

1. En el menú del lado izquierdo, bajo el encabezado **Programa**, haga clic en ![Icono de esquema de carpeta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositorios**.

1. En la página **Repositorios**, usando la columna **Tipo** para guiarle en su selección, busque el repositorio que desee y haga clic en ![Puntos suspensivos - Icono de más](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) junto a él.

   ![Opción Configurar webhook en el menú desplegable para un repositorio seleccionado](/help/managing-code/assets/repository-config-webhook.png)

1. En el menú desplegable, haga clic en **Configurar webhook**.

   ![Cuadro de diálogo Configurar webhook](/help/managing-code/assets/config-webhook.png)

1. En el cuadro de diálogo **Configurar webhook**, haga lo siguiente:

   1. Junto al campo **URL de webhook**, haga clic en ![Icono de copia](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).
Pegue la dirección URL en un archivo de texto sin formato. La URL copiada es necesaria para la configuración del webhook del proveedor Git.
   1. Junto al campo de clave/token **Secreto de webhook**, haz clic en **Generar** y luego haz clic en ![Icono de copiar](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).
Pegue el secreto en un archivo de texto sin formato. El secreto copiado es necesario para la configuración del webhook del proveedor Git.
1. Haga clic en **Cerrar**.
1. Vaya a la solución de su proveedor de Git (GitHub Enterprise, GitLab o Bitbucket).

   Todos los detalles de la configuración del gancho web y los eventos necesarios para cada proveedor están disponibles en [Agregar un repositorio externo](#add-ext-repo). En el paso 8, consulte la tabla.

>[!BEGINTABS]

>[!TAB GitHub Enterprise]

1. Busque la sección Configuración de **Webhook** de la solución.
1. Pegue la dirección URL del webhook copiada anteriormente en el campo de texto URL.
   1. Reemplace el parámetro de consulta `api_key` en la dirección URL del webhook por su propia clave de API real.

      Para generar una clave de API, debe crear un proyecto de integración en Adobe Developer Console. Consulte [Creación de un proyecto de integración de API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) para obtener información detallada.

1. Pegue el secreto de webhook que copió anteriormente en el campo de texto **Secreto** (o **Clave secreta**, o **Token secreto**).
1. Configure el webhook para enviar los eventos requeridos que espera Cloud Manager.

   | Eventos de gancho web requeridos |
   | --- |
   | Estos eventos permiten que Cloud Manager responda a la actividad de GitHub, como la validación de solicitudes de extracción, los déclencheur basados en push para canalizaciones o la sincronización de código de Edge Delivery Services.<br>Asegúrese de que el gancho web esté configurado para el déclencheur en los siguientes eventos de gancho web necesarios:<ul><li>Solicitudes de extracción<li>Inserciones<li>Comentarios sobre problemas</li></li></li></ul></ul></ul> |

>[!TAB GitLab]

1. Busque la sección Configuración de **Webhook** de la solución.
1. Pegue la dirección URL del webhook copiada anteriormente en el campo de texto URL.
   1. Reemplace el parámetro de consulta `api_key` en la dirección URL del webhook por su propia clave de API real.

      Para generar una clave de API, debe crear un proyecto de integración en Adobe Developer Console. Consulte [Creación de un proyecto de integración de API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) para obtener información detallada.

1. Pegue el secreto de webhook que copió anteriormente en el campo de texto **Secreto** (o **Clave secreta**, o **Token secreto**).
1. Configure el webhook para enviar los eventos requeridos que espera Cloud Manager.

   | Eventos de gancho web requeridos |
   | --- |
   | Estos eventos de gancho web permiten a Cloud Manager almacenar en déclencheur las canalizaciones cuando se inserta código o se envía una solicitud de combinación. También rastrean los comentarios relacionados con la validación de solicitudes de extracción (a través de eventos de nota).<br>Asegúrese de que el gancho web esté configurado para el déclencheur en los siguientes eventos de gancho web requeridos<ul><li>Eventos push<li>Combinar eventos de solicitud<li>Eventos de nota</li></li></li></ul></ul></ul> |

>[!TAB Bits]

1. Busque la sección Configuración de **Webhook** de la solución.
1. Pegue la dirección URL del webhook copiada anteriormente en el campo de texto URL.
   1. Reemplace el parámetro de consulta `api_key` en la dirección URL del webhook por su propia clave de API real.

      Para generar una clave de API, debe crear un proyecto de integración en Adobe Developer Console. Consulte [Creación de un proyecto de integración de API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/) para obtener información detallada.

1. Pegue el secreto de webhook que copió anteriormente en el campo de texto **Secreto** (o **Clave secreta**, o **Token secreto**).
1. Configure el webhook para enviar los eventos requeridos que espera Cloud Manager.

   | Eventos de gancho web requeridos |
   | --- |
   | Estos eventos garantizan que Cloud Manager pueda validar las solicitudes de extracción, responder a inserciones de código e interactuar con comentarios para la coordinación de canalizaciones.<br>Asegúrese de que el gancho web esté configurado para el déclencheur en los siguientes eventos de gancho web requeridos<ul><li>Solicitud de extracción: creada<li>Solicitud de extracción: actualizada<li>Solicitudes de extracción: combinadas<li>Solicitud de extracción: comentario<li>Repositorio: push</li></li></li></ul></ul></ul> |

>[!ENDTABS]

### Validación de solicitudes de extracción con webhooks

Una vez configurados correctamente los enlaces web, Cloud Manager déclencheur automáticamente las ejecuciones de canalización o las comprobaciones de validación de PR de su repositorio.

Se aplican los siguientes comportamientos:

>[!BEGINTABS]

>[!TAB GitHub Enterprise]

Cuando se crea la comprobación, aparece como la siguiente captura de pantalla a continuación. La diferencia clave de `GitHub.com` es que `GitHub.com` usa una ejecución de comprobación, mientras que GitHub Enterprise (que usa tokens de acceso personal) genera un estado de confirmación:

![Confirmar estado para indicar el proceso de validación de PR en GitHub Enterprise](/help/managing-code/assets/repository-webhook-github-pr-validation.png)

>[!TAB GitLab]

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

Cuando se ejecuta la validación de calidad del código:

![Estado mientras se ejecuta la validación de calidad del código](/help/managing-code/assets/repository-webhook-bitbucket1.png)

Utiliza el estado de confirmación para rastrear el progreso de validación de PR. En el siguiente caso, la captura de pantalla muestra qué sucede cuando una validación de calidad de código falla debido a un problema con el cliente. Se agrega un comentario con información detallada del error y se crea una comprobación de compromiso, que muestra el error (visible a la derecha):

![Estado de validación de solicitud de extracción para Bitbucket](/help/managing-code/assets/repository-webhook-bitbucket2.png)

>[!ENDTABS]

## Solucionar problemas de webhook

* Asegúrese de que la dirección URL del webhook incluya una clave de API válida.
* Compruebe que los eventos de gancho web estén correctamente configurados en la configuración del proveedor de Git.
* Si los déclencheur de validación de PR o canalización no funcionan, compruebe que el secreto de webhook esté actualizado tanto en Cloud Manager como en el proveedor de Git.