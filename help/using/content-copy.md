---
title: La herramienta Copia de contenido
description: La herramienta de copia de contenido de Cloud Manager AEM permite a los usuarios copiar contenido mutable bajo demanda desde entornos de producción de la versión 6.x de la alojada en AMS a entornos más bajos para realizar pruebas.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '1076'
ht-degree: 36%

---


# La herramienta de copia de contenido {#content-copy}

La herramienta de copia de contenido de Cloud Manager AEM permite a los usuarios copiar contenido mutable bajo demanda desde entornos de producción de la versión 6.x de la alojada en AMS a entornos más bajos para realizar pruebas.

## Introducción {#introduction}

Los datos actuales y reales son valiosos para las pruebas, la validación y la aceptación de usuarios. AEM La herramienta de copia de contenido le permite copiar contenido del entorno de producción AMS-alojado en la versión 6.x a entornos de ensayo o desarrollo. Este flujo de trabajo admite varios escenarios de prueba.

Un conjunto de contenido define el contenido que se va a copiar. Un conjunto de contenido incluye una lista de rutas JCR con el contenido mutable que se va a copiar. El contenido pasa de un entorno de origen a un entorno de destino. Todo dentro del mismo programa de Cloud Manager.

Se permiten las siguientes rutas en un conjunto de contenido:

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

Al copiar contenido, el entorno de origen es la fuente de información.

* Si edita contenido en el entorno de destino, el contenido de origen lo sobrescribe si las rutas coinciden.
* Si las rutas son diferentes, el contenido del origen se combina con el contenido del destino.

## Permisos {#permissions}

Para usar la herramienta de copia de contenido, el usuario debe estar asignado al rol **Administrador de implementación** en los entornos de origen y destino.

## Creación de un conjunto de contenido {#create-content-set}

Para poder copiar cualquier contenido, se debe definir un conjunto de contenido. Una vez definidos, los conjuntos de contenido se pueden reutilizar para copiar contenido. Siga estos pasos para crear un conjunto de contenido.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Desde la página **Información general**, vaya a la pantalla **Entornos**.

1. Desde la pantalla **Entornos**, vaya a la página **Conjuntos de contenido**.

1. Cerca de la parte superior derecha de la pantalla, haga clic en **Agregar conjunto de contenido**.

   ![Conjuntos de contenido](/help/assets/content-sets.png)

1. En la ficha **Detalles** del asistente, proporcione un nombre y una descripción para el conjunto de contenido y haga clic en **Continuar**.

   ![Detalles del conjunto de contenido](/help/assets/add-content-set-details.png)

1. En la pestaña **Rutas de contenido** del asistente, especifique las rutas del contenido mutable que se incluirán en el conjunto de contenido.

   1. Introduzca la ruta en el campo **Añadir ruta de inclusión**.
   1. Haga clic en **Agregar ruta** para agregar la ruta al conjunto de contenido.
   1. Vuelva a hacer clic en **Agregar ruta** según sea necesario.

   ![Añadir rutas al conjunto de contenido](/help/assets/add-content-set-paths.png)

1. Si es necesario precisar o restringir el conjunto de contenido, se pueden excluir las subrutas.

   1. En la lista de rutas incluidas, haga clic en el icono **Agregar subrutas de exclusión** situado junto a la ruta que debe restringir.
   1. Introduzca la subruta que desea excluir de la ruta seleccionada.
   1. Haga clic en **Excluir ruta**.
   1. De nuevo, haga clic en **Agregar subrutas de exclusión** para agregar rutas adicionales que se excluirán según sea necesario.

   ![Exclusión de rutas](/help/assets/add-content-set-paths-excluded.png)

1. Si es necesario, puede modificar las rutas especificadas.

   1. Haga clic en `X` al lado de las subrutas excluidas para eliminarlas.
   1. Haga clic en el botón de los tres puntos situado junto a las rutas para mostrar las opciones **Editar** y **Eliminar**.

   ![Edición de la lista de rutas](/help/assets/add-content-set-excluded-paths.png)

1. Haga clic en **Crear** para crear el conjunto de contenido.

A partir de ahora, se puede utilizar el conjunto de contenido para copiar contenido entre entornos.

>[!NOTE]
>
>Puede añadir hasta 50 rutas en un conjunto de contenido.
>No hay limitación en las rutas excluidas.

## Edición de un conjunto de contenido {#edit-content-set}

