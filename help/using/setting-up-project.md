---
title: Configuración del proyecto
description: Siga esta página para aprender a configurar un proyecto
feature: Introducción, Programas De Producción
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
translation-type: tm+mt
source-git-commit: cf19c7dfd593810779c03c51e08081954f8fc11e
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 8%

---

# Configuración del proyecto {#setting-up-your-project}

## Modificación de los detalles de configuración del proyecto {#modifying-project-setup-details}

Para poder crearse e implementarse correctamente con Cloud Manager, los proyectos de AEM existentes deben adherirse a algunas reglas básicas:

* Los proyectos deben crearse con Apache Maven.
* Debe haber un archivo *pom.xml* en la raíz del repositorio de Git. Este archivo *pom.xml* puede hacer referencia a tantos submódulos (que a su vez pueden tener otros submódulos, etc.) según sea necesario.

* Puede añadir referencias a repositorios de artefactos Maven adicionales en sus archivos *pom.xml*. El acceso a [repositorios de artefactos protegidos por contraseña](#password-protected-maven-repositories) se admite cuando se configura. Sin embargo, no se admite el acceso a repositorios de artefactos protegidos por la red.
* Los paquetes de contenido implementables se descubren analizando los archivos de paquete de contenido *zip* que se encuentran en un directorio llamado *target*. Cualquier número de submódulos puede producir paquetes de contenido.

* Los artefactos implementables de Dispatcher se descubren analizando archivos *zip* (nuevamente, contenidos en un directorio llamado *target*) que tienen directorios llamados *conf* y *conf.d*.

* Si hay más de un paquete de contenido, no se garantiza la ordenación de las implementaciones de paquetes. Si se necesita un orden específico, se pueden utilizar dependencias del paquete de contenido para definir el orden. Los paquetes pueden [omitirse](#skipping-content-packages) desde la implementación.


## Activación de perfiles de Maven en Cloud Manager {#activating-maven-profiles-in-cloud-manager}

En algunos casos limitados, es posible que tenga que variar ligeramente el proceso de compilación al ejecutarse dentro de Cloud Manager, en lugar de cuando se ejecuta en estaciones de trabajo para desarrolladores. En estos casos, se pueden usar [Perfiles de Maven](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) para definir cómo debe ser diferente la compilación en diferentes entornos, incluido Cloud Manager.

La activación de un perfil Maven dentro del entorno de compilación de Cloud Manager debe realizarse buscando la variable de entorno CM_BUILD descrita anteriormente. Por el contrario, un perfil que se vaya a usar solo fuera del entorno de compilación de Cloud Manager debe realizarse buscando la ausencia de esta variable.

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
>Para probar este perfil en una estación de trabajo para desarrolladores, puede habilitarlo en la línea de comandos (con `-PcmBuild`) o en el entorno de desarrollo integrado (IDE).

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

>[!NOTE]
>Los artefactos de un repositorio Maven protegido por contraseña solo deben utilizarse con mucha cautela, ya que el código implementado mediante este mecanismo no se ejecuta actualmente a través de las puertas de calidad de Cloud Manager. Por lo tanto, solo debe utilizarse en casos excepcionales y para código no vinculado a AEM. También se recomienda implementar las fuentes Java, así como todo el código fuente del proyecto junto con el binario.

Para utilizar un repositorio Maven protegido por contraseña de Cloud Manager, especifique la contraseña (y, opcionalmente, el nombre de usuario) como una [Variable de canalización](/help/using/build-environment-details.md#pipeline-variables) secreta y, a continuación, haga referencia a ese secreto dentro de un archivo denominado `.cloudmanager/maven/settings.xml` en el repositorio de Git. Este archivo sigue el esquema [Maven Settings File](https://maven.apache.org/settings.html) . Cuando se inicie el proceso de compilación de Cloud Manager, el elemento `<servers>` de este archivo se combinará con el archivo predeterminado `settings.xml` proporcionado por Cloud Manager. Los ID de servidor que comienzan por `adobe` y `cloud-manager` se consideran reservados y no deben usarlos los servidores personalizados. Cloud Manager nunca reflejará los ID de servidor **no** que coincidan con uno de estos prefijos o con el ID predeterminado `central`. Con este archivo en su lugar, se haría referencia al ID de servidor desde un elemento `<repository>` o `<pluginRepository>` dentro del archivo `pom.xml`. Por lo general, estos `<repository>` y/o `<pluginRepository>` elementos estarían contenidos dentro de un [perfil específico de Cloud Manager](#activating-maven-profiles-in-cloud-manager), aunque esto no es estrictamente necesario.

Por ejemplo, supongamos que el repositorio se encuentra en https://repository.myco.com/maven2, el nombre de usuario Cloud Manager debe utilizar es `cloudmanager` y la contraseña es `secretword`.

Primero, establezca la contraseña como un secreto en la canalización:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`

A continuación, haga referencia a esto desde el archivo `.cloudmanager/maven/settings.xml`:

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

Configure el complemento maven-source-plugin en su proyecto:

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

Se recomienda implementar todo el origen del proyecto junto con el binario en un repositorio Maven, lo que permite reconstruir el artefacto exacto.

Configure el complemento maven-assembly-plugin en su proyecto:

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

En Cloud Manager, las compilaciones pueden producir cualquier cantidad de paquetes de contenido.
Por varios motivos, puede ser deseable crear un paquete de contenido, pero no implementarlo. Esto puede resultar útil, por ejemplo, al crear paquetes de contenido que solo se utilizan para pruebas o que se van a volver a empaquetar mediante otro paso en el proceso de compilación, es decir, como un subpaquete de otro paquete.

Para dar cabida a estos escenarios, Cloud Manager buscará una propiedad denominada ***cloudManagerTarget*** en las propiedades de los paquetes de contenido creados. Si esta propiedad se establece en “ninguno”, el paquete se omitirá y no se implementará. El mecanismo para establecer esta propiedad depende de la forma en que la compilación produce el paquete de contenido. Por ejemplo, con el complemento filevault-maven-plugin puede configurar el complemento de esta manera:

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

Con el content-package-maven-plugin es similar:

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

## Desarrolle su código basado en las prácticas recomendadas {#develop-your-code-based-on-best-practices}

Los equipos de Ingeniería y Consultoría de Adobe han desarrollado un [completo conjunto de prácticas recomendadas para desarrolladores de AEM](https://helpx.adobe.com/es/experience-manager/6-4/sites/developing/using/best-practices.html).
