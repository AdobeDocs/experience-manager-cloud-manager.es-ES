---
source-git-commit: 4ff440250b4ed0770c34a7042ec7d22c79ffe05e
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---
# Fragmentos (#snippets)

## Problemas conocidos de la copia de contenido {#content-copy-known-issues}

Tenga en cuenta el siguiente problema conocido al usar la funcionalidad [copia de contenido.](/help/using/content-copy.md)

* Si se cambia el nombre de un recurso en el entorno de origen, puede provocar que la operación de copia de contenido falle debido a UUID en conflicto en el entorno de destino.
   * Para evitar este error, en lugar de cambiar el nombre de los recursos, primero elimínelos y vuelva a crearlos con el nuevo nombre de recurso que desee.
