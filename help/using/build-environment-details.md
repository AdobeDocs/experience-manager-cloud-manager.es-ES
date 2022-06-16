---
title: Explicación del entorno de compilación
description: Siga esta página para obtener más información sobre los entornos
feature: Environments
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: 9959f649e553d0ff6d41a70a468bec3e2e854d75
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 1%

---

# Explicación del entorno de compilación {#build-environment-details}

Cloud Manager crea y prueba su código mediante un entorno de compilación especializado. Este entorno tiene los siguientes atributos:

* El entorno de compilación está basado en Linux, derivado de Ubuntu 18.04.
* Apache Maven 3.6.0 está instalado.
* Las versiones de Java instaladas son Oracle JDK 8u202, Azul Zulu 8u292, Oracle JDK 11.0.2 y Azul Zulu 11.0.11.
* De forma predeterminada, la variable de entorno JAVA_HOME está configurada en `/usr/lib/jvm/jdk1.8.0_202` que contiene el Oracle JDK 8u202. Consulte [Versión JDK de ejecución de Maven alternativa](#alternate-maven) para obtener más información.
* Hay algunos paquetes de sistema adicionales instalados que son necesarios:

   * bzip2
   * descomprimir
   * libpng
   * imagemagick
   * graphicsmagick

* Se pueden instalar otros paquetes en el momento de la compilación, tal como se describe [below](#installing-additional-system-packages).
* Cada construcción se realiza en un entorno prístino; el contenedor de compilación no mantiene ningún estado entre ejecuciones.
* Maven siempre se ejecuta con estos tres comandos:

   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`

* Maven se configura a nivel del sistema con un archivo settings.xml que incluye automáticamente el Adobe público **Artefacto** repositorio que utiliza un perfil denominado `adobe-public`.
Consulte [Repositorio Maven Público de Adobe](https://repo1.maven.org/) para obtener más información.

>[!NOTE]
>Aunque Cloud Manager no define una versión específica de la variable `jacoco-maven-plugin`, la versión utilizada debe ser al menos `0.7.5.201505241946`.


>[!NOTE]
>Consulte los siguientes recursos adicionales para aprender a utilizar las API de Cloud Manager:
> * [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Creación de una integración de API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/create-api-integration.md)
>* [Permisos de API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md)


## Uso de una versión de Java específica {#using-java-version}

De forma predeterminada, los proyectos se crean mediante el proceso de compilación de Cloud Manager con el JDK de Oracle 8. Los clientes que deseen utilizar un JDK alternativo tienen dos opciones: Maven Toolchain y seleccionar una versión JDK alternativa para todo el proceso de ejecución de Maven.

### Cadenas de herramientas de Maven {#maven-toolchains}

La variable [Complemento Maven Toolchain](https://maven.apache.org/plugins/maven-toolchains-plugin/) permite que los proyectos seleccionen un JDK específico (o *toolchain*) que se utilizará en el contexto de los complementos Maven con conocimiento de herramientas. Esto se hace en el `pom.xml` especificando un valor de proveedor y de versión. Una sección de muestra de la sección `pom.xml` es:

```xml
        <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-toolchains-plugin</artifactId>
    <version>1.1</version>
    <executions>
        <execution>
            <goals>
                <goal>toolchain</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <toolchains>
            <jdk>
                <version>11</version>
                <vendor>oracle</vendor>
            </jdk>
        </toolchains>
    </configuration>
</plugin>
```

Esto hará que todos los plugins Maven con conocimiento de herramientas utilicen el Oracle JDK, versión 11.

Al utilizar este método, el propio Maven sigue ejecutándose utilizando el JDK predeterminado (Oracle 8) y el `JAVA_HOME` no cambia. Por lo tanto, compruebe o aplique la versión de Java a través de complementos como el [Complemento Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) no funciona y estos complementos no deben usarse.

Las combinaciones de proveedor/versión disponibles actualmente son:

* oracle 1.8
* oracle 1.11
* oracle 11
* sun 1.8
* sun 1.11
* sol 11
* azul 1.8
* azul 1.11
* azul 8

### Versión JDK de ejecución de Maven alternativa {#alternate-maven}

También es posible seleccionar Azul 8 o Azul 11 como JDK para toda la ejecución de Maven. A diferencia de las opciones de toolchain, esto cambia el JDK utilizado para todos los plugins a menos que también se establezca la configuración de toolchain en cuyo caso la configuración de toolchain se sigue aplicando a los plugins Maven según las cadenas de herramientas. Como resultado, comprobar y aplicar la versión de Java utilizando la variable [Complemento Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) funcionará.

Para ello, cree un archivo con el nombre `.cloudmanager/java-version` en la rama del repositorio de git utilizada por la canalización. Este archivo puede tener el contenido 11 u 8. Se ignora cualquier otro valor. Si se especifica 11, se usa Azul 11 y la variable de entorno JAVA_HOME está configurada como `/usr/lib/jvm/jdk-11.0.11`. Si se especifica 8, se usa Azul 8 y la variable de entorno JAVA_HOME está configurada en `/usr/lib/jvm/jdk-8.0.292`.

## Variables de entorno {#environment-variables}

### Variables de entorno estándar {#standard-environ-variables}

En algunos casos, los clientes consideran necesario variar el proceso de compilación en función de la información sobre el programa o la canalización.

Por ejemplo, si se está realizando la minimización de JavaScript en tiempo de compilación, a través de una herramienta como gulp, puede haber un deseo de utilizar un nivel de minificación diferente al crear para un entorno de desarrollo, en lugar de construir para fase y producción.

Para admitir esto, Cloud Manager agrega estas variables de entorno estándar al contenedor de compilación para cada ejecución.

| **Nombre de la variable** | **Definición** |
|---|---|
| CM_BUILD | Siempre se configura como &quot;true&quot; |
| RAMA | La rama configurada para la ejecución |
| CM_PIPELINE_ID | El identificador numérico de la canalización |
| CM_PIPELINE_NAME | El nombre de la canalización |
| CM_PROGRAM_ID | Identificador numérico del programa |
| CM_PROGRAM_NAME | El nombre del programa |
| ARTIFACTS_VERSION | Para una fase o canalización de producción, la versión sintética generada por Cloud Manager |

### Variables de canalización {#pipeline-variables}

En algunos casos, el proceso de compilación de un cliente puede depender de variables de configuración específicas que no deberían colocarse en el repositorio de Git o deberían variar entre las ejecuciones de canalización que utilizan la misma rama.

Cloud Manager permite que estas variables se configuren mediante la API de Cloud Manager o la CLI de Cloud Manager por canalización. Las variables pueden almacenarse como texto sin formato o cifrarse en reposo. En cualquier caso, las variables están disponibles dentro del entorno de compilación como una variable de entorno a la que se puede hacer referencia desde dentro del `pom.xml` archivo u otras secuencias de comandos de compilación.

Para configurar una variable usando la CLI, ejecute un comando como:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test`

Las variables actuales pueden enumerarse:

`$ aio cloudmanager:list-pipeline-variables PIPELINEID`

Los nombres de las variables solo pueden contener caracteres alfanuméricos y subrayados (_). Por convención, los nombres deben estar en mayúsculas. Hay un límite de 200 variables por canalización, cada nombre debe tener menos de 100 caracteres y cada valor debe tener menos de 2048 caracteres en el caso de variables de tipo cadena y 500 caracteres en el caso de variables de tipo secretString.

Cuando se utiliza dentro de un `Maven pom.xml` , normalmente resulta útil asignar estas variables a las propiedades de Maven mediante una sintaxis similar a esta:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```


## Instalación de paquetes de sistema adicionales {#installing-additional-system-packages}

Algunas compilaciones requieren que se instalen paquetes de sistema adicionales para funcionar completamente. Por ejemplo, una compilación puede invocar un script Python o ruby y, como resultado, necesita tener instalado un intérprete de idioma adecuado. Esto se puede hacer llamando a la función [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) para invocar APT. Esta ejecución debe envolverse generalmente en un perfil Maven específico de Cloud Manager. Por ejemplo, para instalar python:

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

Esta misma técnica se puede utilizar para instalar paquetes específicos del idioma, es decir, utilizando `gem` para RubyGems o `pip` para paquetes Python.

>[!NOTE]
>La instalación de un paquete del sistema de esta manera sí **not** instálelo en el entorno de tiempo de ejecución utilizado para ejecutar Adobe Experience Manager. Si necesita instalar un paquete del sistema en el entorno de AEM, póngase en contacto con su representante de Adobe.
