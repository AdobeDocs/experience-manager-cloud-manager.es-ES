---
title: Trabajar con varios repositorios Git de origen
description: 'Trabajar con varios repositorios Git de origen: Administrador de nube'
translation-type: tm+mt
source-git-commit: f5359dee907b32cefa2db2c4ad2baf8e337f6060
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 0%

---


# Trabajar con varios repositorios Git de origen {#working-with-multiple-source-git-repos}


## Sincronización de repositorios Git administrados por el cliente {#syncing-customer-managed-git-repositories}

En lugar de trabajar directamente con el repositorio Git de Cloud Manager, los clientes pueden trabajar con su propio repositorio Git o con varios repositorios Git propios. En estos casos, debe configurarse un proceso de sincronización automatizado para garantizar que el repositorio Git del Administrador de nube siempre se mantenga actualizado. Dependiendo de dónde esté alojado el repositorio Git del cliente, se podría utilizar una acción GitHub o una solución de integración continua como Jenkins para configurar la automatización. Con la automatización implementada, cada push a un repositorio Git propiedad del cliente se puede reenviar automáticamente al repositorio Git del Administrador de nube.

Aunque esta automatización para un único repositorio Git propiedad del cliente es directa, la configuración de varios repositorios requiere una configuración inicial. El contenido de los varios repositorios Git debe asignarse a diferentes directorios dentro del repositorio Git del administrador de nube único.  El repositorio Git de Cloud Manager debe aprovisionarse con un pom raíz Maven, enumerando los diferentes subproyectos en la sección de módulos

A continuación se muestra un ejemplo de dos repositorios Git de propiedad del cliente: el primer proyecto se colocará en el directorio denominado `project-a`, el segundo proyecto se colocará en el directorio denominado `project-b`.

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

Este tipo de pom raíz se inserta en una rama del repositorio Git del Administrador de nube. A continuación, los dos proyectos deben configurarse para reenviar automáticamente los cambios al repositorio Git del Administrador de nube.

Por ejemplo, una acción de GitHub se puede activar mediante una inserción en una rama del proyecto A. La acción retirará el proyecto A y el repositorio Git de Cloud Manager y copiará todo el contenido del proyecto A en el directorio `project-a` del repositorio Git de Cloud Manager y, a continuación, confirmará y insertará el cambio. Por ejemplo, un cambio en la rama principal del proyecto A se inserta automáticamente en la rama principal del repositorio git del Administrador de nube. Por supuesto, podría haber una asignación entre ramas, como una inserción en una rama denominada &quot;dev&quot; en el proyecto A se transfiere a una rama denominada &quot;desarrollo&quot; en el repositorio Git del Administrador de nubes. Se requieren pasos similares para el proyecto B.

Según la estrategia de ramificación y los flujos de trabajo, la sincronización puede configurarse para distintas ramas. Si el repositorio Git usado no proporciona un concepto similar a las acciones de GitHub, también es posible una integración a través de Jenkins (o similar). En este caso, un enlace web desencadena un trabajo de Jenkins que realiza el trabajo.

Siga los pasos a continuación para agregar un nuevo (tercer) origen o repositorio:

1. Añada una nueva acción de GitHub en el nuevo repositorio que transfiera los cambios de ese repositorio al repositorio Git de Cloud Manager.
1. Realice esa acción al menos una vez para asegurarse de que el código del proyecto se encuentra en el repositorio Git del Administrador de nube.
1. Añada una referencia al nuevo directorio en la página raíz Maven del repositorio Git del Administrador de nube.


## Ejemplo de acción de GitHub {#sample-github-action}

Se trata de una acción de ejemplo de GitHub desencadenada por una notificación push a la rama principal y luego introducida en un subdirectorio del repositorio Git del Administrador de nube. Las acciones de GitHub deben proporcionarse con dos secretos, `MAIN_USER` y `MAIN_PASSWORD`, para poder conectarse al repositorio Git del Administrador de nube y enviarlas al mismo.

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

Como se muestra arriba, el uso de una acción GitHub es muy flexible. Se puede realizar cualquier asignación entre ramas de los repositorios Git, así como cualquier asignación de los proyectos Git independientes en el diseño de directorio del proyecto principal.

>[!NOTE]
>La secuencia de comandos anterior utiliza `git add` para actualizar el repositorio, lo que supone que se incluyen eliminaciones, según la configuración predeterminada de Git, esto debe reemplazarse por `git add --all`.

## Ejemplo de trabajo de Jenkins {#sample-jenkins-job}

Este es un script de ejemplo que se puede utilizar en un trabajo de Jenkins o similar. Se activa por un cambio en un repositorio Git. El trabajo de Jenkins comprueba el estado más reciente de ese proyecto o ramificación y luego activa este script.

A su vez, este script extrae el repositorio Git del Administrador de nube y envía el código del proyecto a un subdirectorio.

El trabajo de Jenkins debe proporcionarse con dos secretos, `MAIN_USER` y `MAIN_PASSWORD`, para poder conectarse al repositorio Git de Cloud Manager y enviarlo al mismo.

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

Como se ha mostrado anteriormente, el uso de un trabajo de Jenkins es muy flexible. Se puede realizar cualquier asignación entre las ramas de los repositorios Git, así como cualquier asignación de los proyectos Git independientes en el diseño de directorio del proyecto principal.

>[!NOTE]
>La secuencia de comandos anterior utiliza `git add` para actualizar el repositorio, lo que supone que se incluyen eliminaciones, según la configuración predeterminada de Git, esto debe reemplazarse por `git add --all`.