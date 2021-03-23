---
title: Preguntas frecuentes sobre Cloud Manager
seo-title: Preguntas frecuentes sobre Cloud Manager
description: Consulte las preguntas frecuentes de Cloud Manager para obtener algunas sugerencias para la resolución de problemas
seo-description: Siga esta página para obtener respuestas sobre las preguntas frecuentes de Cloud Manager
feature: Introducción
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 0%

---


# Preguntas frecuentes de Cloud Manager {#cloud-manager-faqs}

La siguiente sección proporciona respuestas a las preguntas más frecuentes relacionadas con Cloud Manager.

## ¿Es posible utilizar Java 11 con compilaciones de Cloud Manager? {#java-11-cloud-manager}

AEM compilación de Cloud Manager falla al intentar cambiar la compilación de Java 8 a 11. El problema puede tener muchas causas y las más comunes se documentan a continuación:

* Agregue el complemento toolchain con la configuración correcta para Java 11 como se documenta [aquí](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started).  Por ejemplo, consulte el [código de proyecto de muestra inteligente](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Si encuentra el siguiente error, debe eliminar el uso de `maven-scr-plugin` y convertir todas las anotaciones OSGi en anotaciones OSGi R6. Para obtener instrucciones, consulte [aquí](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Para las compilaciones de Cloud Manager, el complemento maven enforcer falla con el error `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. Este es un problema conocido debido a que Cloud Manager utiliza una versión diferente de Java para ejecutar el comando maven en comparación con el código de compilación. Por ahora, omita `requireJavaVersion` de las configuraciones de maven-enforcer-plugin.

## Nuestra implementación está atascada porque la comprobación de calidad del código falló. ¿Hay alguna manera de evitar este cheque? {#deployment-stuck}

Todos los errores de calidad del código excepto *Clasificación de seguridad* son métricas no críticas, por lo que se pueden evitar ampliando los elementos en la interfaz de usuario de los resultados.

Un usuario con la función [Deployment Manager, Project Manager o Business Owner](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) puede anular los problemas, en cuyo caso la canalización continúa o puede aceptar los problemas, en cuyo caso la canalización se detiene con un error.  Consulte [Puerta de tres niveles al ejecutar una canalización](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) para obtener más información.

## Las implementaciones de Cloud Manager fallan en el paso de prueba de rendimiento en los entornos de Adobe Managed Services. ¿Cómo depuramos esto para pasar las métricas críticas? {#debug-critical-metrics}

Consulte [Comprender los resultados de la prueba](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) para comprender los resultados.

Algunas notas sobre el paso Prueba de rendimiento :

* El *paso de rendimiento* es un paso de rendimiento web, es decir, el tiempo para cargar la página mediante un explorador web.
* Las direcciones URL enumeradas en el archivo *CSV* resultante se cargan en un explorador Chrome en la infraestructura de Cloud Manager durante la prueba.
* Una métrica común que falla es la *tasa de error*. Para que se pase una URL, la URL principal debe cargarse con estado `200` y en menos de `20` segundos. Las cargas de página que superen los `20` segundos se marcan como `504` errores.
* Si el sitio requiere autenticación de usuario, consulte [Pruebas de rendimiento autenticadas](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#how-to-use) para configurar la prueba para autenticarse en el sitio.

## ¿Se nos permite utilizar SNAPSHOT en la versión del proyecto Maven? ¿Cómo funciona el control de versiones de los paquetes y los archivos jar del paquete para las implementaciones de fase y producción? {#snapshot-version}

Consulte los siguientes escenarios para obtener más información sobre el control de versiones de los paquetes y los archivos jar de paquetes para las implementaciones de fase y producción:

1. Para implementaciones de desarrollador, los archivos de rama `pom.xml` de Git deben contener `-SNAPSHOT` al final del valor `<version>`. Esto permite una implementación posterior en la que la versión no cambia para instalarse. En implementaciones de desarrolladores, no se agrega ni genera ninguna versión automática para la compilación de maven.

1. En la implementación de fase y producción, se genera una versión automática como se documenta [aquí](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code).

1. Para las versiones personalizadas en las implementaciones de fase y producción, establezca una versión maven adecuada para 3 partes como `1.0.0`. Actualice la versión cada vez que tenga que realizar otra implementación en producción.

1. Cloud Manager añade automáticamente su versión a las compilaciones de Fase y Producción e incluso crea una rama Git. No se requiere ninguna configuración especial. Si se omite el paso 3 anterior, la implementación seguiría funcionando correctamente y se establecería una versión automáticamente.

1. No hay problemas, si deja la versión con `-SNAPSHOT` para compilaciones o implementaciones de fase y producción. Cloud Manager establece automáticamente un número de versión adecuado y crea una etiqueta para usted en Git. Se puede hacer referencia a esta etiqueta más adelante, si es necesario.

1. Si desea probar algún código experimental en el entorno de desarrollo, puede crear una nueva rama de Git y establecer la canalización para utilizar esa rama diferente. Esto resulta útil cuando las implementaciones comienzan a fallar y le gustaría probarlo con versiones anteriores del código para ver cuándo se interrumpió.

   El comando Git de abajo crea una rama remota denominada *testbranch1* frente a una confirmación preexistente específica `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Esta rama especial se puede usar en Cloud Manager sin afectar a otras ramas:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Consulte la [documentación de Git](https://git-scm.com/book/en/v2/Git-Internals-Git-References) para obtener más información.

   Si desea eliminar la rama de prueba más adelante, utilice el comando eliminar:

   `git push origin --delete testbranch1`

## La compilación de Maven falla en las implementaciones de Cloud Manager, pero se genera localmente sin errores. ¿Cómo se depura? {#maven-build-fail}

Consulte [Recurso de Git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) para obtener más información.

## No se puede establecer una variable a través de las variables de canalización establecidas de aio cloud manager. ¿Cómo depurar estos problemas? {#set-variable}

Si se produce un error `403` al intentar enumerar o establecer variables de canalización mediante comandos similares a los que se indican a continuación, debe agregarse como función de producto *Deployment Manager* Cloud Manager en el Admin Console.\
Consulte [Permisos de API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) para obtener más información.

Comandos y errores relacionados:

`$ aio cloudmanager:list-pipeline-variables 222`

*Error*:  `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Error*:  `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
