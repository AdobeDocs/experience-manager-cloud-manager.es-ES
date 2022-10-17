---
title: Repositorios de Cloud Manager
description: Obtenga información sobre cómo acceder, crear y editar repositorios para sus programas de Cloud Manager.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: ht
source-wordcount: '666'
ht-degree: 100%

---


# Repositorios de Cloud Manager {#cloud-manager-repos}

En los repositorios es donde administra el código usando Git. Obtenga información sobre cómo crear repositorios para sus programas de Cloud Manager.

## Acceso a repositorios {#accessing-repos}

Puede acceder a sus repositorios de Git y administrarlos en un autoservicio desde Cloud Manager.

Para acceder al repositorio, utilice el botón **Acceder a la info del repositorio** disponible en Cloud Manager, de forma más destacada en la tarjeta de canalización.

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) y seleccione la organización y programa adecuados.

1. Vaya a la tarjeta **Canalizaciones** desde la página **Resumen del programa** y verá la opción **Acceder a la info del repositorio** para acceder y administrar su repositorio de Git [configurado con esta canalización.](/help/using/production-pipelines.md)

   ![Botón Acceder a la info del repositorio](/help/assets/access-repo1.png)

1. Si cambia a la pestaña de canalización **No son de producción**, la opción **Acceder a la info del repositorio** también está disponible como [configurada para la canalización.](/help/using/non-production-pipelines.md)

   ![Canalizaciones que no son de producción](/help/assets/access-repo-nonprod.png)

1. Haga clic en el botón **Acceder a la info del repositorio** para abrir un cuadro de diálogo que contenga lo siguiente:

   * La URL del repositorio de Git
   * Nombre de usuario
   * Contraseña
   * El comando Git para ejecutar la clonación del repositorio localmente

   ![El cuadro de diálogo Información del repositorio](/help/assets/access-repo-create.png)

Utilice la información proporcionada para clonar el repositorio localmente y así iniciar el desarrollo local.

>[!NOTE]
>
>La variable **Acceder a la info del repositorio** es visible para los usuarios con la función **Desarrollador** o **Administrador de implementación**.

## Adición de repositorios {#add-repos}

Siga estos pasos para agregar repositorios en Cloud Manager:

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) y seleccione la organización y programa adecuados.

1. Desde la página **Resumen del programa**, haga clic en la pestaña **Repositorios** y vaya a la página **Repositorios**.

1. Haga clic en **Agregar repositorio** para lanzar el asistente.

   >[!NOTE]
   >
   >Debe tener la función **Administrador de implementación** o **Propietario empresarial** para agregar un repositorio.

   ![Agregar repositorio](/help/assets/create-repo2.png)

1. Introduzca el nombre y la descripción como se solicita y haga clic en **Guardar**.

   ![Detalles del repositorio](/help/assets/repo-1.png)

1. Seleccione **Guardar**.

Se mostrará el repositorio recién creado.

![Nuevo repositorio creado](/help/assets/create-repo3.png)

Los repositorios creados en Cloud Manager están disponibles para que usted los seleccione al [crear sus canalizaciones.](/help/overview/ci-cd-pipelines.md)

## Ver y editar repositorios {#edit-repos}

Siga estos pasos para editar y ver repositorios en Cloud Manager:

1. Inicie sesión en Cloud Manager en [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) y seleccione la organización y programas adecuados.

1. En la página **Resumen del programa**, haga clic en la pestaña **Repositorios** y vaya a la página **Repositorios**. Aquí puede ver los detalles de sus repositorios existentes.

1. Seleccione el repositorio y haga clic en el botón de elipsis en la parte más a la derecha de la tabla para **Copiar URL del repositorio**, **Ver y actualizar el estado** o **Eliminar** su repositorio.

![Editar repositorio](/help/assets/create-repo3.png)

## Compatibilidad con el submódulo Git {#git-submodule-support}

Los submódulos Git se pueden usar para combinar el contenido de varias ramas en repositorios Git en el momento de la compilación.

Cuando se ejecuta el proceso de creación de Cloud Manager, después de clonar el repositorio configurado para la canalización y de verificar la rama configurada, si la rama contiene un archivo `.gitmodules` en el directorio raíz, se ejecuta el comando.

```
$ git submodule update --init
```

Esto comprobará que cada submódulo esté en el directorio apropiado. Esta técnica es una alternativa potencial a [trabajar con varios repositorios Git de origen](/help/managing-code/multiple-git-repos.md) para organizaciones que se sienten cómodas con el uso de submódulos Git y no desean administrar un proceso de combinación externo.

Por ejemplo, supongamos que hay tres repositorios, cada uno de los cuales contiene una sola rama denominada `main`. En el repositorio “principal”, es decir, el configurado en las canalizaciones, la rama `main` tiene el archivo `pom.xml` que enumera los proyectos contenidos en los otros dos repositorios:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

Luego debe agregar submódulos para los otros dos repositorios:

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Esto da como resultado el archivo `.gitmodules` que tiene este aspecto:

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

Puede encontrar más información sobre los submódulos Git en el [Manual de referencia de Git](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

### Restricciones     {#limitations}

Cuando utilice submódulos Git, tenga en cuenta lo siguiente:

* La dirección URL de Git debe ser exacta como la sintaxis descrita anteriormente.
* Por motivos de seguridad, no incruste credenciales en estas direcciones URL.
* Solo se admiten submódulos en la raíz de la rama.
* Las referencias de los submódulos de Git se almacenan en las confirmaciones de Git específicas.
   * Como resultado, cuando se llevan a cabo cambios en el repositorio de submódulos, es necesario actualizar la confirmación a la que se hace referencia, por ejemplo, utilizando `git submodule update --remote`.
* A menos que sea necesario, se recomienda utilizar submódulos “superficiales”.
   * Para ello, ejecute `git config -f .gitmodules submodule.<submodule path>.shallow true` para cada submódulo.
