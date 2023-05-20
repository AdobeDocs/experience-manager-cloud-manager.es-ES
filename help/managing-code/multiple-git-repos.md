---
title: Uso de varios repositorios de Git
description: En lugar de trabajar directamente con el repositorio de Git de Cloud Manager, aprenda cómo puede trabajar con su propio repositorio de Git o con varios.
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a
source-git-commit: da9dff997a277c207e2c48207217cb30325f3c0d
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 100%

---

# Uso de repositorios Git de varias fuentes {#working-with-multiple-source-git-repos}

En lugar de trabajar directamente con el repositorio de Git de Cloud Manager, aprenda cómo puede trabajar con su propio repositorio de Git o con varios.

## Sincronización de repositorios de Git administrados por el cliente {#syncing-customer-managed-git-repositories}

Si quiere trabajar con su propio repositorio o repositorios, se debe configurar un proceso de sincronización automatizada para garantizar que el repositorio de Git de Cloud Manager siempre se mantenga actualizado.

Dependiendo de dónde esté alojado su repositorio de Git, podría aprovecharse una acción de GitHub o una solución de integración continua como Jenkins para configurar la automatización. Con una automatización activa, cada inserción en su propio repositorio se puede reenviar automáticamente al repositorio de Git de Cloud Manager.

Aunque esta automatización es sencilla para un único repositorio de Git propiedad del cliente, la configuración para varios requiere una preparación inicial más complicada. El contenido de varios repositorios de Git debe asignarse a distintos directorios dentro de un único repositorio de Git de Cloud Manager. El repositorio de Git de Cloud Manager debe aprovisionarse con un `pom.xml` de Maven raíz que enumere los diferentes subproyectos en la sección de módulos.

A continuación tiene un `pom.xml` de muestra para dos repositorios de Git propiedad del cliente. El primer proyecto se colocará en el directorio llamado `project-a` y el segundo, en `project-b`.

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

Un `pom.xml` raíz como este se inserta en una rama del repositorio de Git de Cloud Manager. A continuación, es necesario configurar los dos proyectos para que reenvíen automáticamente los cambios al repositorio de Git de Cloud Manager.

Por ejemplo, una acción de GitHub se puede activar por la inserción en una rama en el proyecto A. La acción comprobará el proyecto A y el repositorio de Git de Cloud Manager y copiará todo el contenido del proyecto A en el directorio `project-a` en el repositorio de Git de Cloud Manager. A continuación, confirmará la inserción del cambio.

Por ejemplo, un cambio en la rama `main` del proyecto A se inserta automáticamente en la rama `main` en el repositorio de Git de Cloud Manager. Por supuesto, podría haber una asignación entre ramas, como si una inserción en una rama llamada `dev` en el proyecto A se inserta una rama denominada `development` en el repositorio de Git de Cloud Manager. Se requieren pasos similares para el proyecto B.

Según la estrategia de ramificación y los flujos de trabajo, la sincronización se puede configurar para diferentes ramas. Si el repositorio de Git utilizado no proporciona un concepto similar a las acciones de GitHub, también es posible una integración a través de Jenkins (o similar). En este caso, un webhook activa el trabajo del que se encarga Jenkins.

Siga los pasos a continuación para añadir un nuevo (tercer) origen o repositorio:

1. Agregue una nueva acción de GitHub al nuevo repositorio que inserta cambios de ese repositorio en el repositorio de Git de Cloud Manager.
1. Realice esa acción al menos una vez para asegurarse de que el código del proyecto está en el repositorio de Git de Cloud Manager.
1. Agregue una referencia al nuevo directorio en la raíz de Maven `pom.xml` en el repositorio de Git de Cloud Manager.

## Muestra de acción de GitHub {#sample-github-action}

Esta es una acción de muestra de GitHub desencadenada por una inserción en la rama `main` y luego en un subdirectorio del repositorio de Git de Cloud Manager. Las acciones de GitHub deben tener dos secretos, `MAIN_USER` y `MAIN_PASSWORD`, para poder conectarse y enviar al repositorio de Git de Cloud Manager.

