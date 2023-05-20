---
title: Configuración de ramas
description: Obtenga información sobre cómo configurar su primera rama en Git y cómo la canalización CI/CD la usa para implementar el código de la aplicación.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 4c051cd1696f8a00d0278131c9521ad4dcb956a3
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 100%

---


# Configuración de ramas {#configuring-branches}

Obtenga información sobre cómo configurar su primera rama en Git y cómo la canalización CI/CD la usa para implementar el código de la aplicación.

## Configuración de la primera rama en Git {#setting-up-your-first-branch-in-git}

Un único repositorio de Git, inicialmente vacío, [se aprovisiona](/help/requirements/environment-provisioning.md) para cada programa incorporado en Cloud Manager. Este repositorio puede contener tantas ramas como requiera el proceso de desarrollo, pero debe haber al menos una que utilice la canalización CI/CD para implementar el código de la aplicación en ensayo y producción. Una práctica recomendada es utilizar `main` como el nombre de esta rama. De manera práctica, este es el comportamiento por defecto de los clientes de Git cuando se configuran nuevos proyectos.

Por ejemplo, al hacerlo, se ejecutará un conjunto de comandos similar al siguiente.

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
>No es un requisito emplear el cliente de línea de comandos. Hay una variedad de clientes de Git gráficos disponibles como aplicaciones independientes o como parte de un entorno de desarrollo integrado (IDE) como Eclipse o IntelliJ. Siempre que la aplicación cliente admita Git utilizando HTTPS, debería ser compatible con [!UICONTROL Cloud Manager].

## Inserción de la primera rama {#pushing-your-first-branch}

Una vez que haya confirmado al menos una revisión, puede añadir el repositorio de [!UICONTROL Cloud Manager] como remoto y luego insertar sus confirmaciones en él.

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      main -> main
```

>[!NOTE]
>
>La dirección URL específica, junto con sus credenciales, la proporcionará su ingeniero de éxito del cliente durante la incorporación a [!UICONTROL Cloud Manager].

## Ramas adicionales {#additional-branches}

Una sola rama `main` puede ser suficiente para proyectos muy sencillos, pero en la mayoría de los casos se necesitará una estrategia de ramificación más compleja. Muchos clientes siguen un proceso en el que las actividades de desarrollo cotidianas se ejecutan en una rama denominada `develop`. La rama de desarrollo se fusiona con la rama `main` en el momento de una implementación.

>[!TIP]
>
>Para ver los comandos de Git comunes, consulte la [Hoja de características clave de Git](https://github.github.com/training-kit/downloads/github-git-cheat-sheet).
