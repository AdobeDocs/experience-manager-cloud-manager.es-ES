---
title: La herramienta Copia de contenido
description: La herramienta de copia de contenido de Cloud Manager permite a los usuarios copiar contenido mutable a petición desde sus entornos de producción AEM a entornos inferiores para realizar pruebas.
source-git-commit: 360cbf7e3a21e530a4e43f13f6d414dae4afa104
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 7%

---


# La herramienta Copia de contenido {#content-copy}

La herramienta de copia de contenido de Cloud Manager permite a los usuarios copiar contenido mutable a petición desde sus entornos de producción AEM a entornos inferiores para realizar pruebas.

## Introducción {#introduction}

Los datos actuales y reales son valiosos para fines de prueba, validación y aceptación por parte del usuario. La herramienta de copia de contenido le permite copiar contenido de su entorno de AEM de producción a un entorno de ensayo o desarrollo para dichas pruebas.

El contenido que se va a copiar se define mediante un conjunto de contenido. Un conjunto de contenido consta de una lista de rutas JCR que contienen el contenido mutable que se copiará de un entorno de origen a un entorno de destino dentro del mismo programa de Cloud Manager. Las siguientes rutas están permitidas en un conjunto de contenido.

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
```

Al copiar contenido, el entorno de origen es la fuente de la verdad.

* Si el contenido se ha modificado en el entorno de destino, se sobrescribe con el contenido en el origen, si las rutas son las mismas.
* Si las rutas son diferentes, el contenido del origen se combinará con el contenido del destino.

## Permisos {#permissions}

Para utilizar la herramienta de copia de contenido, el usuario debe estar asignado al **Administrador de implementación** en los entornos de origen y destino.

## Creación de un conjunto de contenido {#create-content-set}

Para poder copiar cualquier contenido, se debe definir un conjunto de contenido. Una vez definidos, los conjuntos de contenido se pueden reutilizar para copiar contenido. Siga estos pasos para crear un conjunto de contenido.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Vaya a la pantalla **Entornos** de la página **Información general**.

1. Vaya a la **Conjuntos de contenido** desde la página **Entornos** en el Navegador.

1. Toque o haga clic en el botón **Agregar conjunto de contenido** en la parte superior derecha de la pantalla.

   ![Conjuntos de contenido](/help/assets/content-sets.png)

1. En el **Detalles** del asistente, proporcione un nombre y una descripción para el conjunto de contenido y toque o haga clic en **Continuar**.

   ![Detalles del conjunto de contenido](/help/assets/add-content-set-details.png)

1. En el **Rutas de contenido** del asistente, especifique las rutas del contenido mutable que se incluirán en el conjunto de contenido.

   1. Introduzca la ruta en el **Agregar ruta de inclusión** campo .
   1. Toque o haga clic en el botón **Agregar ruta** para añadir la ruta al conjunto de contenido.
   1. Toque o haga clic en el botón **Agregar ruta** cuando sea necesario.

   ![Añadir rutas al conjunto de contenido](/help/assets/add-content-set-paths.png)

1. Si necesita refinar o restringir el conjunto de contenido, se pueden excluir las subrutas.

   1. En la lista de rutas incluidas, toque o haga clic en el botón **Añadir subrutas de exclusión** junto a la ruta que debe restringir.
   1. Introduzca la subruta que se excluirá debajo de la ruta seleccionada.
   1. Toque o haga clic **Excluir ruta**.
   1. Toque o haga clic **Añadir subrutas de exclusión** para añadir rutas adicionales que excluir según sea necesario.

   ![Exclusión de rutas](/help/assets/add-content-set-paths-excluded.png)

1. Si es necesario, puede modificar las rutas especificadas.

   1. Toque o haga clic en la X situada junto a las subrutas excluidas para eliminarlas.
   1. Toque o haga clic en el botón de puntos suspensivos situado junto a las rutas para mostrar **Editar** y **Eliminar** opciones.

   ![Edición de la lista de rutas](/help/assets/add-content-set-excluded-paths.png)

1. Toque o haga clic **Crear** para crear el conjunto de contenido.

El conjunto de contenido ahora se puede utilizar para copiar contenido entre entornos.

## Edición de un conjunto de contenido {#edit-content-set}

Siga pasos similares a los del crear un paso de contenido. En lugar de tocar o hacer clic **Agregar conjunto de contenido**, seleccione un conjunto existente de la consola y seleccione **Editar** en el menú elipsis.

![Editar conjunto de contenido](/help/assets/edit-content-set.png)

Al editar el conjunto de contenido, es posible que tenga que expandir las rutas configuradas para mostrar las subrutas excluidas.

## Copia de contenido {#copy-content}

Una vez creado un conjunto de contenido, puede utilizarlo para copiar contenido. Siga estos pasos para copiar contenido.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Vaya a la pantalla **Entornos** de la página **Información general**.

1. Vaya a la **Conjuntos de contenido** desde la página **Entornos** en el Navegador.

1. Seleccione un conjunto de contenido de la consola y seleccione **Copiar contenido** en el menú elipsis.

   ![Copia de contenido](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Es posible que no se pueda seleccionar un entorno si:
   >
   >* El usuario no tiene los permisos adecuados.
   >* El entorno tiene una canalización en ejecución o una operación de copia de contenido en curso.


1. En el **Copiar contenido** especifique el origen y el destino de la acción de copia de contenido.

   ![Copia de contenido](/help/assets/copying-content.png)

1. Toque o haga clic **Copiar**.

Se inicia el proceso de copia. El estado del proceso de copia se refleja en la consola del conjunto de contenido seleccionado.

## Actividad de copia de contenido {#copy-activity}

Puede controlar el estado de los procesos de copia en la variable **Copiar actividad de contenido** página.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Vaya a la pantalla **Entornos** de la página **Información general**.

1. Vaya a la **Copiar actividad de contenido** desde la página **Entornos** en el Navegador.

![Actividad de copia de contenido](/help/assets/copy-content-activity.png)

### Estados de copia de contenido {#statuses}

Una vez que empiece a copiar contenido, el proceso puede tener uno de los siguientes estados.

| Estado | Descripción |
|---|---|
| En curso | La operación de copia de contenido está en curso |
| Error | Error en la operación de copia de contenido |
| Completado | La operación de copia de contenido se completó correctamente |

## Restricciones {#limitations}

La herramienta de copia de contenido tiene las siguientes limitaciones.

* No se puede realizar una copia de contenido desde un entorno inferior a un entorno superior.
* La copia de contenido solo se puede realizar en el mismo nivel (es decir, autor-autor o publicación-publicación).
* No es posible copiar contenido entre programas.
* No es posible ejecutar operaciones de copia de contenido concurrentes en el mismo entorno.
* La copia de contenido no se puede realizar si hay alguna operación activa ejecutándose en el entorno de destino o de origen, como una canalización CI/CD.
* Se pueden especificar hasta diez rutas por conjunto de contenido. No hay limitación en las rutas excluidas.
* La herramienta de copia de contenido no debe utilizarse como herramienta de clonación o espejado, ya que no puede rastrear el contenido movido o eliminado del origen.
* La herramienta de copia de contenido no tiene capacidad de creación de versiones y no puede detectar automáticamente contenido modificado o contenido recién creado en el entorno de origen en un conjunto de contenido desde la última operación de copia de contenido.
   * Si desea actualizar el entorno de destino con cambios de contenido solo desde la última operación de copia de contenido, debe crear un conjunto de contenido. En ese conjunto, especifique las rutas en la instancia de origen en la que se han realizado cambios desde la última operación de copia de contenido.
* La información de la versión no se incluye en una copia de contenido.
