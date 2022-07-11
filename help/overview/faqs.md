---
title: Preguntas frecuentes sobre Cloud Manager
description: Este documento proporciona respuestas a las preguntas más frecuentes sobre Cloud Manager para clientes de AMS.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 6be659e02df0657ec7d3dbce8c18c44a327a36f4
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 1%

---


# Preguntas frecuentes sobre Cloud Manager {#cloud-manager-faqs}

Este documento proporciona respuestas a las preguntas más frecuentes sobre Cloud Manager para clientes de AMS.

## ¿Es posible utilizar Java 11 con compilaciones de Cloud Manager? {#java-11}

Sí. Deberá agregar la variable `maven-toolchains-plugin` con la configuración correcta para Java 11.

* Este proceso está documentado [aquí.](/help/getting-started/using-the-wizard.md)
* Para ver un ejemplo, consulte la [código de proyecto de ejemplo wknd.](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75)

## Mi compilación falla con un error sobre maven-scr-plugin después de cambiar de Java 8 a Java 11. ¿Qué puedo hacer? {#maven-src-plugin}

Es posible que la compilación de AEM Cloud Manager falle al intentar cambiar la compilación de Java 8 a 11. Si encuentra el siguiente error, debe eliminar `maven-scr-plugin` y convertir todas las anotaciones OSGi en anotaciones OSGi R6.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Para obtener instrucciones sobre cómo eliminar este complemento, [consulte aquí.](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/)

## Mi compilación falla con un error sobre RequireJavaVersion después de cambiar de Java 8 a Java 11. ¿Qué puedo hacer? {#requirejavaversion}

Para las compilaciones de Cloud Manager, la variable `maven-enforcer-plugin` puede fallar con este error

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

Este es un problema conocido debido a que Cloud Manager utiliza una versión diferente de Java para ejecutar el comando maven en comparación con el código de compilación. Simplemente omita `requireJavaVersion` de su `maven-enforcer-plugin` configuraciones.

## La comprobación de calidad del código falló y nuestra implementación se atascó. ¿Hay alguna manera de evitar este cheque? {#deployment-stuck}

Sí. Todos los errores de calidad del código, excepto las clasificaciones de seguridad, son métricas no críticas, por lo que se pueden evitar como parte de una canalización de implementación ampliando los elementos en la interfaz de usuario de los resultados.

Un usuario con [Administrador de implementación, Administrador de proyectos o Propietario empresarial](/help/requirements/users-and-roles.md#role-definitions) puede anular los problemas, en cuyo caso la canalización continúa o pueden aceptar los problemas, en cuyo caso la canalización se detiene con un error.

Ver los documentos [Puerta de tres niveles mientras se ejecuta una canalización](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) y [Configuración de canalizaciones que no sean de producción](/help/using/non-production-pipelines.md#understanding-the-flow) para obtener más información.

## Las implementaciones de Cloud Manager fallan en el paso de prueba de rendimiento en los entornos de Adobe Managed Services. ¿Cómo depuramos esto para pasar las métricas críticas? {#debug-critical-metrics}

No hay una respuesta única a esta pregunta. Sin embargo, estos son algunos puntos importantes sobre el paso de la prueba de rendimiento que debe tener en cuenta:

* Este paso es un paso de rendimiento web, es decir, el tiempo para cargar la página mediante un explorador web.
* Las direcciones URL enumeradas en el archivo .csv resultante se cargan en un explorador Chrome en la infraestructura de Cloud Manager durante la prueba.
* Una métrica común que falla es la tasa de error.
   * Para que se pase una URL, la URL principal debe cargarse con `200` estado y en menor que `20` segundos.
   * Cargas de página superiores a `20` los segundos se marcan como `504` errores.
* Si el sitio requiere autenticación de usuarios, consulte el documento [Comprender los resultados de la prueba](/help/using/code-quality-testing.md#authenticated-performance-testing) para configurar la prueba para autenticarse en el sitio.

Consulte el documento [Comprender los resultados de la prueba](/help/using/code-quality-testing.md) para obtener más información sobre los controles de calidad.

## ¿Puedo utilizar SNAPSHOT para la versión del proyecto Maven? {#snapshot}

Sí. Para implementaciones de desarrolladores, la rama de Git `pom.xml` Los archivos deben contener `-SNAPSHOT` al final del `<version>` valor.

Esto permite que la implementación posterior se siga instalando cuando la versión no ha cambiado. En implementaciones de desarrolladores, no se agrega ni genera ninguna versión automática para la compilación de maven.

También puede establecer la versión en `-SNAPSHOT` para compilaciones o implementaciones de fase y producción. Cloud Manager establece automáticamente un número de versión adecuado y crea una etiqueta para usted en Git. Se puede hacer referencia a esta etiqueta más adelante, si es necesario.

Para obtener más información sobre la gestión de versiones, consulte [documentado aquí.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling.html)

## ¿Cómo funcionan las versiones de paquetes y paquetes para las implementaciones de ensayo y producción? {#staging-production}

En las implementaciones de ensayo y producción se genera una versión automática [como se documenta aquí.](/help/managing-code/maven-project-version.md)

Para las versiones personalizadas en las implementaciones de fase y producción, establezca una versión maven adecuada en tres partes como `1.0.0`. Actualice la versión cada vez que implemente en producción.

Cloud Manager añade automáticamente su versión a las compilaciones de fase y producción y crea una rama de Git. No se requiere ninguna configuración especial. Si no establece una versión maven como se describió anteriormente, la implementación se realizará correctamente y se establecerá una versión automáticamente.

## Mi compilación de maven falla en las implementaciones de Cloud Manager, pero se genera localmente sin errores. ¿Qué está mal? {#maven-build-fail}

Consulte esta [recurso de Git](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) para obtener más información.

## No puedo establecer una variable mediante un comando aio. ¿Qué puedo hacer? {#set-variable}

Puede recibir un error 403 como el siguiente cuando intenta enumerar o establecer variables de canalización a través de `aio` comandos.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

En este caso, el usuario que ejecuta estos comandos debe agregarse al **Administrador de implementación** en el Admin Console.

Consulte [Permisos de API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/) para obtener más información.
