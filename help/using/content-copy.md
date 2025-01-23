---
title: Copia de contenido para la coherencia del entorno
description: La copia de contenido en Cloud Manager permite a los usuarios copiar contenido mutable On-demand desde los entornos de producción de Adobe Experience Manager 6.x alojados en Adobe Managed Services a entornos inferiores para realizar pruebas.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 84b3366481c2efd497583627eac67046452f6c38
workflow-type: ht
source-wordcount: '1321'
ht-degree: 100%

---


# Copia de contenido para la coherencia del entorno {#content-copy}

La copia de contenido en Cloud Manager permite a los usuarios copiar contenido mutable On-demand desde los entornos de producción de Adobe Experience Manager 6.x alojados en Adobe Managed Services a entornos inferiores para realizar pruebas.

## Acerca de la copia de contenido {#introduction}

Los datos actuales y reales son valiosos para las pruebas, la validación y la aceptación de usuarios. La copia de contenido le permite copiar contenido de su entorno AEM 6.x alojado en AMS de producción a un entorno de ensayo o desarrollo. Este flujo de trabajo admite varios escenarios de prueba.

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

Si edita contenido en el entorno de destino, el contenido de origen lo sobrescribe si las rutas coinciden.

Si las rutas son diferentes, el contenido del origen se combinará con el contenido del destino.

### Permisos {#permissions}

Para utilizar la función de copia de contenido, el usuario debe estar asignado a la función de **Administrador de implementación** en los entornos de origen y destino.

## Creación de un conjunto de contenido {#create-content-set}

Para poder copiar cualquier contenido, se debe definir un conjunto de contenido. Una vez definidos, los conjuntos de contenido se pueden reutilizar para copiar contenido. Siga estos pasos para crear un conjunto de contenido.

