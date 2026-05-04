---
title: Adición de un repositorio de Adobe en Cloud Manager
description: Aprenda a añadir repositorios administrados por Adobe en Cloud Manager.
exl-id: 24c6ca97-ea70-41b8-b4c7-b8b0f406a57d
TQID: https://experienceleague.adobe.com/LBI6V07enOlxe8yh-XwlkL-mdMWR0MJyKi1gUQtjtK4
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 241
ht-degree: 100%

---

# Adición de un repositorio de Adobe en Cloud Manager {#adobe-repositories}

Aprenda a añadir un repositorio administrado por Adobe en Cloud Manager.

La página **Repositorios** facilita la adición de repositorios adicionales administrados por Adobe al programa seleccionado.

**Para añadir un repositorio de Adobe en Cloud Manager:**

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y el programa adecuados al que desea añadir un repositorio administrado por Adobe.

1. En la página **Resumen del programa**, en el menú lateral, haga clic en la pestaña ![icono de carpeta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Repositorios**.

1. En la página **Repositorios**, junto a la esquina superior derecha, haga clic en **Agregar repositorio**.

   ![Botón Añadir repositorio](/help/managing-code/assets/repositories-tab.png)

1. En el cuadro de diálogo **Agregar repositorio**, asegúrese de que **Repositorio de Adobe** está seleccionado como tipo de repositorio.

1. En los campos de texto correspondientes, introduzca lo siguiente:

   * **Nombre del repositorio**: un nombre expresivo para el nuevo repositorio.
   * **Vista previa de la URL del repositorio**: no es necesario que escriba una ruta de URL ni que edite la ruta existente porque la infraestructura del repositorio ya está configurada y está totalmente integrada y administrada por Adobe.
   * **Descripción (opcional)**: una descripción detallada del repositorio.

   ![Cuadro de diálogo Agregar repositorio](/help/managing-code/assets/repository-add-adobe.png)

1. Haga clic en **Guardar**.
El nuevo repositorio se muestra en la tabla de la página **Repositorios**.

Ahora puede asociar una [Canalización de CI/CD](/help/overview/ci-cd-pipelines.md) con él o administrarlo dentro de la página [**Repositorios**](/help/managing-code/managing-repositories.md).

>[!TIP]
>
>También puede añadir repositorios de GitHub que administre usted mismo como [repositorios privados](/help/managing-code/private-repositories.md).
