---
title: Administración de repositorios en Cloud Manager
description: Obtenga información sobre cómo crear, ver y editar repositorios de Git en Cloud Manager.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 79%

---


# Repositorios de Cloud Manager {#cloud-manager-repos}

Obtenga información sobre cómo crear, ver y editar repositorios de Git en Cloud Manager.

## Información general {#overview}

Los repositorios se utilizan para almacenar y administrar el código del proyecto mediante Git. Cada programa que cree en Cloud Manager tiene un repositorio administrado por Adobe creado para él.

Puede elegir crear repositorios adicionales administrados por Adobe y también añadir sus propios repositorios privados. Todos los repositorios asociados con su programa se pueden ver en la ventana **Repositorios**.

Los repositorios creados en Cloud Manager también estarán disponibles para su selección al añadir o editar canalizaciones. Consulte [Canalizaciones de CI-CD](/help/overview/ci-cd-pipelines.md) para obtener más información.

Hay un único repositorio principal o una rama para una canalización determinada. Con [compatibilidad con el submódulo git](git-submodules.md), se pueden incluir muchas ramas secundarias en el momento de la compilación.

## Ventana Repositorios {#repositories-window}

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. En la página **Información general del programa**, seleccione la pestaña **Repositorios** para pasar a la página **Repositorios**.

1. La ventana **Repositorios** muestra todos los repositorios asociados con su programa.

   ![Ventana Repositorios](assets/repositories.png)

La ventana **Repositorios** proporciona detalles sobre los repositorios:

* El tipo de repositorio
   * **Adobe** indica repositorios administrados por Adobe
   * **GitHub** indica los repositorios de GitHub que se administran
* Cuándo se creó
* Canalizaciones asociadas con el repositorio

Puede seleccionar el repositorio en la ventana y hacer clic en el botón de puntos suspensivos para realizar una acción en el repositorio seleccionado.

* **[Comprobar ramas / Crear proyecto](#check-branches)** (solo disponible para repositorios de Adobe)
* **[Copiar URL del repositorio](#copy-url)**
* **[Ver y actualizar](#view-update)**
* **[Eliminar](#delete)**

![Acciones de repositorio](assets/repository-actions.png)

## Adición de repositorios {#adding-repositories}

Haga clic en el botón **Agregar repositorio** en la ventana **Repositorios** para iniciar el asistente **Agregar repositorio**.

![Asistente para la adición de repositorios](assets/add-repository-wizard.png)

Cloud Manager admite repositorios administrados por el Adobe (**Repositorio de Adobe**) y sus propios repositorios administrados por usted mismo (**Repositorio privado**). Los campos obligatorios difieren según el tipo de repositorio que decida añadir. Consulte los siguientes documentos para obtener más información.

* [Adición de repositorios de Adobe en Cloud Manager](adobe-repositories.md)
* [Adición de repositorios privados en Cloud Manager](private-repositories.md)

>[!NOTE]
>
>* Un usuario debe tener la función **Administrador de implementación** o **Propietario empresarial** para poder añadir un repositorio.
>* Hay un límite de 300 repositorios en todos los programas de cualquier compañía u organización de IMS.

## Acceder a la info del repositorio {#repo-info}

Al ver los repositorios en la ventana **Repositorios**, puede ver los detalles sobre cómo acceder mediante programación a los repositorios administrados por Adobe haciendo clic en el botón **Acceder a la info del repositorio** de la barra de herramientas.

![Información del repositorio](assets/access-repo-info.png)

La ventana **Información del repositorio** se abre con los detalles. Para obtener más información sobre el acceso a la información del repositorio, vea [Acceso a la información del repositorio](accessing-repositories.md).

## Comprobar ramas {#check-branches}

La acción **Comprobar ramas/Crear proyecto** realiza dos funciones según el estado del repositorio.

* AEM Si el repositorio es de reciente creación, la acción crea un proyecto de ejemplo basado en [el arquetipo del proyecto de la](https://experienceleague.adobe.com/es/docs/experience-manager-core-components/using/developing/archetype/overview).
* Si al repositorio ya se le ha creado el proyecto de muestra, compruebe el estado del repositorio y sus ramas e informes de nuevo si el proyecto de muestra ya existe.

![Acción Comprobar ramas](assets/check-branches.png)

## Copiar la URL del repositorio {#copy-url}

La acción **Copiar la URL del repositorio** copia la URL del repositorio seleccionado en la ventana **Repositorios** en el portapapeles para utilizarla en otra parte.

## Ver y actualizar {#view-update}

La acción **Ver y actualizar** abre el cuadro de diálogo **Actualizar repositorio**. Si lo usa, podrá ver **Name** y **vista previa de la URL del repositorio**, así como actualizar la **descripción** del repositorio.

![Ver y actualizar la información del repositorio](assets/update-repository.png)

## Eliminar {#delete}

La acción **Eliminar** elimina el repositorio del proyecto. Un repositorio no se puede eliminar si está asociado con una canalización.

![Eliminar](assets/delete.png)

Tenga en cuenta que cuando se elimina un repositorio en Cloud Manager, se marca como eliminado y ya no es accesible para el usuario, pero se mantiene en el sistema a efectos de recuperación.

Si intenta crear un repositorio nuevo después de eliminar uno con el mismo nombre, recibirá el mensaje de error `An error has occurred while trying to create repository. Contact your CSE or Adobe Support.`

Si recibe este mensaje de error, póngase en contacto con el Soporte técnico de Adobe para que le ayuden a cambiar el nombre del repositorio eliminado o a elegir un nombre diferente para el nuevo repositorio.