**Para crear un conjunto de contenido:**

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. En la esquina superior izquierda de la página, haga clic en el ![icono de Mostrar menú](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para abrir el menú del lado izquierdo.

1. En el menú del lado izquierdo, en la página **Servicios**, haga clic en el ![icono de Cuadro ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Conjuntos de contenido**.

1. Cerca de la esquina superior derecha de la página, haga clic en **Añadir conjunto de contenido**.

   ![Conjuntos de contenido](/help/assets/content-sets.png)

1. En el cuadro de diálogo **`Add Content Set`**, en la ficha **Detalles**, en los campos **Nombre** y **Descripción**, escriba un nombre y una descripción opcional para el conjunto de contenido y, a continuación, haga clic en **Continuar**.

   ![Detalles del conjunto de contenido](/help/assets/add-content-set-details.png)

1. En la ficha **Rutas de contenido**, en el campo de texto **Ruta**, especifique una ruta al contenido que se pueda cambiar y se deba incluir en el conjunto de contenido.

   Solo se pueden incluir las rutas que comienzan con `/content`, `/conf`, `/etc`, `/var/workflow/models` o `/var/commerce`.

1. Haga clic en el ![icono de adición de carpeta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg) **Añadir ruta** para añadir (o incluir) la ruta al conjunto de contenido.

1. (Opcional) Si es necesario, añada las rutas de adición (hasta 50) que sean necesarias repitiendo los dos pasos anteriores. De lo contrario, continúe con el siguiente paso.

   ![Añadir rutas al conjunto de contenido](/help/assets/add-content-set-paths.png)

1. (Opcional) Para reducir el conjunto de contenido, puede especificar, opcionalmente, subrutas dentro de una ruta de contenido incluida que deban excluirse.

   1. A la derecha de una ruta de contenido incluida que desee restringir, haga clic en el ![icono de eliminación de carpeta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg).
   1. En el campo de texto, escriba una ruta relativa a la ruta raíz que aparece en el cuadro de diálogo.
   1. Haga clic en el ![icono de eliminación de carpeta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **Excluir ruta**.
   1. Si es necesario, repita los pasos i. a iii. arriba para añadir más rutas de exclusión; no hay limitación. De lo contrario, continúe con el siguiente paso.

   ![Exclusión de rutas](/help/assets/add-content-set-paths-excluded.png)

1. (Opcional) Realice una de las siguientes acciones:

   1. Haga clic en el ![icono 500 de tamaño cruzado](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) a la derecha de una subruta excluida para eliminarla.
   1. Haga clic en el ![icono de Más](https://spectrum.adobe.com/static/icons/ui_18/More.svg) a la derecha de la ruta de contenido incluida y, a continuación, haga clic en **Editar** o **Eliminar**.

   ![Edición de la lista de rutas](/help/assets/add-content-set-excluded-paths.png)

1. Haga clic en **Crear**. Ahora puede utilizar el conjunto de contenido para copiar contenido entre entornos.

## Edición o eliminación de un conjunto de contenido {#edit-content-set}

Al editar el conjunto de contenido, es posible que tenga que expandir las rutas configuradas para mostrar las subrutas excluidas.

**Para editar o eliminar un conjunto de contenido:**

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. En la esquina superior izquierda de la página, haga clic en el ![icono de Mostrar menú](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para mostrar el menú del lado izquierdo.

1. En el menú del lado izquierdo, debajo de **Servicios**, haga clic en el ![icono de Cuadro ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Conjuntos de contenido**.

1. En la tabla de la página **Conjuntos de contenido**, haga clic en el ![icono de Más](https://spectrum.adobe.com/static/icons/ui_18/More.svg) a la derecha de una ruta de contenido incluida y, a continuación, haga clic en **Editar** o **Eliminar**.

![Editar conjunto de contenido](/help/assets/edit-content-set.png)

## Copiar contenido {#copy-content}

Una vez creado un conjunto de contenido, puede utilizarlo para copiar contenido.

Es posible que un entorno no esté disponible para su selección si se aplica cualquiera de las siguientes condiciones:

* El usuario carece de los permisos necesarios.
* Se está ejecutando una operación de canalización o de copia de contenido en el entorno.

**Para copiar contenido:**

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. En la esquina superior izquierda de la página, haga clic en el ![icono de Mostrar menú](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para mostrar el menú del lado izquierdo.

1. En el menú del lado izquierdo, debajo de **Servicios**, haga clic en el ![icono de Cuadro ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Conjuntos de contenido**.

1. En la tabla de la página **Conjuntos de contenido**, a la derecha de la ruta de contenido incluida que desea copiar, haga clic en el ![icono de Más](https://spectrum.adobe.com/static/icons/ui_18/More.svg) y, a continuación, haga clic en **Copiar contenido**.

   ![Copia de contenido](/help/assets/copy-content.png)

1. En el cuadro de diálogo **Copiar contenido**, seleccione el entorno **Origen** y el entorno **Destino** para la acción de copia de contenido.

   * Las regiones de un entorno de destino deben ser un subconjunto de las regiones de un entorno de origen.
   * Los problemas de compatibilidad se comprueban antes de ejecutar una acción de copia de contenido. Al seleccionar el entorno **Destino**, el sistema valida automáticamente los entornos de origen y destino. Si la validación falla, el proceso se detiene y aparece un mensaje de error en el cuadro de diálogo que explica el motivo del error.

     ![Copia de contenido](/help/assets/copying-content.png)

1. (Opcional) Realice una de las siguientes acciones:

   1. Para *conservar* las rutas excluidas en el entorno de destino, marque **`Do not delete exclude paths from destination`**. Esta configuración mantiene intactas las rutas excluidas especificadas en el conjunto de contenido.
   1. Para *quitar* las rutas excluidas en el entorno de destino, desmarque **`Do not delete exclude paths from destination`**. Esta configuración elimina las rutas excluidas especificadas en el conjunto de contenido.
   1. Para copiar el historial de versiones de las rutas del entorno de origen en el entorno de destino, marque **Copiar versiones**. El proceso de copia de contenido es considerablemente más rápido cuando *no* se copia el historial de versiones.

1. Haga clic en **Copiar**. El estado del proceso de copia se refleja en la consola del conjunto de contenido seleccionado.

## Comprobación del estado de una copia de contenido {#copy-activity}

Puede controlar el estado de los procesos de la copia en la página **Copiar actividad de contenido**.

**Para comprobar el estado de una copia de contenido:**

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) y seleccione la organización y programa adecuados.

1. En la esquina superior izquierda de la página, haga clic en el ![icono de Mostrar menú](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) para mostrar el menú del lado izquierdo.

1. En el menú del lado izquierdo, debajo de **Servicios**, haga clic en el ![icono de Historial ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **Actividad de copia de contenido**.

   ![Actividad de la copia de contenido](/help/assets/copy-content-activity.png)

   Un proceso de copia de contenido puede tener uno de los siguientes estados:

   | Estado | Descripción |
   | --- | --- |
   | En curso | El proceso de copia de contenido está en curso. |
   | Completado | El proceso de copia de contenido se ha completado correctamente. |
   | Error | Error en el proceso de copia de contenido. |

## Limitaciones de la copia de contenido {#limitations}

* No se puede realizar una copia de contenido de un entorno inferior a un entorno superior.
* La copia de contenido solo se puede realizar en el mismo nivel. Es decir, autor-autor o publicación-publicación.
* No es posible copiar contenido entre programas o entre regiones.
* La copia de contenido para la topología basada en el almacén de datos en la nube solo se puede realizar cuando el entorno de origen y de destino están en el mismo proveedor de nube y en la misma región.
* No es posible ejecutar operaciones de copia de contenido simultáneas en el mismo entorno.
* La copia de contenido no se puede realizar si hay alguna operación activa ejecutándose en el entorno de destino o de origen, como, por ejemplo, una canalización de CI/CD.
* La copia de contenido no debe utilizarse como una herramienta de clonación o espejo, ya que no puede rastrear el contenido movido o eliminado del origen.
* Una copia de contenido no se puede pausar ni cancelar una vez que se inicia.
* La copia de contenido duplica los recursos junto con metadatos de Dynamic Media desde el entorno superior al entorno inferior seleccionado. A continuación, los recursos copiados deben volver a procesarse mediante la variable [Flujo de trabajo de recursos de proceso DAM](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/assets/using/assets-workflow) en el entorno inferior para utilizar la configuración de Dynamic Media correspondiente.
* No se admiten [configuraciones de Dynamic Media con tamaños de recursos superiores a 2 GB habilitados](https://experienceleague.adobe.com/es/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb).
* Las regiones del entorno de destino deben ser las mismas o un subconjunto de las regiones del entorno de origen.

## Problemas conocidos de la copia de contenido {#known-issues}

{{content-copy-known-issues}}
