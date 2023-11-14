---
title: Uso de sus propios repositorios de GitHub en Cloud Manager
description: Obtenga información sobre cómo configurar Cloud Manager para que funcione con sus propios repositorios de GitHub.
feature: Release Information
source-git-commit: 76a3dc6df41032488a3cfe11d0c72769562b96df
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 1%

---


# Uso de sus propios repositorios de GitHub en Cloud Manager {#byo-github}

Al configurar Cloud Manager para que funcione con sus propios repositorios de GitHub, puede validar el código directamente en su repositorio de GitHub a través de Cloud Manager, lo que elimina la necesidad de sincronizar de forma coherente el código con el repositorio de Adobe.

>[!NOTE]
>
>Esta función solo está disponible para [el programa de adopción temprana.](/help/release-notes/current.md#early-adoption)

## Configuración {#configuration}

La configuración consta de dos pasos principales:

1. [Agregar repositorio](#add-repo)
1. [Validación de propiedad del repositorio privado](#validate-ownership)

### Añadir repositorio {#add-repo}

1. En Cloud Manager, desde el **Resumen del programa** página, toque o haga clic en **Repositorios** para cambiar a la pestaña **Repositorios** y haga clic en **Añadir repositorio**.

1. En el **Añadir repositorio** diálogo, seleccione **Repositorio privado** como el tipo de repositorio.

1. Proporcione los detalles del repositorio

   * **Nombre del repositorio** - Un nombre expresivo
   * **URL del repositorio** : la URL del repositorio, que debe finalizar en `.git`
   * **Descripción** (opcional): una descripción más larga del repositorio según sea necesario

   ![Añadir su propio repositorio](/help/assets/repositories/add-own-github.png)

1. Haga clic o pulse **Guardar**.

>[!TIP]
>
>Para obtener más información sobre la administración de repositorios en Cloud Manager, consulte el documento [Repositorios de Cloud Manager.](/help/managing-code/repositories.md)

### Validación de propiedad de repositorio privado {#validate-ownership}

Cloud Manager ahora conoce su repositorio de GitHub, pero aún necesita acceso a él. Para conceder acceso, debe instalar la aplicación de Adobe de GitHub y comprobar que es el propietario del repositorio especificado.

1. Después de agregar su propio repositorio, la variable **Validación de propiedad de repositorio privado** se abrirá.

   ![Validación de propiedad de repositorio privado](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager utiliza una aplicación de GitHub para interactuar de forma segura con el repositorio.
   * Un propietario de su organización de GitHub debe instalar la aplicación ubicada en `https://github.com/apps/cloud-manager-for-aem-stage` y conceder acceso al repositorio.
   * Consulte la documentación de GitHub para obtener más información sobre cómo hacerlo.

1. Para mejorar la seguridad, debe crear un archivo secreto en la rama predeterminada del repositorio. Haga clic o pulse **Generar**.

1. Confirme la generación del archivo secreto tocando o haciendo clic en **Confirmar**.

   ![Confirmar generación de secretos](/help/assets/repositories/confirm-generation.png)

1. De nuevo en **Validación de propiedad de repositorio privado** , Cloud Manager ha generado el contenido del archivo privado en la **Contenido de archivo secreto** field. Copie el contenido de ese campo.

   * El contenido del archivo secreto solo se mostrará una vez. Si no copia el contenido antes de cerrar esta ventana, deberá volver a generar el secreto.

   ![Copiar contenido de archivo secreto](/help/assets/repositories/new-secret.png)

1. Cree un nuevo archivo en la rama predeterminada de su repositorio de GitHub llamado `.well-known/adobe/cloud-manager-challenge` y pegue el contenido del archivo secreto en ese archivo y guarde.

1. Una vez que la aplicación está instalada y el archivo secreto existe en el repositorio, puede tocar o hacer clic en **Validate** en el **Validación de propiedad de repositorio privado** diálogo.

La aplicación se puede instalar y el archivo secreto se puede crear en cualquier orden. Sin embargo, ambos pasos deben completarse antes de poder validar.

Hasta la validación, el repositorio se mostrará con un icono rojo que indica que aún no se ha validado y que aún no se puede utilizar.

![Repositorio no validado](/help/assets/repositories/unvalidated-repo.png)

Tenga en cuenta que la variable **Tipo** identifica fácilmente los repositorios proporcionados por el Adobe (**Adobe**) y sus propios repositorios de GitHub (**GitHub**).

Si necesita volver al repositorio en una fecha posterior para completar la validación, en el **Repositorios** , toque o haga clic en el botón de puntos suspensivos en la fila que representa el repositorio de GitHub que acaba de añadir y seleccione **Validación de propiedad** en el menú desplegable.

## Uso de sus propios repositorios de GitHub con Cloud Manager {#using}

Una vez validado el repositorio de GitHub en Cloud Manager, la integración se completa y puede utilizarlo con Cloud Manager.

1. Al crear una solicitud de extracción, se inicia automáticamente una comprobación de GitHub.

   ![Comprobaciones de GitHub](/help/assets/repositories/github-checks.png)

1. Para cada solicitud de extracción, una [canalización de calidad de código de pila completa](/help/using/managing-pipelines.md) se creará automáticamente. Esta canalización se inicia en cada actualización de solicitud de extracción.

1. La comprobación de GitHub permanece en estado de ejecución hasta que se completen las comprobaciones de calidad del código. Los resultados de calidad del código se propagan a la comprobación de GitHub.

   ![Comprobaciones de calidad del código de GitHub](/help/assets/repositories/github-code-quality.png)

Cuando se cierra o combina la solicitud de extracción, la canalización de calidad del código de pila completa creada se elimina automáticamente.

## Restricciones {#limitations}

Tenga en cuenta las siguientes limitaciones al utilizar sus propios repositorios de GitHub con Cloud Manager.

* No puede usar los repositorios de GitHub como origen de repositorio directo para las canalizaciones que administra.
   * Esta funcionalidad está planificada.
* No se puede pausar la validación de la solicitud de extracción mediante la comprobación de GitHub desde Cloud Manager.
   * Si el repositorio de GitHub se valida en Cloud Manager, Cloud Manager siempre intentará validar las solicitudes de extracción creadas para ese repositorio.
Si la aplicación de Adobe de GitHub se elimina de su organización de GitHub, se eliminará la función de validación de solicitudes de extracción de todos los repositorios.
