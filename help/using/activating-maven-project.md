---
title: Administración de versiones del proyecto de Maven
seo-title: Administración de versiones del proyecto de Maven
description: Obtenga más información sobre la administración de versiones del proyecto de Maven.
seo-description: Siga esta página para obtener más información sobre la administración de versiones del proyecto de Maven
translation-type: tm+mt
source-git-commit: 519f43ff16e0474951f97798a8e070141e5c124b

---


# Administración de versiones del proyecto de Maven {#project-version}

## Explicación de la administración de versiones del proyecto de Maven {#understanding-project-version}

Para implementaciones de fase y producción, Cloud Manager genera una versión única e incremental.

Esta versión se ve en la página de detalles de la ejecución de la canalización, así como en la página de actividades. Cuando se ejecuta una compilación, el proyecto Maven se actualiza para utilizar esta versión y se crea una etiqueta en el repositorio git con esa versión como nombre.

Si la versión original del proyecto cumple ciertos criterios, la versión actualizada del proyecto de Maven combinará la versión original del proyecto y la versión generada por Cloud Manager. Sin embargo, la etiqueta siempre utiliza la versión generada. Para que se produzca esta combinación, la versión original del proyecto debe estar formada con exactamente tres segmentos de versión, por ejemplo, 1.0.0 o 1.2.3, pero no 1.0 ni 1, y la versión original no debe terminar en -SNAPSHOT.

Si la versión original cumple estos criterios, la versión generada se agregará a la versión original como un segmento de nueva versión. La versión generada también se modificará ligeramente para incluir la correcta ordenación y gestión de versiones. Por ejemplo, suponiendo una versión generada de 2019.926.121356.0000020490:

| **Versión** | **versión en pom.xml** | **Comentario** |
|---|---|---|
| 1.0.0 | 1.0.0.2019_0926_121356_0000020490 | Versión original correctamente formada |
| 1.0.0-SNAPSHOT | 2019.926.121356.0000020490 | Versión de instantánea, sobrescrita |
| 1 | 2019.926.121356.0000020490 | Versión incompleta, sobrescrita |

>[!NOTE]
>
>Independientemente de si la versión original se incorporó o no a la versión inicializada por el Administrador de nube, la versión original está disponible como propiedad Maven con el nombre *cloudManagerOriginalVersion*.
