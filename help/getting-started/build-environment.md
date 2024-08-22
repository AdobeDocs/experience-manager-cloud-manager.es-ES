---
title: El entorno de compilación
description: Obtenga información sobre el entorno de compilación especializado en el que los usuarios de Cloud Manager generan y prueban su código.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 54%

---


# El entorno de compilación {#build-environment}

Obtenga información sobre el entorno de compilación especializado en el que los usuarios de Cloud Manager generan y prueban su código.

## Detalles del entorno {#details}

Los entornos de compilación de Cloud Manager tienen los atributos siguientes.

* El entorno de compilación está basado en Linux, derivado de Ubuntu 22.04.
* Apache Maven 3.9.4 está instalado.
   * El Adobe recomienda a los usuarios [actualizar sus repositorios Maven para que utilicen HTTPS en lugar de HTTP](#https-maven).
* Las versiones de Java instaladas son Oracle JDK 8u401 y Oracle JDK 11.0.22.
   * `/usr/lib/jvm/jdk1.8.0_401`
   * `/usr/lib/jvm/jdk-11.0.22`
* De forma predeterminada, la variable de entorno `JAVA_HOME` está configurada en `/usr/lib/jvm/jdk1.8.0_401`, que contiene el JDK de Oracle 8u401. Consulte la sección [Versión JDK de ejecución de Maven alternativa](#alternate-maven) para obtener más información.
* Hay algunos paquetes de sistema adicionales instalados que son necesarios.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* Se pueden instalar otros paquetes en el momento de la compilación, tal como se describe en la sección [Instalación de paquetes de sistema adicionales](#installing-additional-system-packages).
* Cada compilación se realiza en un entorno en buen estado. El contenedor de compilación no mantiene ningún estado entre las ejecuciones.
* Maven siempre se ejecuta con estos tres comandos:
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven se configura a nivel de sistema con un archivo `settings.xml`, que incluye automáticamente el repositorio de artefactos de Adobe público usando un perfil denominado `adobe-public`. Consulte el [repositorio Maven público de Adobe](https://repo1.maven.org/) para obtener más información.
* Node.js 18 está disponible para [canalizaciones front-end](/help/overview/ci-cd-pipelines.md).

>[!NOTE]
>
>Aunque Cloud Manager no define una versión específica de `jacoco-maven-plugin`, la versión utilizada debe ser al menos `0.7.5.201505241946`.

>[!TIP]
>
>Consulte los siguientes recursos adicionales para aprender a utilizar las API de Cloud Manager:
>
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Creación de una integración de API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [Permisos de API](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)

## Repositorios HTTPS Maven {#https-maven}

Cloud Manager [2023.10.0](/help/release-notes/2023/2023-10-0.md) inició una actualización gradual del entorno de compilación (que se completó con la versión 2023.12.0), que incluyó una actualización de Maven 3.8.8. Un cambio significativo introducido en Maven 3.8.1 fue una mejora de la seguridad destinada a mitigar posibles vulnerabilidades. Específicamente, Maven ahora deshabilita todas las duplicaciones `http://*` no seguras de forma predeterminada, como se describe en las [notas de la versión de Maven](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291).

Como resultado de esta mejora de seguridad, algunas personas pueden tener problemas durante el paso de compilación, especialmente al descargar artefactos de repositorios Maven que utilizan conexiones HTTP no seguras.

Para garantizar una experiencia sin problemas con la versión actualizada, Adobe recomienda actualizar los repositorios de Maven para que utilicen HTTPS en lugar de HTTP. Este ajuste se ha llevado a cabo para adaptarse a la adopción creciente de la industria de protocolos de comunicación seguros y ayuda a mantener un proceso de compilación seguro y fiable.

## Uso de una versión de Java específica {#using-java-version}

De forma predeterminada, los proyectos creados por el proceso de compilación de Cloud Manager utilizan el JDK de Oracle 8. Los clientes que deseen utilizar un JDK alternativo tienen dos opciones.

* [Cadenas de herramientas de Maven](#maven-toolchains)
* [Selección de una versión JDK alternativa para todo el proceso de ejecución de Maven](#alternate-maven)

### Cadenas de herramientas de Maven {#maven-toolchains}

El [complemento Maven Toolchains](https://maven.apache.org/plugins/maven-toolchains-plugin/) permite que los proyectos seleccionen un JDK específico (o toolchain) para usarlo en el contexto de complementos Maven con conocimiento de herramientas. Este proceso se realiza en el archivo `pom.xml` del proyecto especificando un valor de proveedor y de versión. Una sección de muestra en el archivo `pom.xml` es la siguiente:

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

Este proceso hace que todos los complementos Maven con conocimiento de herramientas utilicen el JDK de Oracle, versión 11.

Al utilizar este método, Maven se sigue ejecutando con el JDK predeterminado (Oracle 8) y la variable de entorno `JAVA_HOME` no cambia. Por lo tanto, comprobar o aplicar la versión de Java a través de complementos como el [complemento Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) no funciona y estos complementos no deben usarse.

Las combinaciones de proveedor/versión disponibles actualmente son:

| Proveedor | Versión |
|---|---|
| Oracle | 1.8 |
| Oracle | 1.11 |
| Oracle | 11 |
| dom. | 1.8 |
| dom. | 1.11 |
| dom. | 11 |

>[!NOTE]
>
>A partir de abril de 2022, el JDK de Oracle AEM será el JDK predeterminado para el desarrollo y el funcionamiento de aplicaciones de. El proceso de creación de Cloud Manager cambia automáticamente al uso de JDK de Oracle, incluso si se selecciona explícitamente una opción alternativa en la cadena de herramientas de Maven. Consulte las [notas de la versión de abril](/help/release-notes/2022/2022-4-0.md) para obtener más información.

### Versión JDK de ejecución de Maven alternativa {#alternate-maven}

También es posible seleccionar Oracle 8 u Oracle 11 como JDK para toda la ejecución de Maven. A diferencia de las opciones de cadenas de herramientas, esto cambia el JDK utilizado para todos los complementos, a menos que también se establezca la configuración de cadenas de herramientas, en cuyo caso esta se sigue aplicando a los complementos Maven compatibles con ella. Como resultado, funciona la comprobación y aplicación de la versión de Java mediante el [complemento Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/).

Para realizar este proceso, cree un archivo con el nombre `.cloudmanager/java-version` en la rama del repositorio Git utilizada por la canalización. Este archivo puede tener el contenido `11` o `8`. Se omite cualquier otro valor. Si se especifica `11`, se usa Oracle 11 y la variable de entorno `JAVA_HOME` se establece en `/usr/lib/jvm/jdk-11.0.22`. Si se especifica `8`, se utiliza Oracle 8 y la variable de entorno `JAVA_HOME` se establece en `/usr/lib/jvm/jdk1.8.0_401`.

## Variables de entorno {#environment-variables}

### Variables de entorno estándar {#standard-environ-variables}

En algunos casos, puede que sea necesario variar el proceso de compilación en función de la información acerca del programa o la canalización.

Por ejemplo, al utilizar una herramienta como gulp para la minificación de JavaScript, es posible que prefiera diferentes niveles de minificación para los entornos de desarrollo frente a los de ensayo y producción.

Para ello, Cloud Manager añade variables de entorno estándar al contenedor de compilación para cada ejecución.

| Nombre de la variable | Descripción |
|---|---|
| `CM_BUILD` | Siempre establecido en `true` |
| `BRANCH` | La rama configurada para la ejecución |
| `CM_PIPELINE_ID` | El identificador numérico de la canalización |
| `CM_PIPELINE_NAME` | El nombre de la canalización |
| `CM_PROGRAM_ID` | Identificador numérico del programa |
| `CM_PROGRAM_NAME` | El nombre del programa |
| `ARTIFACTS_VERSION` | En el caso de una canalización de ensayo o de producción, la versión sintética generada por Cloud Manager |

### Disponibilidad de variables de entorno estándar {#availability}

Las variables de entorno estándar se pueden usar en varios lugares.

#### Entornos de creación, previsualización y publicación {#author-preview-publish}

Tanto las variables de entorno normales como los secretos se pueden usar en los entornos de creación, previsualización y publicación.

#### Dispatcher {#dispatcher}

Solo se pueden usar variables de entorno normales con [Dispatcher](https://experienceleague.adobe.com/es/docs/experience-manager-dispatcher/using/dispatcher). Los secretos no se pueden usar.

Sin embargo, las variables de entorno no se pueden usar en `IfDefine` directivas.

>[!TIP]
>
>Valide el uso de variables de entorno con [Dispatcher localmente](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools) antes de implementar.

#### Configuraciones de OSGi {#osgi}

Tanto las variables de entorno normales como los secretos se pueden utilizar en las [configuraciones OSGi](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi).

### Variables de canalización {#pipeline-variables}

En algunos casos, el proceso de compilación puede depender de variables de configuración específicas que no serían adecuadas para colocarse en el repositorio de Git o que necesitarían variar entre ejecuciones de canalización que utilicen la misma rama.

Cloud Manager permite que estas variables se configuren mediante la API de Cloud Manager o la CLI de Cloud Manager por canalización. Las variables pueden almacenarse como texto sin formato o cifrarse en reposo. En cualquier caso, las variables están disponibles en el entorno de compilación como una variable de entorno, a la que se puede hacer referencia desde dentro del archivo `pom.xml` u otras secuencias de comandos de compilación.

Para establecer una variable mediante la CLI, ejecute un comando similar al siguiente.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Las variables actuales se pueden enumerar mediante un comando similar al siguiente.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Las variables deben cumplir ciertas limitaciones.

* Los nombres de las variables solo pueden contener caracteres alfanuméricos y el guion bajo (`_`).
   * Por convención, los nombres deberían estar en mayúsculas.
* Hay un límite de 200 variables por canalización.
* Cada nombre debe tener menos de 100 caracteres.
* Cada valor de cadena debe tener menos de 2048 caracteres.
* Cada valor de `secretString` debe tener menos de 500 caracteres.

Cuando se utiliza dentro de un archivo `pom.xml` de Maven, suele resultar útil asignar estas variables a las propiedades de Maven mediante una sintaxis similar a la siguiente.

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

Para funcionar completamente, algunas compilaciones requieren que se instalen paquetes de sistema adicionales. Por ejemplo, una compilación puede invocar un script de Python o Ruby y, como resultado, necesita tener instalado un intérprete de idioma adecuado. Este escenario se puede realizar llamando a [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) para invocar APT. Esta ejecución debe envolverse generalmente en un perfil Maven específico de Cloud Manager. Por ejemplo, para instalar Python puede hacer lo siguiente:

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

Esta técnica también se puede utilizar para instalar paquetes específicos del idioma. Es decir, usar `gem` para RubyGems o `pip` para paquetes Python.

>[!NOTE]
>
>La instalación de un paquete del sistema de esta manera no lo instala en el entorno de tiempo de ejecución utilizado para ejecutar Adobe Experience Manager. Si necesita instalar un paquete del sistema en el entorno de AEM, póngase en contacto con su representante de Adobe.
