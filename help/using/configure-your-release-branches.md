---
title: Configurar las ramas de lanzamiento
seo-title: Configurar las ramas de lanzamiento
description: Configure las ramas de lanzamiento en Git para AEM Cloud Manager
seo-description: Siga esta página para obtener información sobre cómo configurar las ramas de lanzamiento en git.
uuid: d 12 a 8 b 85-b 7 fd -4 b 55-a 05 a-a 0 f 874 ce 598 c
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introducción
discoiquuid: 53807 ea 6-9464-429 d -9322-85 c 9 f 405 dff 6
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Configurar las ramas de lanzamiento {#configure-your-release-branches}

## Configuración de su primera rama en Git {#setting-up-your-first-branch-in-git}

Un repositorio **de Git único y vacío se aprovisiona** para cada programa introducido en el Administrador de nube. Este repositorio puede contener tantas (o pocas) ramas como sigue el proceso de desarrollo, pero debe haber al menos una rama utilizada por el canal CI/CD para implementar el código de aplicación en el escenario y en la producción. La mejor opción es utilizar `master` como nombre de esta rama. Es cómodo, es el comportamiento predeterminado de los clientes Git al configurar nuevos proyectos.

Por ejemplo, al configurar un proyecto nuevo, ejecutará un conjunto de comandos como éste:

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
>No es necesario utilizar el cliente de la línea de comandos. Hay una variedad de clientes gráficos gráficos disponibles como aplicaciones independientes o como parte de un entorno de desarrollo integrado (IDE) como Eclipse o intellij. Siempre y cuando la aplicación cliente admita Git con HTTPS, debería ser compatible [!UICONTROL Cloud Manager]con.

## Insertar su primera rama {#pushing-your-first-branch}

Una vez que haya anidado al menos una revisión, puede agregar [!UICONTROL Cloud Manager] el repositorio como **remoto** y, a continuación, insertarlo en:

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
>La dirección URL específica, junto con sus credenciales, le será proporcionada por su ingeniero de éxito de cliente durante [!UICONTROL Cloud Manager] la integración.

## Ramas adicionales {#additional-branches}

Una `master` sola rama puede bastar para proyectos muy sencillos pero en la mayoría de los casos se requiere una estrategia de ramificación más compleja. Muchos clientes siguen un proceso donde las actividades de desarrollo diarias se realizan en una rama llamada `develop` y la rama de desarrollo se combina en `master` la rama cuando es hora de una implementación.

>[!NOTE]
>
>Para ver los comandos de git comunes, consulte la Hoja de consejos [de Git](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf).

