---
title: Creación de un proyecto de aplicación AEM
seo-title: Creación de un proyecto de aplicación AEM
description: nulo
seo-description: Siga esta página para obtener más información sobre la configuración de un proyecto de AEM al iniciarse con Cloud Manager.
uuid: 7 b 976 ebf -5358-49 d 8-a 58 d -0 bae 026303 fa
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introducción
discoiquuid: 76 c 1 a 8 e 4-d 66 f -4 a 3 b -8 c 0 c-b 80 c 9 e 17700 e
translation-type: tm+mt
source-git-commit: b39fc865e3c34052fb94b223d9eebc0fce3495d2

---


# Create an AEM Application Project {#create-an-aem-application-project}

## Using Wizard to Create an AEM Application Project {#using-wizard-to-create-an-aem-application-project}

Cuando los clientes están conectados a Cloud Manager, se les proporciona un repositorio de git vacío. Los actuales clientes de Adobe Managed Services (AMS) (o clientes in situ que estén migrando a AMS) generalmente ya dispondrán de su código de proyecto en git (u otro sistema de control de versiones) e importarán su proyecto al repositorio git de Cloud Manager. Sin embargo, los nuevos clientes no tienen proyectos existentes.

Para ayudarle a empezar a utilizar nuevos clientes, Cloud Manager ahora puede crear un proyecto de AEM mínimo como punto de partida. This process is based on the [**AEM Project Archetype**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T12:52:50.071-0400

2018.8.0: Added this new section

 -->

Siga los pasos a continuación para crear un proyecto de aplicación AEM en Cloud Manager:

1. Once you log in to Cloud Manager and the basic program setup is complete, a special call to action card will be shown on the **Overview** screen, if the repository is empty.

   ![](assets/image2018-10-3_14-29-44.png)

1. Click **Create** to navigate to the **Pipeline Setup** screen.

   ![](assets/image2018-10-3_14-30-22.png)

1. Click **Create to** open a dialog box, which allows the user to provide the parameters required by the AEM Project Archetype. En el formulario predeterminado, el cuadro de diálogo solicita dos valores:

   * **Título** : de forma predeterminada se establece en el nombre *del programa*

   * **Nuevo nombre** de rama: de forma predeterminada, es *maestro*
   ![](assets/screen_shot_2018-10-08at55825am.png)

   El cuadro de diálogo tiene un cajón que se puede abrir haciendo clic en el indicador hacia la parte inferior del cuadro de diálogo. En el formulario ampliado, el cuadro de diálogo muestra todos los parámetros de configuración para el tipo de archetype. Many of these parameters have default values which are generated based on the **Title**.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >For example, if the **Title** is ***We.Finance***, the Base Maven Artifact Id parameter is generated as ***com.wefinance***. Si lo desea, estos valores se pueden cambiar.
   >
   >
   >For example, you can change from the generated ***value com.wefinance*** to ***net.wefinance***.

1. Click **Create** in the preceding step to create the starter project by using the archetype and commit to the named git branch. Una vez que esto ocurra, puede configurar la canalización.

## Setting up your Project {#setting-up-your-project}

### Modifying Project Setup Details {#modifying-project-setup-details}

Para poder crear e implementar correctamente con Cloud Manager, los proyectos de AEM existentes deben atenerse a algunas reglas básicas:

* Los proyectos deben crearse con Apache Maven.
* There must be a *pom.xml* file in the root of the Git repository. This *pom.xml* file can refer to as many submodules (which in turn may have other submodules, etc.) según sea necesario.

* You can add references to additional Maven artifact repositories in your *pom.xml* files. Sin embargo, no se admite el acceso a repositorios de artefactos protegidos mediante contraseña o protegidos por redes.
* Deployable content packages are discovered by scanning for content package *zip* files which are contained in a directory named *target*. Cualquier número de submódulos puede producir paquetes de contenido.

* Deployable Dispatcher artifacts are discovered by scanning for *zip* files (again, contained in a directory named *target*) which have directories named *conf* and *conf.d*.

* Si hay más de un paquete de contenido, no se garantiza el orden de las implementaciones de paquetes. Si se necesita un orden específico, se pueden utilizar dependencias de paquetes de contenido para definir el orden.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## Build Environment Details {#build-environment-details}

Cloud Manager builds and tests your code using a specialized build runtime **Environment**. Este entorno tiene los atributos siguientes:

* El entorno de compilación se basa en Linux.
* Apache Maven 3.6.0 está instalado.
* La versión de Java instalada es Oracle JDK 8 u 202.
* Se han instalado algunos paquetes de sistemas adicionales que son necesarios:

   * bzip2
   * descomprimir
   * libpng
   * imagemagick
   * graphicsmagick
   * Si necesita otros paquetes, deberá solicitarlos a través de los ingenieros de éxito de clientes (CSE).

* Cada compilación se realiza en un entorno impecable; el contenedor de compilación no mantiene ningún estado entre ejecuciones.
* Maven is always run with the command: *mvn --batch-mode clean org.jacoco:jacoco-maven-plugin:prepare-agent package*
* Maven is configured at a system level with a settings.xml file which automatically includes the public Adobe **Artifact** repository. (Refer to [Adobe Public Maven Repository](https://repo.adobe.com/) for more details).

## Activating Maven Profiles in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

En algunos casos limitados, es posible que necesite variar el proceso de diseño ligeramente cuando se ejecuta dentro de Cloud Manager en oposición a cuando se ejecuta en estaciones de trabajo programadoras. For these cases, [Maven Profiles](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) can be used to define how the build should be different in different environments, including Cloud Manager.

Activation of a Maven Profile inside the Cloud Manager build environment should be done by looking for the presence of an environment variable named `CM_BUILD`. Esta variable siempre se configurará dentro del entorno de compilación de Cloud Manager. Por el contrario, un perfil diseñado solo fuera del entorno de creación de Cloud Manager debe realizarse buscando el significado de esta variable.

Por ejemplo, si desea generar un mensaje simple solo cuando la compilación se ejecuta dentro de Cloud Manager, lo haría:

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
>To test this profile on a developer workstation, you can either enable it on the command line (with `-PcmBuild`) or in your Integrated Development Environment (IDE).

Y si desea generar un mensaje simple solo cuando la compilación se ejecuta fuera de Cloud Manager, lo haría:

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

## Variables de entorno personalizado

En algunos casos, el proceso de generación de un cliente puede depender de variables de configuración específicas que serían inadecuadas para colocarse en el repositorio de git. El Administrador de nube permite que un ingeniero de éxito de cliente (CSE) configure estas variables cada cliente. Estas variables se almacenan en una ubicación de almacenamiento seguro y solo son visibles en el contenedor de compilación para el cliente específico. Los clientes que deseen utilizar esta función deben ponerse en contacto con su CSE para configurar sus variables.

Una vez configuradas, estas variables estarán disponibles como variables de entorno. Para utilizarlos como propiedades Maven, puede hacer referencia a ellos dentro del archivo pom.xml, posiblemente dentro de un perfil como se describe anteriormente:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <properties>
                  <my.custom.property>${env.MY_CUSTOM_PROPERTY}</my.custom.property>  
            </properties>
        </profile>
```

>[!NOTE]
>
>Los nombres de variables de entorno sólo pueden contener caracteres alfanuméricos y guiones bajos (_). Por convención, los nombres deberían estar todo en mayúsculas.

## Develop your Code Based on Best Practices {#develop-your-code-based-on-best-practices}

Adobe Engineering and Consulting teams have developed a [comprehensive set of best practices for AEM developers](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html).