Siga los mismos pasos que para la creación de un paso de contenido. En lugar de hacer clic en **Agregar conjunto de contenido**, seleccione un conjunto existente de la consola y seleccione **Editar** del menú de los tres puntos.

![Editar conjunto de contenido](/help/assets/edit-content-set.png)

Al editar el conjunto de contenido, es posible que tenga que expandir las rutas configuradas para mostrar las subrutas excluidas.

## Copia de contenido {#copy-content}

Una vez creado un conjunto de contenido, puede utilizarlo para copiar contenido. Siga estos pasos para copiar contenido.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. Desde la página **Información general**, vaya a la pantalla **Entornos**.

1. Desde la pantalla **Entornos**, vaya a la página **Conjuntos de contenido**.

1. Seleccione un conjunto de contenido de la consola y seleccione **Copiar contenido** en el menú de puntos suspensivos.

   ![Copia de contenido](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Es posible que no se pueda seleccionar un entorno si ocurre lo siguiente:
   >
   >* El usuario no tiene los permisos adecuados.
   >* El entorno tiene una canalización en ejecución o una operación de copia de contenido en curso.

1. En el cuadro de diálogo **Copiar contenido**, especifique el origen y el destino de la acción de copia de contenido.

1. Puede elegir eliminar o conservar las rutas de exclusión en el entorno de destino. Seleccione la casilla de verificación `Do not delete exclude paths from destination` para conservar `exclude paths` que se han especificado en el conjunto de contenido. Si la casilla de verificación no está marcada, las rutas de exclusión se eliminan en el entorno de destino.

1. Puede elegir copiar el historial de versiones de las rutas que se copian del entorno de origen al de destino. Seleccione la casilla de verificación `Copy Versions` si desea copiar todos los historiales de versiones.

   ![Copia de contenido](/help/assets/copying-content.png)

1. Haga clic en **Copiar**.

Se inicia el proceso de copia. El estado del proceso de copia se refleja en la consola del conjunto de contenido seleccionado.

## Actividad de copia de contenido {#copy-activity}

Puede controlar el estado de los procesos de la copia en la página **Copiar actividad de contenido**.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y, a continuación, seleccione la organización y el programa adecuados.

1. Desde la página **Información general**, vaya a la pantalla **Entornos**.

1. Desde la pantalla **Entornos**, vaya a la página **Copiar actividad de contenido**.

![Actividad de la copia de contenido](/help/assets/copy-content-activity.png)

### Estados de copia de contenido {#statuses}

Una vez que empiece a copiar contenido, el proceso puede tener uno de los siguientes estados.

| Estado | Descripción |
|---|---|
| En curso | La operación de copia de contenido está en curso |
| Error | Error en la operación de copia de contenido |
| Completado | La operación de copia de contenido se ha completado correctamente |

## Restricciones {#limitations}

La herramienta de copia de contenido tiene las siguientes limitaciones.

* No se puede realizar una copia de contenido de un entorno inferior a un entorno superior.
* La copia de contenido solo se puede realizar dentro del mismo nivel. Es decir, autor-autor o publicación-publicación.
* No es posible copiar contenido entre programas o entre regiones.
* La copia de contenido para la topología basada en el almacén de datos de la nube solo se puede realizar cuando los entornos de origen y destino están en el mismo proveedor de la nube y en la misma región.
* No es posible ejecutar operaciones de copia de contenido simultáneas en el mismo entorno.
* No se puede realizar la copia de contenido si hay alguna operación activa ejecutándose en el entorno de destino o de origen, como una canalización CI/CD.
* Se pueden especificar hasta cincuenta rutas por cada conjunto de contenido. No hay limitación en las rutas excluidas.
* La herramienta de copia de contenido no debe utilizarse como herramienta de clonación o creación de reflejo porque no puede realizar el seguimiento del contenido movido o eliminado en el origen.
* No puede pausar ni cancelar una copia de contenido después de iniciarla.
* La herramienta de copia de contenido transfiere recursos y metadatos de Dynamic Media del entorno superior al entorno inferior seleccionado. A continuación, es necesario volver a procesar los recursos copiados mediante el [flujo de trabajo de recursos de proceso DAM](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/assets/using/assets-workflow) en el entorno inferior para utilizar la configuración de Dynamic Media correspondiente.

* Cuando no se copia el historial de versiones, el proceso de copia de contenido es considerablemente más rápido.
