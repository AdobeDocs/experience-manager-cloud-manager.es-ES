---
title: La herramienta Copia de contenido
description: La herramienta de copia de contenido de Cloud Manager permite a los usuarios copiar contenido mutable bajo demanda desde sus entornos de producción de AEM a entornos inferiores para realizar pruebas.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 7ef29a244688de82537da0b879fbf397900427c0
workflow-type: ht
source-wordcount: '1083'
ht-degree: 100%

---

# La herramienta Copia de contenido {#content-copy}

La herramienta de copia de contenido de Cloud Manager permite a los usuarios copiar contenido mutable bajo demanda desde sus entornos de producción de AEM a entornos inferiores para realizar pruebas.

## Introducción {#introduction}

Los datos actuales y reales son valiosos para las pruebas, la validación y la aceptación de usuarios. La herramienta de copia de contenido permite copiar contenido del entorno de AEM de producción a un entorno de ensayo o desarrollo para realizar dichas pruebas.

El contenido que se va a copiar se define mediante un conjunto de contenido. Un conjunto de contenido consta de una lista de rutas JCR que contienen el contenido mutable que se copiará de un entorno de origen a un entorno de destino dentro del mismo programa de Cloud Manager. Se permiten las siguientes rutas en un conjunto de contenido.

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
```

Al copiar contenido, el entorno de origen es la fuente de información.

* Si el contenido se ha modificado en el entorno de destino, se sobrescribirá con el contenido en el origen, si las rutas son las mismas.
* Si las rutas son diferentes, el contenido del origen se combinará con el contenido del destino.

   >[!NOTE]
   >
   >Solo se admiten topologías basadas en el almacén de datos de archivos.

## Permisos {#permissions}

Para utilizar la herramienta de copia de contenido, el usuario debe estar asignado a la función de **Administrador de implementación** en los entornos de origen y destino.

## Creación de un conjunto de contenido {#create-content-set}

Para poder copiar cualquier contenido, se debe definir un conjunto de contenido. Una vez definidos, los conjuntos de contenido se pueden reutilizar para copiar contenido. Siga estos pasos para crear un conjunto de contenido.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Vaya a la pantalla **Entornos** de la página **Información general**.

1. Vaya a la página **Conjuntos de contenido** en la pantalla **Entornos**.

1. Pulse o haga clic en el botón **Añadir conjunto de contenido** en la parte superior derecha de la pantalla.

   ![Conjuntos de contenido](/help/assets/content-sets.png)

1. En la pestaña **Detalles** del asistente, proporcione un nombre y una descripción para el conjunto de contenido y pulse o haga clic en **Continuar**.

   ![Detalles del conjunto de contenido](/help/assets/add-content-set-details.png)

1. En la pestaña **Rutas de contenido** del asistente, especifique las rutas del contenido mutable que se incluirán en el conjunto de contenido.

   1. Introduzca la ruta en el campo **Añadir ruta de inclusión**.
   1. Pulse o haga clic en el botón **Añadir ruta** para agregar la ruta al conjunto de contenido.
   1. Pulse o haga clic de nuevo en el botón **Añadir ruta** cuando sea necesario.

   ![Añadir rutas al conjunto de contenido](/help/assets/add-content-set-paths.png)

1. Si es necesario precisar o restringir el conjunto de contenido, se pueden excluir las subrutas.

   1. En la lista de rutas incluidas, pulse o haga clic en el botón **Añadir subrutas de exclusión** junto a la ruta que debe restringir.
   1. Introduzca la subruta que se excluirá debajo de la ruta seleccionada.
   1. Pulse o haga clic en **Excluir ruta**.
   1. Pulse o haga clic en **Añadir subrutas de exclusión** para agregar rutas adicionales para excluir según sea necesario.

   ![Exclusión de rutas](/help/assets/add-content-set-paths-excluded.png)

1. Si es necesario, puede modificar las rutas especificadas.

   1. Pulse o haga clic en la X situada junto a las subrutas excluidas para eliminarlas.
   1. Pulse o haga clic en el botón de puntos suspensivos situado junto a las rutas para mostrar las opciones **Editar** y **Eliminar**.

   ![Edición de la lista de rutas](/help/assets/add-content-set-excluded-paths.png)

1. Pulse o haga clic en **Crear** para crear el conjunto de contenido.

A partir de ahora, se puede utilizar el conjunto de contenido para copiar contenido entre entornos.

>[!NOTE]
>
>Puede añadir hasta 50 rutas en un conjunto de contenido.
>No hay limitación en las rutas excluidas.

## Edición de un conjunto de contenido {#edit-content-set}

Siga los mismos pasos que para la creación de un paso de contenido. En lugar de pulsar o hacer clic en **Añadir conjunto de contenido**, seleccione un conjunto existente de la consola y seleccione **Editar** en el menú de puntos suspensivos.

![Editar conjunto de contenido](/help/assets/edit-content-set.png)

Al editar el conjunto de contenido, es posible que tenga que expandir las rutas configuradas para mostrar las subrutas excluidas.

## Copia de contenido {#copy-content}

Una vez creado un conjunto de contenido, puede utilizarlo para copiar contenido. Siga estos pasos para copiar contenido.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Vaya a la pantalla **Entornos** de la página **Información general**.

1. Vaya a la página **Conjuntos de contenido** en la pantalla **Entornos**.

1. Seleccione un conjunto de contenido de la consola y seleccione **Copiar contenido** en el menú de puntos suspensivos.

   ![Copia de contenido](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Es posible que no se pueda seleccionar un entorno si ocurre lo siguiente:
   >
   >* El usuario no tiene los permisos adecuados.
   >* El entorno tiene una canalización en ejecución o una operación de copia de contenido en curso.


1. En el diálogo **Copiar contenido**, especifique el origen y el destino de la acción de copia de contenido.

1. Puede optar por eliminar o conservar las rutas de exclusión en el entorno destinatario. Seleccione la casilla de verificación `Do not delete exclude paths from destination` si desea conservar las rutas de exclusión especificadas en el conjunto de contenido. Si la casilla de verificación se deja sin marcar, las rutas de exclusión se eliminarán del entorno destinatario.

   ![Copia de contenido](/help/assets/copying-content.png)

1. Pulse o haga clic en **Copiar**.

Se inicia el proceso de copia. El estado del proceso de copia se refleja en la consola del conjunto de contenido seleccionado.

## Actividad de la copia de contenido {#copy-activity}

Puede controlar el estado de los procesos de la copia en la página **Copiar actividad de contenido**.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Vaya a la pantalla **Entornos** de la página **Información general**.

1. Vaya a la página **Copiar actividad de contenido** en la pantalla **Entornos**.

![Actividad de la copia de contenido](/help/assets/copy-content-activity.png)

### Estados de la copia de contenido {#statuses}

Una vez que empiece a copiar contenido, el proceso puede tener uno de los siguientes estados.

| Estado | Descripción |
|---|---|
| En curso | La operación de copia de contenido está en curso |
| Error | Error en la operación de copia de contenido |
| Completado | La operación de copia de contenido se ha completado correctamente |

## Restricciones {#limitations}

La herramienta de copia de contenido tiene las siguientes limitaciones.

* No se puede realizar una copia de contenido de un entorno inferior a un entorno superior.
* La copia de contenido solo se puede realizar en el mismo nivel (es decir, autor-autor o publicación-publicación).
* No es posible copiar contenido entre programas.
* No es posible ejecutar operaciones de copia de contenido simultáneas en el mismo entorno.
* La copia de contenido no se puede realizar si hay alguna operación activa ejecutándose en el entorno de destino o de origen, como, por ejemplo, una canalización de CI/CD.
* Se pueden especificar hasta cincuenta rutas por cada conjunto de contenido. No hay limitación en las rutas excluidas.
* La herramienta de copia de contenido no debe utilizarse como una herramienta de clonación o reflejo, ya que no puede rastrear el contenido movido o eliminado del origen.
* La herramienta de copia de contenido no tiene capacidad de creación de versiones y no puede detectar automáticamente contenido modificado o recién creado en el entorno de origen en un conjunto de contenido desde la última operación de copia de contenido.
   * Si desea actualizar el entorno de destino con cambios de contenido solo desde la última operación de copia de contenido, debe crear un conjunto de contenido. En ese conjunto, especifique las rutas en la instancia de origen en la que se realizaron cambios desde la última operación de copia de contenido.
* La información de la versión no se incluye en una copia de contenido.
