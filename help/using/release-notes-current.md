---
title: Notas de la versión 2020.7.0
seo-title: Notas de la versión de AEM Cloud Manager para 2020.7.0
description: Siga esta página para obtener información sobre la versión 2020.7.0 de Cloud Manager
seo-description: Siga esta página para obtener información sobre la versión 2020.7.0 de AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 02515ac6e3ac54909e23a276a78f571ea5c249c4
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 8%

---

# Notas de la versión 2020.7.0 {#release-notes-for}

En la siguiente sección se describen las Notas de revisión generales de la versión 2020.7.0 [!UICONTROL Cloud Manager] .

## Fecha de la versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2020.7.0 es el 9 de julio de 2020.

## Novedades {#whats-new}

* La desvinculación y la asociación de instancias de despachante de los equilibradores de carga durante las implementaciones de producción ahora funcionan de forma más coherente.

* El contenedor de compilación de Cloud Manager ahora admite Java 8 y Java 11.

* Las canalizaciones de Cloud Manager ahora admiten las variables y los secretos establecidos por el cliente. Consulte [Variables](/help/using/create-an-application-project.md#pipeline-variables) de canalización para obtener más detalles.

## Corrección de errores {#bug-fixes}

* Las opciones **Cancelar** y **Guardar** de la página Editar tubería no de producción no siempre estaban visibles.

* Ciertos errores en el proceso de calidad del código podrían ocasionar que el archivo de registro no se genere correctamente.

* Algunos registros de pasos de canalización de gran tamaño no se podían descargar de forma consistente a través de la interfaz de usuario.

## Problemas conocidos {#known-issues}

* Cuando un entorno de AMS contiene una instancia de espera, el mensaje registrado indica que la instancia está inactiva en lugar de estar en modo de espera.
