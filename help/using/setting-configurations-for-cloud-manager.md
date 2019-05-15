---
title: Configuración de configuraciones generales para el Administrador de nube
seo-title: Configuración de configuraciones generales para Adobe AEM Cloud Manager
description: Requisitos previos para configurar el Administrador de nube y administrar contenido desde su interfaz de usuario.
seo-description: Requisitos previos para configurar Adobe AEM Cloud Manager y administrar contenido desde su interfaz de usuario.
uuid: 65 d 795 f 9-aa 97-4816-b 66 b -03 b 5 ae 961 f 47
contentOwner: jsyal
discoiquuid: 03241 b 88-8 d 28-401 b-aa 42-17 ead 6183 cd 8
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Configuración de configuraciones generales para [!UICONTROL Cloud Manager]{#setting-up-general-configurations-for-cloud-manager}

La sección siguiente resalta los requisitos previos para configurar [!UICONTROL Cloud Manager] y administrar contenido desde su interfaz de usuario.

Esta página de sección cubre los siguientes temas

* **Configuración de usuarios y funciones**
* **Configuración del proyecto de aplicación AEM**
* **Configuraciones de Dispatcher**
* **Optimizaciones de desarrollo**

El siguiente diagrama ilustra las diferentes funciones que permiten [!UICONTROL Cloud Manager] ofrecer continuamente código de mejor calidad:

![](assets/screen_shot_2018-05-01at81926pm.png)

## Configuración de usuarios y funciones {#setting-up-users-and-roles}

Las funciones se administran desde [!UICONTROL Cloud Manager] Adobe Admin Console. Las membresías de función específicas se proporcionan agregando el usuario a un perfil [!UICONTROL Cloud Manager] de producto en la Consola de administración.

>[!CAUTION]
>
>Para usar [!UICONTROL Cloud Manager], debe tener un Adobe ID y el contexto de producto de los servicios gestionados de Adobe.

Puede asignar grupos de funciones específicos agregando el usuario a un perfil [!UICONTROL Cloud Manager] de producto en Admin Console.

Cree las siguientes funciones mediante la Consola de administración para [!UICONTROL Cloud Manager]:

>[!NOTE]
>
>Adobe Admin Console proporciona una ubicación central para gestionar sus autorizaciones de Adobe en toda la organización.
>
>Para obtener más información sobre Adobe Admin Console, consulte la documentación de [Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html).

| **[!UICONTROL Cloud Manager]Funciones** | **Descripción** |
|---|---|
| Propietario comercial | Responsable de definir KPI, aprobar implementaciones de producción y anular errores importantes de 3 niveles. |
| Administrador de programas | Utiliza [!UICONTROL Cloud Manager] para realizar configuraciones de equipo, revisar el estado y ver KPI. Puede aprobar errores importantes de 3 niveles. |
| Administrador de implementación | Gestiona las operaciones de implementación. Utiliza [!UICONTROL Cloud Manager] para ejecutar implementaciones de etapas y producción. Puede aprobar errores importantes de 3 niveles. Tiene acceso a git. |
| Desarrollador | Desarrolla y prueba el código de aplicación personalizado. Utiliza principalmente [!UICONTROL Cloud Manager] para ver el estado. Ha consolidado el acceso a git. |
| Ingeniero de éxito del cliente | Generalmente admite el éxito de los clientes para los clientes de AMS. Interactúa con [!UICONTROL Cloud Manager] el objetivo de ejecutar implementaciones que requieran supervisión CSE. |
| Autor de contenido | Generalmente no interactúa [!UICONTROL Cloud Manager]con. Puede utilizar [!UICONTROL Cloud Manager] el Conmutador de programa (que ha navegado de [!UICONTROL Experience Cloud]) para acceder a AEM. |

### Uso de la Consola de administración para configurar equipo {#using-admin-console-to-set-up-team}

Para proporcionar los permisos adecuados basados en roles a [!UICONTROL Cloud Manager] los usuarios, un administrador de la organización del cliente debe crear nuevos perfiles de producto en Contexto [!UICONTROL AEM Managed Services] de producto.

>[!NOTE]
>
>Para acceder a la consola de administración y configurar su equipo (usuarios y funciones), abra un navegador y visite [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

La adición de usuarios (o grupos) a estos perfiles de producto se realiza utilizando la funcionalidad normal de la Consola de administración, como se muestra en la siguiente figura:

1. Inicie sesión en la Consola de administración y haga clic **en Nuevo perfil** para agregar un nuevo perfil.

   ![](assets/admin_console_roles.png)

1. Complete los campos para configurar una nueva función para [!UICONTROL Cloud Manager].

   Introduzca **Nombre de perfil**, **Descripción** para crear un nuevo perfil. Además, puede seleccionar un **grupo de permisos** para el perfil.

   Haga clic **en Hecho** para completar el paso de creación de perfiles.

   ![](assets/screen_shot_2018-04-23at75014am.png)

## Configuración del proyecto de aplicación AEM {#aem-application-project-setup}

Antes de configurar el proyecto de la aplicación, [!UICONTROL Cloud Manager]tendrá que tener en cuenta uno de los dos escenarios. Puede ser nuevo en AEM 6.4 o ya es cliente existente.

>[!NOTE]
>
>Para tener acceso a [!UICONTROL Cloud Manager], póngase en contacto con los ingenieros de éxito de clientes (CSE) para obtener la dirección URL y las credenciales para empezar.

Puede configurar un proyecto de aplicación para [!UICONTROL Cloud Manager], en base a los dos escenarios siguientes:

* **Nuevo proyecto de AEM**:

Un nuevo proyecto de AEM aprovechará el proyecto existente y trabajará con [!UICONTROL Cloud Manager].

Para obtener más información, consulte [Introducción a AEM 6.4](https://chl-author./content/help/en/experience-manager/6-4/sites/deploying/using/deploy.html). Además, consulte Recursos [AEM](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&mv=other) para obtener más información.

* **Proyecto AEM existente**:

Un proyecto de AEM existente debe confirmar las reglas a la configuración del proyecto. Puede actualizar la instalación existente de AEM para obtener nuevas funciones y mejoras ofrecidas en AEM 6.4 y comenzar [!UICONTROL Cloud Manager]con. Estos criterios deberían funcionar con cambios mínimos. Póngase en contacto con los ingenieros de éxito de clientes (CSE) para obtener asistencia.

Para obtener información adicional sobre cómo actualizar su instancia de AEM a 6.4, consulte [Actualización a AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

### Configuración del repositorio {#setting-up-repository}

Un repositorio de git único y vacío se aprovisiona para cada programa incorporado en [!UICONTROL Cloud Manager]. Los desarrolladores y administradores de implementación se proporcionan con la URL git y las credenciales a partir de su CSE.

Con esta información, un desarrollador puede agregar su código, siguiendo las directrices del** Conjunto de proyectos**, en la sección siguiente, para completar los requisitos de configuración antes de Utilizar [!UICONTROL Cloud Manager].

## Configuraciones de Dispatcher {#dispatcher-configurations}

[!UICONTROL Cloud Manager] puede implementar archivos de configuración de servidor web y de distribuidor, suponiendo que se almacenan en el repositorio de git, además de los paquetes de contenido de AEM normales.

Para aprovechar esta capacidad, la compilación Maven genera un archivo comprimido que contiene dos directorios ***: conf*** y ***conf. d***.

Tras la implementación en una instancia de Dispatcher, el contenido de estos directorios sobrescribirá el contenido de estos directorios en la instancia de Dispatcher. Dado que los archivos de configuración del servidor Web y de la dispatcher suelen requerir información específica del entorno, para que esta capacidad se utilice correctamente, primero deberá trabajar con sus ingenieros de éxito de clientes (CSE) para extraer estas variables de entorno en /etc/sysconfig/httpd.

Siga los pasos a continuación para completar el proceso inicial al configurar Dispatcher:

1. Obtenga archivos de configuración de producción actuales de su CSE.
1. Elimine datos específicos del entorno predeterminado (p. ej., IP de procesador de publicación) y sustituya por variables.
1. Defina las variables necesarias en pares clave-valor para cada despachante de destino y solicite que CSE agregue a ***/etc/sysconfig/httpd*** en cada instancia.
1. Pruebe las configuraciones actualizadas en el escenario y luego solicite que CSE implemente en producción para asegurarse de que funcionan correctamente.
1. Transferir archivos a git.
1. Implementar a través [!UICONTROL Cloud Manager]de.

El archivo zip real se puede producir mediante maven-assembly-plugin. Los proyectos generados con la plantilla Multimódulo de Lazybones AEM pueden tener creada la estructura de proyecto Maven correcta como parte de la creación de proyectos.

>[!NOTE]
>
>La configuración de la dispatcher se realiza durante la introducción [!UICONTROL Cloud Manager], pero también se puede realizar más adelante.

### Configuración de Dispatcher para pruebas de rendimiento {#configuring-dispatcher-for-performance-testing}

Para ejecutar [!UICONTROL Cloud Manager] correctamente las pruebas de rendimiento, el servidor despachante de etapa debe responder a los mismos nombres de host que el despachante de producción de forma coherente con el servidor de producción.

*Por ejemplo*, si un cliente tiene [www.myco.com](http://www.myco.com/) y [www.myotherco.com](http://www.myotherco.com,/) como nombre de host de producción y stage-myco. adobecqms. net como nombre de host del escenario, una solicitud como ésta debe responder correctamente:

```
curl -H"Host: www.myco.com" http://stage-myco.adobecqms.net/en/home.html
```

Esto requerirá no sólo que los nombres de host se configuren correctamente en la configuración del despachante sino también que ***/etc/map***, cualquier Apache vuelva a escribir o que, en realidad, cualquier otra ***regla de asignación o filtro*** de rutas se implemente de manera coherente entre la etapa y la producción.

## Optimizaciones de desarrollo {#development-best-practices}

Antes de utilizar [!UICONTROL Cloud Manager], se recomienda comprender algunas prácticas recomendadas para configurar el proyecto y configurar el servidor Web o desvincular la configuración.

### Configuración del proyecto {#project-set-up}

Los proyectos deben atenerse a algunos criterios para trabajar [!UICONTROL Cloud Manager]con ellos.

Siga las prácticas recomendadas para configurar el proyecto en [!UICONTROL Cloud Manager]:

* La única herramienta de generación proporcionada y admitida es Apache Maven. Apache Maven 3.3.9 está instalado.
* Las compilaciones se ejecutan en un entorno Linux en un contenedor de Docker como el usuario raíz.
* La versión de Java instalada es Oracle JDK 8 u 161.
* Hay algunos paquetes de sistemas adicionales instalados como, por ejemplo, bzip 2, unzip, libpng, imagemagick y graphicsmagick. Si necesita otros paquetes, deberá solicitarlos a través de CSE.
* Maven siempre se ejecuta con el paquete limpio mvn -b.
* Se le proporcionará exactamente un repositorio git. Debe haber un archivo pom.xml en la raíz de este repositorio. Este pom.xml archivo puede referirse a tantos submódulos (que a su vez pueden tener otros submódulos, etc.) si es necesario, pero debe haber sólo un punto de entrada.
* Maven está configurado a nivel de sistema con un archivo settings.xml que incluye automáticamente el repositorio de artefactos pública de Adobe (repo.adobe.com).
* Puede agregar repositorios adicionales en sus pom.xml. Sin embargo, no se admite el acceso a repositorios de artefactos protegidos mediante contraseña o protegidos por redes.
* Los paquetes de contenido implementables se detectan digitalizando archivos zip contenidos en un directorio denominado target. Una vez más, cualquier número de submódulos puede producir paquetes de contenido.
* Si hay más de un paquete de contenido, no se garantiza el orden de las implementaciones de paquetes. Si se necesita un orden específico, se pueden utilizar dependencias de paquetes de contenido para definir el orden.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-05-02T18:18:15.028-0400

change as per KT

 -->

### Pasos siguientes {#the-next-steps}

Una vez configuradas las configuraciones generales, podrá utilizarlas [!UICONTROL Cloud Manager].

Consulte [Uso de [! UICONTROL Cloud Manager]](https://helpx.adobe.com/experience-manager/cloud-manager/using/using-cloud-manager.html) para empezar [!UICONTROL Cloud Manager].
