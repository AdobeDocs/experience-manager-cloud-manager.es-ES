---
title: Notas de la versión de 2019.10.0
seo-title: Notas de la versión de AEM Cloud Manager para 2019.10.0
description: Siga esta página para obtener información sobre la versión 2019.10.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2019.10.0 de AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 2028569406bcaacb27c42879a79832dec7ec91f4

---

# Notas de la versión de 2019.10.0 {#release-notes-for}

La siguiente sección describe las Notas de revisión generales de la versión 2019.10.0 y agrega actualizaciones a los pasos de implementación y al manejo de versiones del proyecto. [!UICONTROL Cloud Manager] 
Siga las secciones a continuación para obtener más detalles.

## Fecha de lanzamiento {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2019.10.0 es el 12 de octubre de 2019.

## Novedades {#whats-new}

* Se ha logrado un mayor rendimiento de porciones importantes de los pasos de implementación.
* Cuando proceda, la versión del proyecto de compilación Maven incorporará la versión del proyecto en git.
* En el momento de la creación, hay disponibles nuevas variables de entorno.
* Las tuberías que no son de producción se pueden eliminar de la tarjeta en la página **Información general** , así como en la API.
* Hay un nuevo paso de aprobación opcional inmediatamente después del paso de implementación de la etapa, pero antes del paso de prueba de seguridad.
* Al configurar una canalización CI/CD, la desvinculación y asociación de instancias de despachante del equilibrador de carga se puede omitir para entornos de desarrollo y de etapa.
Consulte Proceso **[de implementación](deploying-code.md#deployment-process)** para obtener más detalles.
* La CLI de Cloud Manager se ha ampliado para admitir el acceso a los registros de pasos de ejecución.
* La API de Cloud Manager ahora admite la edición de la rama configurada de un canalizador.
* Las solicitudes ejecutadas durante la prueba de rendimiento ahora incluyen un token ***CloudManagerTest*** específico en el agente de usuario.

## Corrección de errores {#bug-fixes}

* Algunas de las tarjetas de la página **Información general** no estaban correctamente alineadas verticalmente.
* Ciertas condiciones de fallo no hacían que las ejecuciones de los gasoductos se marcaran correctamente e impedían las ejecuciones posteriores.