```java
name: SYNC
env:
  # Username/email used to commit to Cloud Manager's Git repository
  USER_NAME: <NAME>
  USER_EMAIL: <EMAIL>
  # Directory within the Cloud Manager Git repository
  PROJECT_DIR: project-a
  # Cloud Manager's Git repository
  MAIN_REPOSITORY: https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
  # The branch in Cloud Manager's Git repository to push to
  MAIN_BRANCH : <BRANCH_NAME>
 
# Only run on a push to this branch
on:
  push:
     branches: [ main ]
 
jobs:
  build:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout this project into a sub folder
      - uses: actions/checkout@v2
        with:
          path: sub
      # Cleanup sub project
      - name: Clean project
        run: |
          git -C sub log --format="%an : %s" -n 1 > commit.txt
          rm -rf sub/.git
          rm -rf sub/.github
      # Set global git configuration
      - name: Set git config
        run: |
          git config --global credential.helper cache
          git config --global user.email ${USER_EMAIL}
          git config --global user.name ${USER_NAME}
      # Checkout the main project
      - name: Checkout main project
        run:
          git clone -b ${MAIN_BRANCH} https://${{ secrets.PAT }}@github.com/${MAIN_REPOSITORY}.git main 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf main/${PROJECT_DIR} 
          mv sub main/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C main add -f ${PROJECT_DIR}
          git -C main commit -F ../commit.txt
          git -C main push
```

Como se muestra arriba, el uso de una acción de GitHub es muy flexible. Se puede ejecutar cualquier asignación entre ramas de los repositorios de Git, así como cualquier asignación de los proyectos de Git independientes al diseño de directorios del proyecto principal.

>[!NOTE]
>
>La secuencia de comandos anterior utiliza `git add` para actualizar el repositorio que supone que se incluyen las eliminaciones. Según la configuración predeterminada de Git, es posible que deba reemplazarse por `git add --all`.

## Ejemplo de trabajo de Jenkins {#sample-jenkins-job}

Esta es una secuencia de comandos de muestra que puede usarse en un trabajo de Jenkins o similar. Se activa mediante un cambio en un repositorio de Git. El trabajo de Jenkins comprueba el estado más reciente de ese proyecto o rama y luego activa esta secuencia de comandos.

A su vez, esta extrae el repositorio de Git de Cloud Manager y confirma el código del proyecto en un subdirectorio.

El trabajo de Jenkins debe tener dos secretos, `MAIN_USER` y `MAIN_PASSWORD`, para poder conectarse y enviar al repositorio de Git de Cloud Manager.

```java
# Username/email used to commit to Cloud Manager's Git repository
export USER_NAME=<NAME>
export USER_EMAIL=<EMAIL>
# Directory within the Cloud Manager Git repository
export PROJECT_DIR=project-a
# Cloud Manager's Git repository
export MAIN_REPOSITORY=https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
# The branch in Cloud Manager's Git repository to push to
export MAIN_BRANCH=<BRANCH_NAME>
 
# clean up and init
rm -rf target
mkdir target
 
# mv project to sub folder
mkdir target/sub
for f in .* *
do
    if [ "$f" != "." -a "$f" != ".." -a "$f" != "target" ]
    then
        mv "$f" target/sub
    fi
done
cd target
 
# capture log and remove git info
cd sub
git log --format="%an : %s" -n 1 > ../commit.txt
rm -rf .git
rm -rf .github
cd ..
 
# checkout main repository
git clone -b $MAIN_BRANCH $MAIN_REPOSITORY main
cd main
 
# configure main repository
git config credential.helper cache
git config user.email $USER_EMAIL
git config user.name $USER_NAME
 
# update project in main
rm -rf $PROJECT_DIR
mv ../sub $PROJECT_DIR
 
# commit changes to main
git add -f $PROJECT_DIR
git commit -F ../commit.txt
git push
```

Como se ha mostrado anteriormente, el uso de un trabajo de Jenkins es muy flexible. Se puede ejecutar cualquier asignación entre ramas de los repositorios de Git, así como cualquier asignación de los proyectos de Git independientes al diseño de directorios del proyecto principal.

>[!NOTE]
>
>La secuencia de comandos anterior emplea `git add` para actualizar el repositorio que supone que se incluyen las eliminaciones. Dependiendo de la configuración predeterminada de Git, es posible que haya que sustituirlo por `git add --all`.
