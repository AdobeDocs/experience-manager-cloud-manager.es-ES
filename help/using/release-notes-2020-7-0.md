---
title: Notas de la versión 2020.7.0
seo-title: Notas de la versión de AEM Cloud Manager para 2020.7.0
description: Siga esta página para obtener información sobre la versión 2020.7.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2020.7.0 de AEM Cloud Manager
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 52%

---

# Notas de la versión 2020.7.0 {#release-notes-for}

La siguiente sección describe las notas de la versión generales de la versión [!UICONTROL Cloud Manager] 2020.7.0.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2020.7.0 de [!UICONTROL Cloud Manager] es el 9 de julio de 2020.

## Novedades {#whats-new}

* La desconexión y la adjuntación de instancias de Dispatcher de los equilibradores de carga durante las implementaciones de producción ahora funcionan de forma más coherente.

* El contenedor de generación de Cloud Manager ahora admite Java 8 y Java 11.

* Las canalizaciones de Cloud Manager ahora admiten las variables y los secretos establecidos por el cliente.
Consulte [Variables de canalización](/help/using/build-environment-details.md#pipeline-variables) para obtener más detalles.

## Corrección de errores {#bug-fixes}

* Las opciones **Cancel** y **Save** de la página de edición de la canalización que no es de producción no siempre estaban visibles.

* Ciertos errores en el proceso de calidad del código podrían ocasionar que el archivo de registro no se genere correctamente.

* Algunos registros de pasos de canalización de gran tamaño no se podían descargar de forma consistente a través de la interfaz de usuario.

## Problemas conocidos {#known-issues}

* Cuando un entorno de AMS contiene una instancia de espera, el mensaje registrado indica que la instancia está desactivada, en lugar de estar en modo de espera.

* Debido a un cambio en la forma de calcular la cobertura del código, la versión _mínima_ del complemento Jacoco es ahora 0.7.5.201505241946 (publicada en mayo de 2015). Los clientes que hagan referencia explícita a una versión anterior recibirán un mensaje de error en el proceso de calidad del código.
