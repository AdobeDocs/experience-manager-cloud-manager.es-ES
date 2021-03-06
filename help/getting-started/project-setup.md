---
title: Configuración del proyecto
description: Obtenga información sobre cómo configurar el proyecto para que pueda administrarlo e implementarlo con Cloud Manager.
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 2%

---


# Configuración del proyecto {#setting-up-your-project}

Obtenga información sobre cómo configurar el proyecto para que pueda administrarlo e implementarlo con Cloud Manager.

## Modificación de proyectos existentes {#modifying-project-setup-details}

Los proyectos de AEM existentes deben adherirse a algunas reglas básicas para crearse e implementarse correctamente con Cloud Manager.

* Los proyectos deben crearse con Apache Maven.
* Debe haber un `pom.xml` en la raíz del repositorio de Git.
   * Esta `pom.xml` puede hacer referencia a tantos submódulos (que a su vez pueden tener otros submódulos) como sea necesario.
   * Puede agregar referencias a repositorios de artefactos Maven adicionales en su `pom.xml` archivos.
   * Acceso a [repositorios de artefactos protegidos por contraseña](#password-protected-maven-repositories) se admite cuando se configura. Sin embargo, no se admite el acceso a repositorios de artefactos protegidos por la red.
* Los paquetes de contenido implementables se descubren analizando los archivos .zip del paquete de contenido que hay en un directorio llamado `target`.
   * Cualquier número de submódulos puede producir paquetes de contenido.
* Los artefactos de Dispatcher implementables se detectan analizando para `zip` archivos contenidos en subdirectorios de `target` named `conf` y `conf.d`.
* Si hay más de un paquete de contenido, no se garantiza la ordenación de las implementaciones de paquetes.
* Si se necesita un orden específico, se pueden utilizar dependencias del paquete de contenido para definir el orden.
* Los paquetes pueden ser [omitido](#skipping-content-packages) desde la implementación.

## Activación de perfiles de Maven en Cloud Manager {#activating-maven-profiles-in-cloud-manager}

En algunos casos limitados, es posible que tenga que variar ligeramente el proceso de compilación al ejecutarse dentro de Cloud Manager, en lugar de cuando se ejecuta en estaciones de trabajo para desarrolladores. Para estos casos, [Perfiles de Maven](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) se puede utilizar para definir cómo la compilación debe ser diferente en diferentes entornos, incluido Cloud Manager.

La activación de un perfil Maven dentro del entorno de compilación de Cloud Manager debe realizarse buscando `CM_BUILD` [variable de entorno](/help/getting-started/build-environment.md#environment-variables) variable de entorno. Por el contrario, un perfil que se vaya a usar solo fuera del entorno de compilación de Cloud Manager debe realizarse buscando la ausencia de esta variable.

Por ejemplo, si desea enviar un mensaje simple solo cuando la compilación se ejecuta dentro de Cloud Manager, debe hacer lo siguiente:

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

Y si desea enviar un mensaje simple solo cuando la compilación se ejecuta fuera de Cloud Manager, debe hacer lo siguiente:

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

Los artefactos de un repositorio Maven protegido por contraseña solo deben utilizarse con mucha cautela, ya que el código implementado mediante este mecanismo no se ejecuta a través de todas las reglas de calidad implementadas en las puertas de calidad de Cloud Manager. También se recomienda implementar las fuentes Java, así como todo el código fuente del proyecto junto con el binario.

>[!TIP]
>
>Los artefactos de repositorios Maven protegidos por contraseña solo deben utilizarse en casos excepcionales y para código no vinculado a AEM.

Para utilizar un repositorio Maven protegido por contraseña de Cloud Manager, especifique la contraseña (y, opcionalmente, el nombre de usuario) como secreto [Variable de canalización](/help/getting-started/build-environment.md#pipeline-variables) y luego hacer referencia a ese secreto dentro de un archivo llamado `.cloudmanager/maven/settings.xml` en el repositorio de Git. Este archivo sigue a la [Archivo de configuración de Maven](https://maven.apache.org/settings.html) esquema.

Cuando se inicia el proceso de creación de Cloud Manager, la variable `<servers>` elemento de este archivo se combinará en el valor predeterminado `settings.xml` archivo proporcionado por Cloud Manager. ID de servidor que empiecen por `adobe` y `cloud-manager` se consideran reservados y no deben utilizarlos los servidores personalizados. Los ID de servidor que no coinciden con uno de estos prefijos o con el ID predeterminado `central` Cloud Manager nunca lo reflejará.

Con este archivo en su lugar, se hará referencia al ID de servidor desde un `<repository>` y/o `<pluginRepository>` dentro del `pom.xml` archivo. Generalmente, estos `<repository>` y/o `<pluginRepository>` los elementos estarían contenidos dentro de un [Perfil específico de Cloud Manager](#activating-maven-profiles-in-cloud-manager), aunque esto no es estrictamente necesario.

Por ejemplo, supongamos que el repositorio se encuentra en `https://repository.myco.com/maven2`, el nombre de usuario de Cloud Manager debe usar es `cloudmanager` y la contraseña es `secretword`.

Primero, establezca la contraseña como un secreto en la canalización:

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword
```

A continuación, haga referencia a esto desde el `.cloudmanager/maven/settings.xml` archivo:

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

Y finalmente hacer referencia al ID de servidor dentro de la variable `pom.xml` archivo:

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

### Implementación de fuentes de proyecto {#deploying-project-sources}

Se recomienda implementar todo el origen del proyecto junto con el binario en un repositorio Maven. Esto permite reconstruir el artefacto exacto.

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

## Omisión de paquetes de contenido {#skipping-content-packages}

En Cloud Manager, las compilaciones pueden producir cualquier cantidad de paquetes de contenido. Por varios motivos, puede ser deseable crear un paquete de contenido, pero no implementarlo. Esto puede resultar útil, por ejemplo, al crear paquetes de contenido que solo se utilizan para pruebas o que se van a volver a empaquetar mediante otro paso en el proceso de compilación, es decir, como un subpaquete de otro paquete.

Para dar cabida a estos escenarios, Cloud Manager buscará una propiedad denominada `cloudManagerTarget` en las propiedades de los paquetes de contenido creados. Si esta propiedad está definida como `none`, el paquete se omitirá y no se implementará. El mecanismo para establecer esta propiedad depende de la forma en que la compilación produce el paquete de contenido. Por ejemplo, con la variable `filevault-maven-plugin` puede configurar el complemento de esta manera:

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

Con la variable `content-package-maven-plugin` es similar:

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

En muchos casos, el mismo código se implementa en varios entornos de AEM. Siempre que sea posible, Cloud Manager evitará la reconstrucción del código base cuando detecte que se utiliza la misma confirmación de Git en varias ejecuciones de canalización de pila completa.

Cuando se inicia una ejecución, se extrae la confirmación del HEAD actual para la canalización de ramas. El hash de confirmación se puede ver en la interfaz de usuario y a través de la API . Cuando el paso de compilación se completa correctamente, los artefactos resultantes se almacenan en función de ese hash de confirmación y se pueden reutilizar en ejecuciones de canalización posteriores.

Los paquetes se reutilizan en todas las canalizaciones si están en el mismo programa. Al buscar paquetes que puedan reutilizarse, AEM ignora las ramas y vuelve a utilizar artefactos entre ramas.

Cuando se produce una reutilización, los pasos de compilación y calidad del código se sustituyen eficazmente por los resultados de la ejecución original. El archivo de registro para el paso de compilación enumerará los artefactos y la información de ejecución que se utilizó para crearlos originalmente.

El siguiente es un ejemplo de este resultado de registro.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

El registro del paso de calidad del código contiene información similar.

### Ejemplos {#example-reuse}

#### Ejemplo 1 {#example-1}

Considere que su programa tiene dos canalizaciones de desarrollo:

* Canalización 1 en rama `foo`
* Canalización 2 en rama `bar`

Ambas ramas están en el mismo ID de confirmación.

1. Al ejecutar primero la canalización 1 se crearán los paquetes normalmente.
1. A continuación, la ejecución de la canalización 2 reutilizará los paquetes creados por la canalización 1.

#### Ejemplo 2 {#example-2}

Tenga en cuenta que el programa tiene dos ramas:

* Rama `foo`
* Rama `bar`

Ambas ramas tienen el mismo ID de confirmación.

1. Se genera y ejecuta una canalización de desarrollo `foo`.
1. Posteriormente, se genera y ejecuta una canalización de producción `bar`.

En este caso, el artefacto de `foo` se reutilizará para la canalización de producción ya que se identificó el mismo hash de confirmación.

### Exclusión {#opting-out}

Si lo desea, el comportamiento de reutilización se puede deshabilitar para canalizaciones específicas configurando la variable de canalización `CM_DISABLE_BUILD_REUSE` a `true`. Si se establece esta variable, el hash de confirmación se extrae y los artefactos resultantes se almacenan para su uso posterior, pero los artefactos almacenados anteriormente no se reutilizarán. Para comprender este comportamiento, considere el siguiente escenario.

1. Se crea una nueva canalización.
1. La canalización se ejecuta (ejecución #1) y la confirmación del HEAD actual es `becdddb`. La ejecución se realiza correctamente y se almacenan los artefactos resultantes.
1. La variable `CM_DISABLE_BUILD_REUSE` está configurada.
1. La canalización se vuelve a ejecutar sin cambiar el código. Aunque hay artefactos almacenados asociados con `becdddb`, no se vuelven a utilizar debido al `CM_DISABLE_BUILD_REUSE` variable.
1. El código se cambia y se ejecuta la canalización. La confirmación del HEAD es ahora `f6ac5e6`. La ejecución se realiza correctamente y se almacenan los artefactos resultantes.
1. La variable `CM_DISABLE_BUILD_REUSE` se eliminará.
1. La canalización se vuelve a ejecutar sin cambiar el código. Dado que hay artefactos almacenados asociados con `f6ac5e6`, esos artefactos se reutilizan.

### Advertencias {#caveats}

* Los artefactos de compilación no se reutilizan en diferentes programas, independientemente de si el hash de confirmación es idéntico.
* Los artefactos de compilación se reutilizan dentro del mismo programa incluso si la rama o canalización son diferentes.
* [Administración de versiones de Maven](/help/managing-code/maven-project-version.md) reemplace la versión del proyecto solo en las canalizaciones de producción. Por lo tanto, si se utiliza la misma confirmación tanto en la ejecución de una implementación de desarrollo como en la ejecución de una canalización de producción, y la canalización de implementación de desarrollo se ejecuta primero, las versiones se implementarán en fase y producción sin ser cambiadas. Sin embargo, se seguirá creando una etiqueta en este caso.
* Si la recuperación de los artefactos almacenados no se realiza correctamente, el paso de compilación se ejecuta como si no se hubieran almacenado artefactos.
* Variables de canalización distintas de `CM_DISABLE_BUILD_REUSE` no se tienen en cuenta cuando Cloud Manager decide reutilizar los artefactos de compilación creados anteriormente.

## Desarrollar el código en función de las prácticas recomendadas {#develop-your-code-based-on-best-practices}

Los equipos de ingeniería y consultoría de Adobe han desarrollado un [conjunto completo de prácticas recomendadas para desarrolladores de AEM.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/bestpractices/best-practices.html)
