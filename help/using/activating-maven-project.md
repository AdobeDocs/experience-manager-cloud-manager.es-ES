---
title: Administrar versiones del proyecto de Maven
seo-title: Administrar versiones del proyecto de Maven
description: Obtenga más información sobre Maven Project Version Handling.
seo-description: Siga esta página para obtener más información sobre Maven Project Version Handling.
feature: Introducción
exl-id: a1d676e0-27cc-4b0d-8799-527c0520946a
source-git-commit: aa2d7cb3d0fa3d6038d364659ce8d5eacb6825c5
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 7%

---

# Administrar versiones del proyecto de Maven {#project-version}

## Explicación de la administración de versiones del proyecto de Maven {#understanding-project-version}

Para implementaciones de fase y producción, Cloud Manager genera una versión única e incremental.

Esta versión se ve en la página de detalles de ejecución de la canalización, así como en la página de actividad. Cuando se ejecuta una compilación, el proyecto Maven se actualiza para utilizar esta versión y se crea una etiqueta en el repositorio de Git con esa versión como su nombre.

Si la versión original del proyecto cumple ciertos criterios, la versión actualizada del proyecto Maven combinará la versión original del proyecto y la versión generada por Cloud Manager. Sin embargo, la etiqueta siempre utiliza la versión generada. Para que se produzca esta combinación, la versión original del proyecto debe formarse con exactamente tres segmentos de versión, por ejemplo, 1.0.0 o 1.2.3, pero no 1.0 o 1, y la versión original no debe finalizar en -SNAPSHOT.

>[!NOTE]
>Este valor de versión del proyecto original debe configurarse estáticamente en el elemento `<version>` del archivo `pom.xml` de nivel superior en la rama del repositorio de Git.

Si la versión original cumple estos criterios, la versión generada se añadirá a la versión original como segmento de nueva versión. La versión generada también se modificará ligeramente para incluir la ordenación y el control de versiones adecuados. Por ejemplo, suponiendo una versión generada de 2019.926.121356.0000020490:

| **Versión** | **versión en pom.xml** | **Comentario** |
|---|---|---|
| 1.0.0 | 1.0.0.2019_0926_121356_0000020490 | Versión original correctamente formada |
| 1.0.0: INSTANTÁNEA | 2019,926,121356,0000020490 | Versión de instantánea, sobrescrita |
| 1 | 2019,926,121356,0000020490 | Versión incompleta, sobrescrita |

>[!NOTE]
>
>Independientemente de si la versión original se incorporó o no a la versión inicializada por Cloud Manager, la versión original está disponible como propiedad Maven con el nombre *cloudManagerOriginalVersion.*
