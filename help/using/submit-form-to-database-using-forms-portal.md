---
title: Envío de formularios adaptables a la base de datos mediante el Portal de formularios
description: Amplíe el metamodelo predeterminado para agregar patrones, validaciones y entidades específicas de su organización, y aplique configuraciones a los campos de formularios adaptables mientras ejecuta el servicio de conversión automatizada de formularios.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
source-git-commit: 298d6c0641d7b416edb5b2bcd5fec0232f01f4c7
workflow-type: ht
source-wordcount: '1156'
ht-degree: 100%

---


# Integración de formularios adaptables con la base de datos mediante el Portal de formularios {#submit-forms-to-database-using-forms-portal}

El servicio de conversión automatizada de formularios le permite convertir un formulario PDF no interactivo, un AcroForm o un formulario PDF basado en XFA en un formulario adaptable. Al iniciar el proceso de conversión, tiene la opción de generar un formulario adaptable con o sin enlaces de datos.

Si selecciona generar un formulario adaptable sin enlaces de datos, puede integrar el formulario adaptable convertido con un modelo de datos de formulario, un esquema XML o JSON después de la conversión. Sin embargo, si crea un formulario adaptable con enlaces de datos, el servicio de conversión lo asocia automáticamente con un esquema JSON y origina un enlace de datos entre los campos disponibles en el formulario adaptable y el esquema JSON. A continuación, puede integrar el formulario adaptable con una base de datos de su elección, rellenar los datos y enviarlo a la base de datos mediante el Portal de formularios.

La siguiente figura muestra las distintas etapas de integración de un formulario adaptable convertido con una base de datos mediante el Portal de formularios:

![integración de la base de datos](assets/database_integration.gif)

En este artículo se describen las instrucciones paso a paso para ejecutar correctamente todas estas etapas de integración.

El ejemplo que se analiza en este artículo es una implementación de referencia de servicios personalizados de metadatos y datos para integrar una página del Portal de formularios con una base de datos. La base de datos utilizada en la implementación de muestra es MySQL 5.6.24. Sin embargo, puede integrar la página del Portal de formularios con cualquier base de datos de su elección.

## Requisitos previos {#pre-requisites}

