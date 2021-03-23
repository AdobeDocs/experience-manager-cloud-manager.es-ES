---
title: Notas de la versión 2020.5.0
seo-title: Notas de la versión de AEM Cloud Manager para 2020.5.0
description: Siga esta página para obtener información sobre la versión 2020.5.0 de Cloud Manager.
seo-description: Siga esta página para obtener información sobre la versión 2020.5.0 de AEM Cloud Manager
feature: Información de la versión
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 67%

---

# Notas de la versión 2020.5.0 {#release-notes-for}

La siguiente sección describe las notas de la versión generales de la versión [!UICONTROL Cloud Manager] 2020.5.0.

## Fecha de la versión {#release-date}

La fecha de versión de la versión 2020.5.0 de [!UICONTROL Cloud Manager] es el 7 de mayo de 2020.

## Novedades {#whats-new}

* Se han agregado seis reglas de calidad de código adicionales para ayudar a los clientes a identificar posibles problemas al planificar una migración a Cloud Service,

* Se ha añadido una nueva métrica *Compatibilidad de Cloud Service* para resumir el número de problemas relacionados con la compatibilidad.

* Se ha mejorado el rendimiento de la página de Actividad y de la API de Lista de ejecuciones de canalización.

* El registro de calidad del código ahora contiene todos los seguimientos de pila para excepciones.

## Corrección de errores {#bug-fixes}

* Se mostraba una tarjeta engañosa en la página de información general mientras se ejecutaba la canalización de producción.

* La regla de calidad del código *DontImplementeOrExtendProviderTypesPomCheck* puede producir a veces una excepción de puntero nulo.

* Algunos vínculos de documentación de la página de información general no funcionaban correctamente.

* Algunas tarjetas de la página de información general no mostraban correctamente los nombres de entidades.

* Ciertas configuraciones de topología harían que el paso de prueba de rendimiento generara un error, en lugar de informar de las métricas que faltan.

