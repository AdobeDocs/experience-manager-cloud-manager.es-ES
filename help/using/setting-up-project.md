---
title: Configuración del proyecto
description: Siga esta página para conocer cómo configurar un proyecto
translation-type: tm+mt
source-git-commit: f73ea3db4bc50891518bebbe5da2d69dd2890a81
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 7%

---


# Configuración del proyecto {#setting-up-your-project}

## Modificación de los detalles de configuración del proyecto {#modifying-project-setup-details}

Para poder compilar e implementar correctamente con Cloud Manager, los proyectos de AEM existentes deben cumplir algunas reglas básicas:

* Los proyectos deben crearse con Apache Maven.
* Debe haber un *archivo pom.xml* en la raíz del repositorio Git. Este archivo *pom.xml* puede referirse a tantos submódulos (que a su vez pueden tener otros submódulos, etc.) según sea necesario.

* Puede agregar referencias a repositorios de artefactos Maven adicionales en los archivos *pom.xml* . El acceso a repositorios [de artefactos protegidos con](#password-protected-maven-repositories) contraseña se admite cuando se configura. Sin embargo, no se admite el acceso a repositorios de artefactos protegidos por la red.
* Los paquetes de contenido implementable se descubren mediante la búsqueda de archivos *zip* del paquete de contenido que se encuentran en un directorio denominado *destinatario*. Cualquier número de submódulos puede producir paquetes de contenido.

* Los artefactos de Dispatcher implementables se detectan mediante el análisis de archivos *zip* (nuevamente, contenidos en un directorio denominado *destinatario*) que tienen directorios llamados *conf* y *conf.d*.

* Si hay más de un paquete de contenido, no se garantiza el orden de las implementaciones de paquetes. Si se necesita un orden específico, se pueden usar dependencias de paquetes de contenido para definir el orden. Es posible que los paquetes se [omitan](#skipping-content-packages) de la implementación.


## Activación de Perfiles Maven en Cloud Manager {#activating-maven-profiles-in-cloud-manager}

En algunos casos limitados, es posible que deba variar ligeramente el proceso de compilación al ejecutarse dentro de Cloud Manager, en lugar de hacerlo en estaciones de trabajo para desarrolladores. En estos casos, los Perfiles [](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) Maven se pueden usar para definir cómo la compilación debe ser diferente en diferentes entornos, incluido Cloud Manager.

La activación de un Perfil Maven dentro del entorno de compilación de Cloud Manager debe realizarse buscando la variable de entorno CM_BUILD descrita anteriormente. Por el contrario, un perfil que se pretenda utilizar solo fuera del entorno de compilación de Cloud Manager debería realizarse buscando la ausencia de esta variable.

Por ejemplo, si desea enviar un mensaje sencillo solo cuando la compilación se ejecute dentro de Cloud Manager, puede hacer lo siguiente:

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
>Para probar este perfil en una estación de trabajo para desarrolladores, puede habilitarlo en la línea de comandos (con `-PcmBuild`) o en el Entorno de desarrollo integrado (IDE).

Y si desea enviar un mensaje sencillo solo cuando la compilación se ejecute fuera de Cloud Manager, puede hacer lo siguiente:

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

## Compatibilidad con repositorio Maven protegido por contraseña {#password-protected-maven-repositories}

>[!NOTE]
>Los artefactos de un repositorio Maven protegido por contraseña solo deben utilizarse con mucha cautela, ya que el código implementado a través de este mecanismo no se ejecuta actualmente a través de las compuertas de calidad del Administrador de nubes. Por lo tanto, sólo debe utilizarse en casos excepcionales y para código no vinculado a AEM. También se recomienda implementar las fuentes Java, así como todo el código fuente del proyecto, junto con el binario.

Para utilizar un repositorio Maven protegido por contraseña de Cloud Manager, especifique la contraseña (y, opcionalmente, el nombre de usuario) como una variable [secreta de](#pipeline-variables) canalización y, a continuación, haga referencia a ese secreto dentro de un archivo denominado `.cloudmanager/maven/settings.xml` en el repositorio git. Este archivo sigue el esquema [Maven Settings File](https://maven.apache.org/settings.html) . Cuando el administrador de nube genera inicios de proceso, el `<servers>` elemento de este archivo se combina en el archivo `settings.xml` predeterminado proporcionado por Cloud Manager. Los ID de servidor que comienzan con `adobe` y `cloud-manager` se consideran reservados y no deben ser utilizados por servidores personalizados. Los ID de servidor que **no** coincidan con uno de estos prefijos o el ID predeterminado nunca `central` será reflejado por Cloud Manager. Con este archivo en su lugar, se haría referencia a la identificación del servidor desde dentro de un elemento `<repository>` y/o `<pluginRepository>` dentro del `pom.xml` archivo. Por lo general, estos `<repository>` y/o `<pluginRepository>` elementos se contendrían dentro de un perfil [específico del Administrador de](/help/using/create-an-application-project.md#activating-maven-profiles-in-cloud-manager)nube, aunque esto no es estrictamente necesario.

Por ejemplo, supongamos que el repositorio se encuentra en https://repository.myco.com/maven2, el nombre de usuario Cloud Manager debe utilizarse `cloudmanager` y la contraseña es `secretword`.

Primero, establezca la contraseña como un secreto en la canalización:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`

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

Y finalmente haga referencia al ID de servidor dentro del `pom.xml` archivo:

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

### Implementación de fuentes de proyectos {#deploying-project-sources}

Es recomendable implementar todo el origen del proyecto junto con el binario en un repositorio Maven, lo que permite reconstruir el artefacto exacto.

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

En Cloud Manager, las compilaciones pueden producir cualquier número de paquetes de contenido.
Por diversos motivos, puede que sea conveniente crear un paquete de contenido pero no implementarlo. Esto puede resultar útil, por ejemplo, cuando se generan paquetes de contenido que solo se utilizan para pruebas o que se van a volver a empaquetar con otro paso en el proceso de compilación, es decir, como un subpaquete de otro paquete.

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

## Desarrollar el código en base a las optimizaciones {#develop-your-code-based-on-best-practices}

Los equipos de Ingeniería y Consultoría de Adobe han desarrollado un [completo conjunto de optimizaciones para desarrolladores](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html)de AEM.
