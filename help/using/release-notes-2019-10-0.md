---
title: Notas de la versión 2019.10.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.10.0
description: Siga esta página para obtener información sobre la versión 2019.10.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.10.0 de AEM Cloud Manager.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 5%

---

# Notas de la versión 2019.10.0 {#release-notes-for}

En la siguiente sección se describen las notas de la versión generales de [!UICONTROL Cloud Manager] versión 2019.10.0, y se añaden actualizaciones a los pasos de implementación y a la gestión de versiones del proyecto.
Siga las secciones a continuación para obtener más información.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2019.10.0 de [!UICONTROL Cloud Manager] es el 10 de octubre de 2019.

## Novedades {#whats-new}

* Se han hecho más eficientes partes importantes de los pasos de implementación.
* Cuando proceda, la versión del proyecto compilar Maven ahora incorporará la versión del proyecto en git.
* En el momento de la compilación, hay disponibles nuevas variables de entorno.
* Las canalizaciones que no sean de producción se pueden eliminar de la tarjeta en la página **Información general**, así como en la API.
* Hay un nuevo paso de aprobación opcional inmediatamente después del paso de implementación de la fase, pero antes del paso de prueba de seguridad.
* Al configurar una canalización CI/CD, la desconexión y la incorporación de instancias de Dispatcher desde el equilibrador de carga se puede omitir para entornos de desarrollo y ensayo.
Consulte **[Proceso de implementación](deploying-code.md#deployment-process)** para obtener más información.
* La CLI de Cloud Manager se ha ampliado para admitir el acceso a los registros de pasos de ejecución.
* La API de Cloud Manager ahora admite la edición de la rama configurada de una canalización.
* Las solicitudes ejecutadas durante la prueba de rendimiento ahora incluyen un token específico ***CloudManagerTest*** en el agente de usuario.

## Corrección de errores {#bug-fixes}

* Algunas de las tarjetas de la página **Información general** no estaban correctamente alineadas verticalmente.
* Algunas condiciones de fallo no hicieron que las ejecuciones de la canalización se marcaran correctamente e impidieron las ejecuciones posteriores.
