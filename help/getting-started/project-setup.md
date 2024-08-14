---
title: Configurar el proyecto
description: Obtenga información sobre cómo configurar el proyecto para que pueda administrarlo e implementarlo con Cloud Manager.
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 54%

---


# Configurar el proyecto {#setting-up-your-project}

Obtenga información sobre cómo configurar el proyecto para que pueda administrarlo e implementarlo con Cloud Manager.

## Editar proyectos existentes {#modifying-project-setup-details}

AEM Los proyectos existentes deben adherirse a algunas reglas básicas para que se puedan crear e implementar correctamente con Cloud Manager.

* Los proyectos deben crearse con Apache Maven.
* Debe haber un archivo `pom.xml` en la raíz del repositorio de Git.
   * El archivo `pom.xml` puede hacer referencia a tantos submódulos (que a su vez pueden tener otros submódulos) como sea necesario.
   * Puede agregar referencias a repositorios de artefactos Maven adicionales en sus archivos `pom.xml`.
   * El acceso a [repositorios de artefactos protegidos por contraseña](#password-protected-maven-repositories) se admite cuando se configura. Sin embargo, no se admite el acceso a repositorios de artefactos protegidos por la red.
* Los paquetes de contenido implementables se descubren analizando los archivos .zip del paquete de contenido que hay en un directorio llamado `target`.
   * Cualquier número de submódulos puede producir paquetes de contenido.
* Los artefactos de Dispatcher implementables se detectan analizando archivos `zip` contenidos en subdirectorios de `target` llamados `conf` y `conf.d`.
* Si hay más de un paquete de contenido, no se garantiza el pedido de las implementaciones de paquetes.
* Si se necesita un orden específico, se pueden utilizar dependencias del paquete de contenido para definir el orden.
* Los paquetes pueden ser [omitidos](#skipping-content-packages) desde la implementación.

## Activación de perfiles de Maven en Cloud Manager {#activating-maven-profiles-in-cloud-manager}

En algunos casos limitados, es posible que tenga que variar ligeramente el proceso de generación al ejecutarse dentro de Cloud Manager, en lugar de cuando se ejecuta en estaciones de trabajo para desarrolladores. En estos casos, se pueden utilizar [Perfiles de Maven](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) para definir cómo la generación debe ser distinta en diferentes entornos, incluido Cloud Manager.

La activación de un perfil Maven dentro del entorno de compilación de Cloud Manager debe realizarse al buscar `CM_BUILD` [variable de entorno](/help/getting-started/build-environment.md#environment-variables). Por el contrario, un perfil que se vaya a usar solamente fuera del entorno de compilación de Cloud Manager debe realizarse buscando la ausencia de esta variable.

Por ejemplo, si desea que salga un mensaje simple cuando la generación se ejecuta solamente dentro de Cloud Manager, debe hacer lo siguiente:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>Para probar este perfil en una estación de trabajo para desarrolladores, puede activarlo en la línea de comandos (con `-PcmBuild`) o en su entorno de desarrollo integrado (IDE).

Y si desea que salga un mensaje simple cuando la generación se ejecuta solamente fuera de Cloud Manager, debe hacer lo siguiente:

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

## Compatibilidad con repositorios Maven protegidos por contraseña {#password-protected-maven-repositories}

Los artefactos de un repositorio Maven protegido por contraseña deben utilizarse con precaución porque el código implementado de esta manera no está completamente sujeto a las comprobaciones de calidad impuestas por las puertas de calidad de Cloud Manager. El Adobe también recomienda implementar las fuentes Java y todo el código fuente del proyecto junto con el binario.

>[!TIP]
>
>Los artefactos de repositorios Maven protegidos por contraseña solo deben utilizarse en casos excepcionales y para un código no vinculado a AEM.

Para usar un repositorio Maven protegido por contraseña de Cloud Manager, especifique la contraseña (y, opcionalmente, el nombre de usuario) como secreto [Variable de canalización](/help/getting-started/build-environment.md#pipeline-variables) y luego haga referencia a ese secreto dentro de un archivo llamado `.cloudmanager/maven/settings.xml` en el repositorio de Git. Este archivo sigue el esquema [Archivo de configuración de Maven](https://maven.apache.org/settings.html).

Cuando se inicia el proceso de generación de Cloud Manager, el elemento `<servers>` de este archivo se combina con el archivo `settings.xml` predeterminado proporcionado por Cloud Manager. Los servidores personalizados no deben usar identificadores de servidor que comiencen por `adobe` y `cloud-manager`. Estos ID se consideran reservados. Cloud Manager refleja únicamente los Id. de servidor que coinciden con uno de los prefijos especificados o con el Id. predeterminado `central`.

Con este archivo en su lugar, se hará referencia al ID de servidor desde un elemento `<repository>` o `<pluginRepository>` dentro del archivo `pom.xml`. Generalmente, los elementos `<repository>` o `<pluginRepository>` estarían contenidos dentro de un [Perfil específico de Cloud Manager](#activating-maven-profiles-in-cloud-manager), aunque esto no es estrictamente necesario.

Por ejemplo, supongamos que el repositorio se encuentra en `https://repository.myco.com/maven2`, el nombre de usuario que Cloud Manager debe usar es `cloudmanager` y la contraseña es `secretword`.

Primero, establezca la contraseña como un secreto en la canalización:

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword
```

A continuación, haga referencia a lo siguiente desde el archivo `.cloudmanager/maven/settings.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>myco-repository</id>
            <username>cloudmanager</username>
            <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
        </server>
    </servers>
</settings>
```

Y finalmente haga referencia al ID de servidor dentro del archivo `pom.xml`:

```xml
<profiles>
    <profile>
        <id>cmBuild</id>
        <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
        </activation>
        <build>
            <repositories>
                <repository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </pluginRepository>
            </pluginRepositories>
        </build>
    </profile>
</profiles>
```

### Implementación de fuentes {#deploying-sources}

Se recomienda implementar las fuentes Java junto con el binario en un repositorio Maven.

Configure las variables `maven-source-plugin` en el proyecto:

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-source-plugin</artifactId>
            <executions>
                <execution>
                    <id>attach-sources</id>
                    <goals>
                        <goal>jar-no-fork</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
```

### Implementar orígenes de proyecto {#deploying-project-sources}

Se recomienda implementar todo el origen del proyecto junto con el binario en un repositorio Maven. Al hacerlo, se puede reconstruir el artefacto exacto.

Configure las variables `maven-assembly-plugin` en el proyecto:

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <executions>
                <execution>
                    <id>project-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                    <configuration>
                        <descriptorRefs>
                            <descriptorRef>project</descriptorRef>
                        </descriptorRefs>
                    </configuration>
                </execution>
            </executions>
        </plugin>
```

## Omitir paquetes de contenido {#skipping-content-packages}

En Cloud Manager, las generaciones pueden producir cualquier cantidad de paquetes de contenido. Por varios motivos, puede ser recomendable producir un paquete de contenido, pero no implementarlo. Por ejemplo, este método puede resultar útil cuando genera paquetes de contenido únicamente para realizar pruebas o cuando otro paso en el proceso de generación los vuelve a empaquetar. Es decir, como un paquete secundario de otro paquete.

Para dar cabida a estos escenarios, Cloud Manager busca una propiedad denominada `cloudManagerTarget` en las propiedades de los paquetes de contenido creados. Si esta propiedad se establece en `none`, el paquete se omitirá y no se implementará. El mecanismo para establecer esta propiedad depende de la forma en que la compilación produce el paquete de contenido. Por ejemplo, con `filevault-maven-plugin` configuraría el complemento de esta manera:

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

Con `content-package-maven-plugin`, es similar:

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

## Generar reutilización de artefactos {#build-artifact-reuse}

En muchos casos, el mismo código se implementa en varios entornos de AEM. Cuando es posible, Cloud Manager evita la reconstrucción del código base cuando detecta que se utiliza el mismo compromiso de Git en varias ejecuciones de canalización full-stack.

Cuando se inicia una ejecución, se extrae el compromiso de HEAD actual para la canalización de ramas. El hash de compromiso se puede ver en la interfaz de usuario y a través de la API. Cuando el paso de generación se completa correctamente, los artefactos resultantes se almacenan en base a ese hash de compromiso y se pueden reutilizar en ejecuciones de canalización posteriores.

Los paquetes se reutilizan en todas las canalizaciones si están en el mismo programa. Al buscar paquetes que puedan reutilizarse, AEM ignora las ramas y vuelve a utilizar artefactos a través de las ramas.

Cuando se produce una reutilización, los pasos de generación y calidad del código se sustituyen eficazmente por los resultados de la ejecución original. El archivo de registro para el paso de generación enumera los artefactos y la información de ejecución que se utilizó para crearlos originalmente.

El siguiente es un ejemplo de este resultado de registro.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

El registro del paso de calidad del código contiene información similar.

### Ejemplos {#example-reuse}

#### Ejemplo 1 {#example-1}

Imagine que su programa tiene dos canalizaciones de desarrollo:

* Canalización 1 en rama `foo`
* Canalización 2 en rama `bar`

Ambas ramas están en el mismo Id. de compromiso.

1. Al ejecutar primero la canalización 1 se generan los paquetes normalmente.
1. A continuación, al ejecutar la canalización 2, se vuelven a utilizar los paquetes creados por la canalización 1.

#### Ejemplo 2 {#example-2}

Imagine que su programa tiene dos ramas: la `foo` y la `bar`.

Ambas ramas tienen el mismo Id. de compromiso.

1. Se genera y ejecuta una canalización de desarrollo `foo`.
1. Posteriormente, se genera y ejecuta una canalización de producción `bar`.

En este caso, el artefacto de `foo` se reutiliza para la canalización de producción porque se identificó el mismo hash de confirmación.

### Exclusión {#opting-out}

Si lo desea, el comportamiento de reutilización se puede deshabilitar para canalizaciones específicas si configura la variable de canalización `CM_DISABLE_BUILD_REUSE` a `true`. Si se establece esta variable, el hash de compromiso se extrae igualmente. Los artefactos resultantes se almacenan para su uso posterior, pero los artefactos almacenados anteriormente no se reutilizan. Para comprender este comportamiento, considere el siguiente escenario:

1. Se crea una nueva canalización.
1. La canalización se ejecuta (ejecución #1) y el compromiso de HEAD actual es `becdddb`. La ejecución se realiza correctamente y se almacenan los artefactos resultantes.
1. La variable `CM_DISABLE_BUILD_REUSE` está configurada.
1. La canalización se vuelve a ejecutar sin cambiar el código. Aunque hay artefactos almacenados asociados con `becdddb`, no se vuelven a utilizar debido a la variable `CM_DISABLE_BUILD_REUSE`.
1. El código se cambia y se ejecuta la canalización. El compromiso de HEAD es ahora `f6ac5e6`. La ejecución se realiza correctamente y se almacenan los artefactos resultantes.
1. La variable `CM_DISABLE_BUILD_REUSE` se elimina.
1. La canalización se vuelve a ejecutar sin cambiar el código. Dado que hay artefactos almacenados asociados con `f6ac5e6`, esos artefactos se reutilizan.

### Advertencias {#caveats}

* Los artefactos de generación no se reutilizan en programas diferentes, independientemente de si el hash de compromiso es idéntico.
* Los artefactos de compilación se reutilizan dentro del mismo programa, aunque sean diferentes la rama o la canalización.
* La [Administración de versiones de Maven](/help/managing-code/maven-project-version.md) reemplaza la versión del proyecto solo en las canalizaciones de producción. Si se utiliza el mismo compromiso tanto para las canalizaciones de desarrollo como de producción, y la canalización de desarrollo se ejecuta primero, las versiones se implementan en fase y producción sin cambios. Sin embargo, en este caso, se sigue creando una etiqueta.
* Si la recuperación de los artefactos almacenados no se realiza correctamente, el paso de generación se ejecuta como si no se almacenaran artefactos.
* Las variables de canalización distintas de `CM_DISABLE_BUILD_REUSE` no se tienen en cuenta cuando Cloud Manager decide reutilizar los artefactos de generación creados anteriormente.

## Desarrolle su código en función de las prácticas recomendadas {#develop-your-code-based-on-best-practices}

Los equipos de ingeniería y consultoría de Adobe AEM han desarrollado un conjunto [completo de prácticas recomendadas para desarrolladores de](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/bestpractices/best-practices).
