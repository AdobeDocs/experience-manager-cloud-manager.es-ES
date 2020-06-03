---
title: Notas de la versión 2020.5.0
seo-title: Notas de la versión de AEM Cloud Manager para 2020.5.0
description: Siga esta página para obtener información sobre la versión 2020.5.0 de Cloud Manager
seo-description: Siga esta página para obtener información sobre la versión 2020.5.0 de AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 0652436ec0c1c95d270a06a600424dbfd0140b27
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 66%

---

# Notas de la versión 2020.5.0 {#release-notes-for}

La siguiente sección describe las Notas de revisión generales de la versión 2020.5.0 [!UICONTROL Cloud Manager] .

## Fecha de la versión {#release-date}

La fecha de versión de [!UICONTROL Cloud Manager] la versión 2020.5.0 es el 7 de mayo de 2020.

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

* Determinadas configuraciones de topología harían que el paso de la prueba de rendimiento generara un error, en lugar de sistema de informes de las métricas que faltan.