* Configuración de una instancia de autor de AEM 6.4 o 6.5
* Instalar el [Service pack más reciente](https://helpx.adobe.com/es/experience-manager/aem-releases-updates.html) para la instancia de AEM
* Última versión del paquete de complementos de AEM Forms
* Configuración del [servicio de conversión automatizada de formularios](configure-service.md)
* Configure una base de datos. La base de datos utilizada en la implementación de muestra es MySQL 5.6.24. Sin embargo, puede integrar el formulario adaptable convertido con cualquier base de datos de su elección.

## Configuración de la conexión entre la instancia de AEM y la base de datos {#set-up-connection-aem-instance-database}

La configuración de una conexión entre una instancia de AEM y una base de datos MySQL consta de lo siguiente:

* [Instalación del paquete del conector MySQL](#install-mysql-connector-java-file)

* [Creación de esquemas y tablas en la base de datos](#create-schema-and-tables-in-database)

* [Configuración de la conexión](#configure-connection-between-aem-instance-and-database)

* [Configuración del paquete de muestra para la integración con el Portal de formularios](#set-up-and-configure-sample)

### Instalar el archivo mysql-connector-java-5.1.39-bin.jar. {#install-mysql-connector-java-file}

Realice los siguientes pasos en todas las instancias de autor y publicación para instalar el archivo mysql-connector-java-5.1.39-bin.jar:

1. Vaya a http://[server]:[port]/system/console/depfinder y busque el paquete com.mysql.jdbc.
1. En la columna Exportado por, compruebe si el paquete fue exportado por algún otro paquete. Continúe si el paquete no se exporta mediante ningún otro.
1. Vaya a http://[server]:[port]/system/console/bundles y haga clic en **[!UICONTROL Install/Update]**.
1. Haga clic en **[!UICONTROL Choose File]** y busque para seleccionar el archivo mysql-connector-java-5.1.39-bin.jar. Seleccione también las casillas de verificación **[!UICONTROL Start Bundle]** y **[!UICONTROL Refresh Packages]**.
1. Haga clic en **[!UICONTROL Install]** o **[!UICONTROL Update]**. Una vez finalizado, reinicie el servidor.
1. (Solo Windows) Desactive el cortafuegos de su sistema operativo.

### Creación de esquemas y tablas en la base de datos {#create-schema-and-tables-in-database}

Siga estos pasos para crear esquemas y tablas en la base de datos:

1. Cree un esquema en la base de datos mediante la siguiente instrucción SQL:

   ```sql
   CREATE SCHEMA `formsportal` ;
   ```

   donde **formsportal** hace referencia al nombre del esquema.

1. Cree una tabla de **datos** en el esquema de la base de datos utilizando la siguiente instrucción SQL:

   ```sql
    CREATE TABLE `data` (
        `owner` varchar(255) DEFAULT NULL,
        `data` longblob,
        `metadataId` varchar(45) DEFAULT NULL,
        `id` varchar(45) NOT NULL,
        PRIMARY KEY (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Cree una tabla de **metadatos** en el esquema de la base de datos utilizando la siguiente instrucción SQL:

   ```sql
   CREATE TABLE `metadata` (
       `formPath` varchar(1000) DEFAULT NULL,
       `formType` varchar(100) DEFAULT NULL,
       `description` text,
       `formName` varchar(255) DEFAULT NULL,
       `owner` varchar(255) DEFAULT NULL,
       `enableAnonymousSave` varchar(45) DEFAULT NULL,
       `renderPath` varchar(1000) DEFAULT NULL,
       `nodeType` varchar(45) DEFAULT NULL,
       `charset` varchar(45) DEFAULT NULL,
       `userdataID` varchar(45) DEFAULT NULL,
       `status` varchar(45) DEFAULT NULL,
       `formmodel` varchar(45) DEFAULT NULL,
       `markedForDeletion` varchar(45) DEFAULT NULL,
       `showDorClass` varchar(255) DEFAULT NULL,
       `sling:resourceType` varchar(1000) DEFAULT NULL,
       `attachmentList` longtext,
       `draftID` varchar(45) DEFAULT NULL,
       `submitID` varchar(45) DEFAULT NULL,
       `id` varchar(60) NOT NULL,
       `profile` varchar(255) DEFAULT NULL,
       `submitUrl` varchar(1000) DEFAULT NULL,
       `xdpRef` varchar(1000) DEFAULT NULL,
       `agreementId` varchar(255) DEFAULT NULL,
       `nextSigners` varchar(255) DEFAULT NULL,
       `eSignStatus` varchar(45) DEFAULT NULL,
       `pendingSignID` varchar(45) DEFAULT NULL,
       `agreementDataId` varchar(255) DEFAULT NULL,
       `enablePortalSubmit` varchar(45) DEFAULT NULL,
       `submitType` varchar(45) DEFAULT NULL,
       `dataType` varchar(45) DEFAULT NULL,
       `jcr:lastModified` varchar(45) DEFAULT NULL,
       PRIMARY KEY (`id`),
       UNIQUE KEY `ID_UNIQUE` (`id`)
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Cree una tabla **additionalmetadatatable** en el esquema de la base de datos utilizando la siguiente instrucción SQL:

   ```sql
   CREATE TABLE `additionalmetadatatable` (
       `value` text,
       `key` varchar(255) NOT NULL,
       `id` varchar(60) NOT NULL,
       PRIMARY KEY (`id`,`key`),
       CONSTRAINT ‘additionalmetadatatable_fk’ FOREIGN KEY (`id`) REFERENCES `metadata` (`id`) ON DELETE CASCADE
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Cree una tabla **commentable** en el esquema de la base de datos utilizando la siguiente instrucción SQL:

   ```sql
   CREATE TABLE `commenttable` (
       `commentId` varchar(255) DEFAULT NULL,
       `comment` text DEFAULT NULL,
       `ID` varchar(255) DEFAULT NULL,
       `commentowner` varchar(255) DEFAULT NULL,
       `time` varchar(255) DEFAULT NULL);
   ```

### Configuración de la conexión entre la instancia de AEM y la base de datos {#configure-connection-between-aem-instance-and-database}

Realice los siguientes pasos de configuración para crear una conexión entre la instancia de AEM y la base de datos MySQL:

1. Vaya a la página de configuración de la consola web de AEM en *http://[host]:[port]/system/console/configMgr*.
1. Haga clic para abrir **[!UICONTROL Forms Portal Draft and Submission Configuration]** en modo de edición.
1. Especifique los valores de las propiedades tal como se describe en la siguiente tabla:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Propiedad</strong></th> 
    <th><strong>Descripción</strong></th>
    <th><strong>Valor</strong></th> 
    </tr> 
    <tr> 
    <td><p>Servicio de datos de borrador del portal de formularios</p></td> 
    <td><p>Identificador del servicio de datos de borrador</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servicio de metadatos de borrador del portal de formularios</p></td> 
    <td><p>Identificador del servicio de metadatos de borrador</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servicio de envío de datos del portal de formularios</p></td> 
    <td><p>Identificador del servicio de envío de datos</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servicio de envío de metadatos del portal de formularios</p></td> 
    <td><p>Identificador del servicio de envío de metadatos</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servicio de datos de firma pendiente del portal de formularios</p></td> 
    <td><p>Identificador del servicio de datos de firma pendiente</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servicio de metadatos de firma pendiente del portal de formularios</p></td> 
    <td><p>Identificador del servicio de metadatos de firma pendiente</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    </tbody> 
    </table>
1. Deje el resto de las configuraciones tal como están y haga clic en **[!UICONTROL Save]**.
1. Busque y haga clic para abrir **[!UICONTROL Apache Sling Connection Pooled DataSource]** en modo de edición en la configuración de la consola web. Especifique los valores de las propiedades tal como se describe en la siguiente tabla:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Propiedad</strong></th> 
    <th><strong>Valor</strong></th> 
    </tr> 
    <tr> 
    <td><p>Nombre de la fuente de datos</p></td> 
    <td><p>Un nombre de fuente de datos para filtrar los controladores del grupo de fuentes de datos. La implementación de muestra utiliza FormsPortal como nombre de la fuente de datos.</p></td>
    </tr>
    <tr> 
    <td><p>Clase de controlador JDBC</p></td> 
    <td><p>com.mysql.jdbc.Driver</p></td>
    </tr>
    <tr> 
    <td><p>URI de conexión JDBC</p></td> 
    <td><p>jdbc:mysql://[host]:[port]/[schema_name]</p></td>
    </tr>
    <tr> 
    <td><p>Nombre de usuario</p></td> 
    <td><p>Un nombre de usuario para autenticar y realizar acciones en tablas de base de datos</p></td>
    </tr>
    <tr> 
    <td><p>Contraseña</p></td> 
    <td><p>La contraseña asociada al nombre de usuario</p></td>
    </tr>
    <tr> 
    <td><p>Aislamiento de transacciones</p></td> 
    <td><p>READ_COMMITTED</p></td>
    </tr>
    <tr> 
    <td><p>Máximo de conexiones activas</p></td> 
    <td><p>1000</p></td>
    </tr>
    <tr> 
    <td><p>Conexiones máximas inactivas</p></td> 
    <td><p>100</p></td>
    </tr>
    <tr> 
    <td><p>Conexiones mínimas inactivas</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Tamaño inicial</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Espera máxima</p></td> 
    <td><p>100 000</p></td>
    </tr>
     <tr> 
    <td><p>Prueba a la vista previa</p></td> 
    <td><p>Comprobado</p></td>
    </tr>
     <tr> 
    <td><p>Prueba mientras está inactiva</p></td> 
    <td><p>Comprobado</p></td>
    </tr>
     <tr> 
    <td><p>Consulta de validación</p></td> 
    <td><p>Los valores de ejemplo son SELECT 1(mysql), select 1 from dual(oracle), SELECT 1(MS Sql Server) (validationQuery)</p></td>
    </tr>
     <tr> 
    <td><p>Tiempo de espera de consulta de validación</p></td> 
    <td><p>10 000</p></td>
    </tr>
    </tbody> 
    </table>

### Configuración del ejemplo {#set-up-and-configure-sample}

Realice los siguientes pasos en todas las instancias de autor y publicación para instalar y configurar el ejemplo:

1. Descargue el siguiente paquete **aem-fp-db-integration-sample-pkg-6.1.2.zip** en su sistema de archivos.

[Obtener archivo](assets/aem-fp-db-integration-sample-pkg-6.1.2.zip)

1. Vaya a al Administrador de paquetes de AEM en *http://[host]:[port]/crx/packmgr/*.
1. Haga clic en **[!UICONTROL Upload Package]**.
1. Busque y seleccione el paquete **aem-fp-db-integration-sample-pkg-6.1.2.zip** y haga clic en **[!UICONTROL OK]**.
1. Haga clic en la opción **[!UICONTROL Install]** que aparece junto al paquete para instalarlo.

## Configuración del formulario adaptable convertido para la integración del Portal de formularios {#configure-converted-adaptive-form-for-forms-portal-integration}

Ejecute los siguientes pasos para habilitar el envío de formularios adaptables mediante la página del Portal de formularios:
1. [Ejecute la conversión](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) para transformar un formulario de origen en uno adaptable.
1. Abra el formulario adaptable en modo de edición.
1. Toque Contenedor de formulario y seleccione Configurar ![Configurar formulario adaptable](assets/configure-adaptive-form.png).
1. En la sección **[!UICONTROL Submission]**, elija **[!UICONTROL Forms Portal Submit Action]** de la lista desplegable **[!UICONTROL Submit Action]**.
1. Toque ![Guardar directiva de plantilla](assets/edit_template_done.png) para guardar la configuración.

## Creación y configuración de la página del Portal de formularios {#create-configure-forms-portal-page}

Realice los siguientes pasos para crear una página del Portal de formularios y configurarla de modo que pueda enviar formularios adaptables mediante ella:

1. Inicie sesión en la instancia de autor de AEM y toque **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Sites]**.
1. Seleccione la ubicación en la que desea guardar la nueva página del Portal de formularios y toque **[!UICONTROL Create]** > **[!UICONTROL Page]**.
1. Seleccione la plantilla de la página, toque **[!UICONTROL Next]**, especifique un título para la página y toque **[!UICONTROL Create]**.
1. Toque **[!UICONTROL Edit]** para configurar la página.
1. En el encabezado de la página, toque ![Editar plantilla](assets/edit_template_sites.png) > **[!UICONTROL Edit Template]** para abrir la plantilla de la página.
1. Toque Contenedor de diseño y ![Editar directiva de plantilla](assets/edit_template_policy.png). En la pestaña **[!UICONTROL Allowed Components]**, habilite las opciones **[!UICONTROL Document Services]** y **[!UICONTROL Document Services Predicates]** y toque ![Guardar directiva de plantilla](assets/edit_template_done.png).
1. Inserte el componente **[!UICONTROL Search & Lister]** en la página. Como resultado, se enumeran en la página todos los formularios adaptables existentes disponibles en la instancia de AEM.
1. Inserte el componente **[!UICONTROL Drafts & Submissions]** en la página. En la página del Portal de formularios aparecen dos pestañas, **[!UICONTROL Draft Forms]** y **[!UICONTROL Submitted Forms]**. La pestaña **[!UICONTROL Draft Forms]** también muestra el formulario adaptable convertido generado mediante los pasos mencionados en [Configuración del formulario adaptable convertido para la integración del Portal de formularios](#configure-converted-adaptive-form-for-forms-portal-integration)

1. Toque **[!UICONTROL Preview]** y el formulario adaptable convertido, especifique valores para los campos de formulario adaptable y envíelo. Los valores especificados para los campos de formulario adaptable se envían a la base de datos integrada.
