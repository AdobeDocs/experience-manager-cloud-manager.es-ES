---
title: Explicación del Entorno de compilación
description: Siga esta página para conocer los entornos
translation-type: tm+mt
source-git-commit: 57a99792e151bd5fe69c8372b6a9d3b100036a51
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---


# Explicación del Entorno de compilación {#build-environment-details}

Cloud Manager crea y prueba el código mediante un entorno de compilación especializado. Este entorno tiene los atributos siguientes:

* El entorno de compilación está basado en Linux, derivado de Ubuntu 18.04.
* Se ha instalado Apache Maven 3.6.0.
* Las versiones de Java instaladas son Oracle JDK 8u202 y 11.0.2.
* Hay algunos paquetes de sistema adicionales instalados que son necesarios:

   * bzip2
   * descomprimir
   * libpng
   * imagemagick
   * graphicsmagick

* Se pueden instalar otros paquetes en el momento de la compilación, como se describe [a continuación](#installing-additional-system-packages).
* Cada obra se construye sobre un entorno prístino; el contenedor de compilación no mantiene ningún estado entre las ejecuciones.
* Maven siempre se ejecuta con estos tres comandos:

   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`

* Maven se configura a nivel de sistema con un archivo settings.xml que incluye automáticamente el repositorio público de Adobe **Artiact** . (Consulte Repositorio [de Maven Público de](https://repo.adobe.com/) Adobe para obtener más detalles).

>[!NOTE]
>Aunque Cloud Manager no define una versión específica del `jacoco-maven-plugin`, la versión utilizada debe ser al menos `0.7.5.201505241946`.

## Uso de Java 11 {#using-java-11}

Cloud Manager ahora admite la creación de proyectos de clientes con Java 8 y Java 11. De forma predeterminada, los proyectos se crean con Java 8. Los clientes que deseen utilizar Java 11 en sus proyectos pueden hacerlo usando el complemento [Apache Maven Toolchain](https://maven.apache.org/plugins/maven-toolchains-plugin/).

Para ello, en el archivo pom.xml, agregue una `<plugin>` entrada con este aspecto:

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

>[!NOTE]
>Los `vendor` valores admitidos son `oracle` y `sun` y los `version` valores admitidos son `1.8`, `1.11`y `11`.

>[!NOTE]
>La compilación del proyecto de Cloud Manager sigue usando Java 8 para invocar Maven, por lo tanto la comprobación o aplicación de la versión de Java configurada en el complemento toolchain a través de complementos como el complemento [](https://maven.apache.org/enforcer/maven-enforcer-plugin/) Apache Maven Enforcer no funciona y estos complementos no deben utilizarse.

## Variables de entorno {#environment-variables}

### Variables de Entorno estándar {#standard-environ-variables}

En algunos casos, los clientes consideran necesario variar el proceso de compilación en función de la información sobre el programa o la canalización.

Por ejemplo, si se está realizando la minimización de JavaScript en tiempo de compilación, a través de una herramienta como gulp, puede haber un deseo de usar un nivel de Minificación diferente al construir para un entorno de desarrollo en lugar de construir para etapa y producción.

Para admitir esto, Cloud Manager agrega estas variables de entorno estándar al contenedor de compilación para cada ejecución.

| **Nombre de variable** | **Definición** |
|---|---|
| CM_BUILD | Siempre definido como &quot;true&quot; |
| RAMA | La rama configurada para la ejecución |
| CM_PIPELINE_ID | El identificador de canalización numérica |
| CM_PIPELINE_NAME | El nombre de la canalización |
| CM_PROGRAMA_ID | El identificador de programa numérico |
| CM_PROGRAMA_NAME | El nombre del programa |
| ARTIFACTS_VERSION | Para una fase o canalización de producción, la versión sintética generada por Cloud Manager |

### Variables de canalización {#pipeline-variables}

En algunos casos, el proceso de generación de un cliente puede depender de variables de configuración específicas que no se pueden colocar en el repositorio Git o que necesitan variar entre las ejecuciones de canalizaciones que utilizan la misma rama.

Cloud Manager permite configurar estas variables mediante la API de Cloud Manager o la CLI de Cloud Manager por canalización. Las variables pueden almacenarse como texto sin formato o cifradas en reposo. En cualquier caso, las variables se ponen a disposición dentro del entorno de compilación como una variable de entorno a la que se puede hacer referencia desde dentro del `pom.xml` archivo u otras secuencias de comandos de compilación.

Para configurar una variable mediante la CLI, ejecute un comando como:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test`

Se pueden enumerar las variables actuales:

`$ aio cloudmanager:list-pipeline-variables PIPELINEID`

Los nombres de variables solo pueden contener caracteres alfanuméricos y de subrayado (_). Por convención, los nombres deben estar en mayúsculas. Hay un límite de 200 variables por canalización, cada nombre debe tener menos de 100 caracteres y cada valor debe tener menos de 2048 caracteres.

Cuando se utiliza dentro de un `Maven pom.xml` archivo, generalmente resulta útil asignar estas variables a las propiedades de Maven con una sintaxis similar a esta:

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

Algunas compilaciones requieren que se instalen paquetes de sistema adicionales para funcionar completamente. Por ejemplo, una compilación puede invocar una secuencia de comandos Python o ruby y, como resultado, debe tener instalado un intérprete de idioma adecuado. Esto se puede hacer llamando al [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) para invocar APT. Esta ejecución generalmente debe envolverse en un perfil Maven específico del Administrador de la nube. Por ejemplo, para instalar python:

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

Esta misma técnica se puede utilizar para instalar paquetes específicos de idioma, es decir, `gem` para RubyGems o `pip` para paquetes Python.

>[!NOTE]
>
>La instalación de un paquete de sistema de esta manera **no** lo instala en el entorno de tiempo de ejecución utilizado para ejecutar Adobe Experience Manager. Si necesita un paquete de sistema instalado en el entorno de AEM, póngase en contacto con los ingenieros de éxito del cliente (CSE).
