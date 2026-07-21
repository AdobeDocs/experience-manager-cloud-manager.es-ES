---
title: Preguntas frecuentes sobre Cloud Manager
description: Conozca las respuestas a las preguntas más frecuentes acerca de Cloud Manager para clientes de AMS.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
TQID: https://experienceleague.adobe.com/aBIiazPCm-krE6rew6k-HSl-Uvc79eagMzM7uYciWdc
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 4dcc367f82c51626ca449ff389a9c9574a562ff7
workflow-type: tm+mt
source-wordcount: 764
ht-degree: 69%

---

# Preguntas frecuentes sobre Cloud Manager {#cloud-manager-faqs}

Este documento proporciona respuestas a las preguntas más frecuentes acerca de Cloud Manager para clientes de AMS.

<!-- 
## Is it possible to use Java 11 with Cloud Manager builds? {#java-11}

Yes. You need to add the `maven-toolchains-plugin` with the correct settings for Java 11.

* This process is documented [here](/help/getting-started/using-the-wizard.md).
* For an example, see the [WKND sample project code](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75). 
-->

## Mi generación falla con un error sobre maven-scr-plugin después de cambiar de Java 8 a Java 11. ¿Qué puedo hacer? {#maven-src-plugin}

La compilación de AEM Cloud Manager falla al intentar cambiar de Java 8 a Java 11. Si encuentra el siguiente error, debe eliminar `maven-scr-plugin` y convertir todas las anotaciones OSGi a anotaciones OSGi R6.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Para obtener instrucciones sobre cómo quitar este complemento, haga clic [aquí](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/).

## Mi generación falla con un error sobre RequireJavaVersion después de cambiar de Java 8 a Java 11. ¿Qué puedo hacer? {#requirejavaversion}

Para las generaciones de Cloud Manager, el `maven-enforcer-plugin` puede fallar con este error.

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

Este problema se produce porque Cloud Manager utiliza una versión diferente de Java para ejecutar el comando Maven. Esta versión es diferente de la utilizada para compilar código. Omita `requireJavaVersion` de su configuraciones de `maven-enforcer-plugin`.

## Error en la comprobación de calidad del código y ahora se detiene la implementación. ¿Hay alguna manera de saltarse esta comprobación? {#deployment-stuck}

Sí. Todos los errores de calidad del código, excepto las clasificaciones de seguridad, son métricas no críticas. Como tal, se pueden evitar como parte de una canalización de implementación expandiendo los elementos en la interfaz de usuario de los resultados.

Un usuario con la función [Administrador de implementación, Administrador de proyectos o Propietario empresarial](/help/requirements/users-and-roles.md#role-definitions) puede anular los problemas. En tal caso, la canalización continúa. O bien, pueden aceptar los problemas, en cuyo caso la canalización se detiene con un error.

Vea los documentos [Puertas de tres niveles al ejecutar una canalización](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) y [Configuración de canalizaciones que no son de producción](/help/using/non-production-pipelines.md#understanding-the-flow) para obtener más información.

## Las implementaciones de Cloud Manager fallan en el paso de prueba de rendimiento en los entornos de Adobe Managed Services. ¿Cómo se puede resolver este problema para pasar las métricas esenciales? {#debug-critical-metrics}

No existe una respuesta única y definitiva a esta pregunta. Sin embargo, los siguientes puntos sobre el paso de la prueba de rendimiento son útiles:

* Este paso es de rendimiento web. Es decir, es aproximadamente el tiempo que se tarda en cargar una página en un explorador web.
* Las direcciones URL enumeradas en el archivo .csv resultante se cargan en un explorador Chrome dentro de la infraestructura de Cloud Manager durante la prueba.
* Una métrica común que falla es la tasa de error. Para que una URL supere la prueba, la URL principal debe cargarse con el estado `200` y en menos de `20` segundos. Si la carga de una página supera los `20` segundos, se marca como un error `504`.
* Si el sitio requiere autenticación de usuario, consulte el documento [Comprensión de los resultados de la prueba](/help/using/code-quality-testing.md#authenticated-performance-testing) para configurar la prueba para autenticarse en el sitio.

Consulte el documento [Comprensión de los resultados de la prueba](/help/using/code-quality-testing.md) para obtener más información sobre los controles de calidad.

## ¿Puedo utilizar SNAPSHOT para la versión del proyecto de Maven? {#snapshot}

Sí. Para implementaciones de desarrolladores, los archivos de la rama de Git `pom.xml` deben contener `-SNAPSHOT` al final del valor `<version>`.

Al hacerlo, las implementaciones posteriores se instalan cuando la versión no ha cambiado. En implementaciones de desarrolladores, no se agrega ni genera ninguna versión automática para la compilación de Maven.

También puede establecer la versión a `-SNAPSHOT` para generaciones o implementaciones de fase y producción. Cloud Manager establece automáticamente un número de versión adecuado y crea una etiqueta para usted en Git. Se puede hacer referencia a esta etiqueta más adelante, si es necesario.

Para obtener más información sobre la administración de versiones, consulte [estos documentos](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling).

## ¿Cómo funcionan las versiones de paquetes y los paquetes para las implementaciones de ensayo y producción? {#staging-production}

En las implementaciones de ensayo y producción se genera una versión automática [como se documenta aquí](/help/managing-code/maven-project-version.md).

Para las versiones personalizadas en las implementaciones de fase y producción, establezca una versión de Maven adecuada en tres partes, como `1.0.0`. Actualice la versión cada vez que implemente en la producción.

Cloud Manager añade automáticamente su versión a las compilaciones de ensayo y producción y crea una rama de Git. No se requiere ninguna configuración especial. Si no establece una versión de Maven como se describió anteriormente, la implementación se realiza correctamente y se establece una versión automáticamente.

## Mi generación de Maven falla en las implementaciones de Cloud Manager, pero se genera localmente sin errores. ¿Cuál es la causa? {#maven-build-fail}

Consulte este [recurso de Git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) para obtener más información.

## No puedo establecer una variable mediante un comando aio. ¿Qué puedo hacer? {#set-variable}

Recibirá un error 403 como el siguiente cuando intente enumerar o establecer variables de canalización mediante `aio` comandos.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

En este caso, el usuario que ejecuta estos comandos debe añadirse a la función **Administrador de implementación** en Admin Console.

Consulte [Permisos de la API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions) para obtener más información.
