---
title: Adición de repositorios privados en Cloud Manager
description: Obtenga información sobre cómo configurar Cloud Manager para que funcione con sus propios repositorios privados de GitHub.
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: dcb48f6914ff48c6905da40609ca99fe529d9fe3
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 80%

---


# Adición de repositorios privados en Cloud Manager {#private-repositories}

Obtenga información sobre cómo configurar Cloud Manager para que funcione con sus propios repositorios privados de GitHub.

## Información general {#overview}

Al configurar Cloud Manager para que funcione con sus propios repositorios privados de GitHub, puede validar su código directamente en el repositorio de GitHub a través de Cloud Manager, lo que elimina la necesidad de sincronizar su código de forma coherente con el repositorio de Adobe.

>[!NOTE]
>
>Esta funcionalidad es exclusiva de GitHub público. La compatibilidad con GitHub autoalojado no está disponible.

## Configuración {#configuration}

La configuración consta de dos pasos principales:

1. [Añadir repositorio](#add-repo)
1. [Validación de propiedad del repositorio privado](#validate-ownership)

### Añadir repositorio {#add-repo}

1. En Cloud Manager, en la página **Resumen del programa**, pulse o haga clic en la pestaña **Repositorios** para cambiar a la pestaña **Repositorios** y haga clic en **Añadir repositorio**.

1. En el diálogo **Añadir repositorio**, seleccione **Repositorio privado** como el tipo de repositorio.

1. Proporcione los detalles del repositorio

   * **Nombre del repositorio**: un nombre expresivo
   * **URL del repositorio**: la URL de este, que debe finalizar en `.git`
   * **Descripción** (opcional): una descripción más larga del repositorio según sea necesario

   ![Añadir su propio repositorio](/help/assets/repositories/add-own-github.png)

1. Haga clic o pulse **Guardar**.

>[!TIP]
>
>Para obtener más información sobre la administración de repositorios en Cloud Manager, consulte el documento [Repositorios de Cloud Manager.](/help/managing-code/managing-repositories.md)

### Validación de propiedad de repositorio privado {#validate-ownership}

Cloud Manager ahora conoce su repositorio de GitHub, pero aún necesita acceso. Para otorgar acceso, debe instalar la aplicación de GitHub de Adobe y comprobar que es el propietario del repositorio especificado.

1. Después de añadir su propio repositorio, se abre el cuadro de diálogo **Validación de propiedad de repositorio privado**.

   ![Validación de propiedad de repositorio privado](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager utiliza una aplicación de GitHub para interactuar de forma segura con el repositorio.
   * Un propietario de su organización de GitHub debe instalar la aplicación ubicada en `https://github.com/apps/cloud-manager-for-aem` y otorgar acceso al repositorio.
   * Consulte la documentación de GitHub para obtener más información sobre cómo hacerlo.

1. Para mejorar la seguridad, debe crear un archivo secreto en la rama predeterminada del repositorio. Pulse o haga clic en **Generar**.

1. Confirme la generación del archivo secreto pulsando o haciendo clic en **Confirmar**.

   ![Confirmar generación de secreto](/help/assets/repositories/confirm-generation.png)

1. De nuevo en la ventana **Validación de propiedad de repositorio privado**, Cloud Manager ha generado el contenido del archivo privado en el campo **Contenido de archivo secreto**. Copie el contenido de dicho campo.

   * El contenido del archivo secreto solo se mostrará una vez. Si no copia el contenido antes de cerrar esta ventana, deberá volver a generar el secreto.

   ![Copiar contenido de archivo secreto](/help/assets/repositories/new-secret.png)

1. Cree un nuevo archivo en la rama predeterminada de su repositorio de GitHub denominado `.well-known/adobe/cloud-manager-challenge` y pegue el contenido del archivo secreto en ese archivo y guárdelo.

1. Una vez que la aplicación está instalada y el archivo secreto existe en el repositorio, puede pulsar o hacer clic en **Validar** en el diálogo **Validación de propiedad de repositorio privado**.

La aplicación se puede instalar y el archivo secreto se puede crear en cualquier orden. Sin embargo, ambos pasos deben completarse antes de poder validar.

Hasta la validación, el repositorio se mostrará con un icono rojo que indica que aún no se ha validado y que todavía no se puede utilizar.

![Repositorio no validado](/help/assets/repositories/unvalidated-repo.png)

Tenga en cuenta que la columna **Tipo** identifica fácilmente los repositorios proporcionados por Adobe (**Adobe**) y sus propios repositorios de GitHub (**GitHub**).

Si necesita volver al repositorio en una fecha posterior para completar la validación, en la página **Repositorios** pulse o haga clic en el botón de puntos suspensivos en la fila que representa el repositorio de GitHub que acaba de añadir y seleccione **Validación de propiedad** en el menú desplegable.

## Uso de repositorios privados con Cloud Manager {#using}

Una vez validado el repositorio de GitHub en Cloud Manager, la integración se completa y puede utilizarlo con Cloud Manager.

1. Al crear una solicitud de extracción, se inicia automáticamente una comprobación de GitHub.

   ![Comprobaciones de GitHub](/help/assets/repositories/github-checks.png)

1. Para cada solicitud de extracción, se crea automáticamente una [canalización de calidad de código de pila completa](/help/using/managing-pipelines.md). Esta canalización se inicia en cada actualización de solicitud de extracción.

1. La comprobación de GitHub permanece en estado de ejecución hasta que se completen las comprobaciones de calidad del código. Los resultados de calidad del código se propagan a la comprobación de GitHub.

   ![Comprobaciones de calidad del código de GitHub](/help/assets/repositories/github-code-quality.png)

Cuando se cierra o se combina la solicitud de extracción, la canalización de calidad del código de pila completa creada se elimina automáticamente.

>[!TIP]
>
>Ver el documento [Anotaciones de comprobación de GitHub](github-annotations.md) para obtener más información sobre la información proporcionada a través de GitHub cuando se ejecutan las comprobaciones de solicitudes de extracción.

>[!TIP]
>
>Puede controlar las canalizaciones que se crean automáticamente para validar cada solicitud de extracción en un repositorio privado. Consulte el documento [Configuración de comprobación de GitHub para repositorios privados](github-check-config.md) para obtener más información.

## Asociación de repositorios privados con canalizaciones {#pipelines}

Los repositorios privados validados se pueden asociar con [canalizaciones full-stack y frontend.](/help/overview/ci-cd-pipelines.md)

>[!NOTE]
>
>Las canalizaciones de nivel web y configuración no son compatibles con los repositorios privados.

## Restricciones {#limitations}

Tenga en cuenta las siguientes limitaciones al utilizar sus propios repositorios de GitHub con Cloud Manager.

* No puede utilizar los repositorios de GitHub como origen de repositorio directo para las canalizaciones que administra.
   * Esta funcionalidad está planificada.
* No se puede pausar la validación de la solicitud de extracción mediante la comprobación de GitHub desde Cloud Manager.
   * Si el repositorio de GitHub se valida en Cloud Manager, Cloud Manager siempre intentará validar las solicitudes de extracción creadas para ese repositorio.
Si la aplicación de GitHub de Adobe se quita de su organización de GitHub, se eliminará la función de validación de solicitudes de extracción de todos los repositorios.
