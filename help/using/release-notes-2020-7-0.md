---
title: Notas de la versión 2020.7.0
seo-title: Notas de la versión de AEM Cloud Manager para 2020.7.0
description: Siga esta página para obtener información sobre la versión 2020.7.0 de Cloud Manager
seo-description: Siga esta página para obtener información sobre la versión 2020.7.0 de AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 3be958aa21d5423ddf371c286825d01afd554c4b
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 51%

---

# Notas de la versión 2020.7.0 {#release-notes-for}

En la siguiente sección se describen las Notas de revisión generales de la versión 2020.7.0 [!UICONTROL Cloud Manager] .

## Fecha de la versión {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.7.0 is July 09, 2020.

## Novedades {#whats-new}

* La desvinculación y la asociación de instancias de despachante de los equilibradores de carga durante las implementaciones de producción ahora funcionan de forma más coherente.

* El contenedor de generación de Cloud Manager ahora admite Java 8 y Java 11.

* Las canalizaciones de Cloud Manager ahora admiten las variables y los secretos establecidos por el cliente.
Consulte [Variables de canalización](/help/using/create-an-application-project.md#pipeline-variables) para obtener más detalles.

## Corrección de errores {#bug-fixes}

* The **Cancel** and **Save** options on the Non-Production Pipeline Edit page were not always visible.

* Ciertos errores en el proceso de calidad del código podrían ocasionar que el archivo de registro no se genere correctamente.

* Algunos registros de pasos de canalización de gran tamaño no se podían descargar de forma consistente a través de la interfaz de usuario.

## Problemas conocidos {#known-issues}

* Cuando un entorno de AMS contiene una instancia de espera, el mensaje registrado indica que la instancia está inactiva en lugar de estar en modo de espera.

* Debido a un cambio en la forma de calcular la cobertura del código, la versión _mínima_ del complemento Jacoco es ahora 0.7.5.201505241946 (publicada en mayo de 2015). Los clientes que hagan referencia explícita a una versión anterior recibirán un mensaje de error en el proceso de calidad del código.
