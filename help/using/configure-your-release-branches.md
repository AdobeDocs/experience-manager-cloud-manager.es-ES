---
title: Configurar las ramas de las versiones
seo-title: Configurar las ramas de las versiones
description: Configuración de ramas de la versión en Git para AEM Cloud Manager
seo-description: Siga esta página para obtener información sobre cómo configurar las ramas de lanzamiento en git.
uuid: d12a8b85-b7fd-4b55-a05a-a0f874ce598c
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 53807ea6-9464-429d-9322-85c9f405dff6
feature: Git Repositories
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 3%

---


# Configurar las ramas de las versiones {#configure-your-release-branches}

## Configuración de la primera rama en Git {#setting-up-your-first-branch-in-git}

Para cada programa incorporado en Cloud Manager, se aprovisiona un único **Repositorio Git** inicialmente vacío. Este repositorio puede contener tantas ramas (o tan pocas) como sigue el proceso de desarrollo, pero debe haber al menos una rama que utilice la canalización CI/CD para implementar el código de aplicación en las fases y la producción. Se recomienda utilizar `master` como nombre de esta rama. Convenientemente, este es el comportamiento predeterminado de los clientes de Git al configurar nuevos proyectos.

Por ejemplo, al configurar un nuevo proyecto, se ejecutará un conjunto de comandos como este:

```shell
$ git init
Initialized empty Git repository in /Users/myname/workspace/new-project/.git/
... steps which add Maven build files and source code ...
$ git add pom.xml core/pom.xml core/src ui.apps/pom.xml ui.apps/src
$ git commit -m "initial commit"
 19 files changed, 777 insertions(+)
 create mode 100644 core/pom.xml
 create mode 100644 pom.xml
 create mode 100644 ui.apps/pom.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/config.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/definition/.content.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/filter.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/nodetypes.cnd
 create mode 100644 ui.apps/src/main/content/META-INF/vault/properties.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/apps/my-aem-project/install/.vltignore
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/_rep_policy.xml
```

>[!NOTE]
>
>No es un requisito utilizar el cliente de línea de comandos. Hay una variedad de clientes Git gráficos disponibles como aplicaciones independientes o como parte de un Entorno de desarrollo integrado (IDE) como Eclipse o IntelliJ. Siempre que la aplicación cliente admita el Git utilizando HTTPS, debería ser compatible con [!UICONTROL Cloud Manager].

## Inserción de la primera rama {#pushing-your-first-branch}

Una vez que haya realizado al menos una revisión, puede agregar el repositorio [!UICONTROL Cloud Manager] como **remoto** y luego insertar las confirmaciones en él:

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      master -> master
```

>[!NOTE]
>
>La dirección URL específica, junto con sus credenciales, la proporcionará su ingeniero de éxito del cliente durante la [!UICONTROL Cloud Manager] incorporación.

## Ramas adicionales {#additional-branches}

Una sola rama `master` puede ser suficiente para proyectos muy simples, pero en la mayoría de los casos se necesitará una estrategia de ramificación más compleja. Muchos clientes siguen un proceso en el que las actividades de desarrollo cotidianas se realizan en una rama denominada `develop` y la rama de desarrollo se fusiona en la rama `master` cuando es el momento de una implementación.

>[!NOTE]
>
>Para ver los comandos comunes de git, consulte la [Hoja de referencia de Git](https://github.github.com/training-kit/downloads/github-git-cheat-sheet).
