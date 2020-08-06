---
title: Envío de formularios adaptables a la base de datos mediante Forms Portal
description: Amplíe el meta-modelo predeterminado para agregar patrones, validaciones y entidades específicas de su organización y aplique configuraciones a campos de formulario adaptables mientras ejecuta el servicio Conversión automatizada de Forms.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: ead1b4ee177029c60f095dc596b1f3db5878760e
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 1%

---


# Integración de formularios adaptables con bases de datos mediante Forms Portal {#submit-forms-to-database-using-forms-portal}

El servicio de conversión automatizada de Forms le permite convertir un formulario PDF no interactivo, un formulario Acro o un formulario PDF basado en XFA en un formulario adaptable. Al iniciar el proceso de conversión, tiene la opción de generar un formulario adaptable con o sin enlaces de datos.

Si selecciona generar un formulario adaptable sin enlaces de datos, puede integrar el formulario adaptable convertido con un modelo de datos de formulario, un esquema XML o un esquema JSON después de la conversión. Sin embargo, si se genera un formulario adaptable con enlaces de datos, el servicio de conversión asocia automáticamente los formularios adaptables con un esquema JSON y crea un enlace de datos entre los campos disponibles en el formulario adaptable y el esquema JSON. A continuación, puede integrar el formulario adaptable con una base de datos de su elección, rellenar los datos del formulario y enviarlos a la base de datos mediante Forms Portal.

En la siguiente figura se muestran las diferentes etapas de integración de un formulario adaptable convertido con una base de datos mediante Forms Portal:

![integración de bases de datos](assets/database_integration.gif)

En este artículo se describen las instrucciones paso a paso para ejecutar correctamente todas estas etapas de integración.

El ejemplo, que se describe en este artículo, es una implementación de referencia de servicios de metadatos y datos personalizados para integrar una página de Forms Portal con una base de datos. La base de datos utilizada en la implementación de muestra es MySQL 5.6.24. Sin embargo, puede integrar la página de Forms Portal con cualquier base de datos que desee.

## Requisitos previos {#pre-requisites}

* Configuración de una instancia de autor de AEM 6.4 o 6.5
* Instale el Service Pack [](https://helpx.adobe.com/es/experience-manager/aem-releases-updates.html) más reciente para su instancia de AEM
* Última versión del paquete del complemento AEM Forms
* Configure [Automated Forms Conversion service](configure-service.md)
* Configure una base de datos. La base de datos utilizada en la implementación de muestra es MySQL 5.6.24. Sin embargo, puede integrar el formulario adaptable convertido con cualquier base de datos que desee.

## Configurar la conexión entre AEM instancia y la base de datos {#set-up-connection-aem-instance-database}

La configuración de una conexión entre una instancia de AEM y una base de datos MYSQL consiste en:

* [Instalación de un paquete de conector MYSQL](#install-mysql-connector-java-file)

* [Creación de esquemas y tablas en la base de datos](#create-schema-and-tables-in-database)

* [Configuración de la configuración de conexión](#configure-connection-between-aem-instance-and-database)

* [Configuración y configuración del paquete de muestra para la integración con Forms Portal](#set-up-and-configure-sample)

### Instale el archivo mysql-Connector-java-5.1.39-bin.jar {#install-mysql-connector-java-file}

Realice los siguientes pasos, en todas las instancias de creación y publicación, para instalar el archivo mysql-Connector-java-5.1.39-bin.jar:

1. Vaya a http://[server]:[port]/system/console/depfinder y busque el paquete com.mysql.jdbc.
1. En la columna Exportado por, compruebe si el paquete lo exporta cualquier paquete. Proceda si el paquete no se exporta mediante ningún paquete.
1. Vaya a http://[server]:[port]/system/console/buncles y haga clic en **[!UICONTROL Install/Update]**.
1. Haga clic **[!UICONTROL Choose File]** y busque para seleccionar el archivo mysql-Connector-java-5.1.39-bin.jar. Además, seleccione **[!UICONTROL Start Bundle]** y **[!UICONTROL Refresh Packages]** casillas de verificación.
1. Haga clic en **[!UICONTROL Install]** o **[!UICONTROL Update]**. Una vez finalizado, reinicie el servidor.
1. (Solo Windows) Desactive el cortafuegos del sistema para su sistema operativo.

### Crear esquemas y tablas en la base de datos {#create-schema-and-tables-in-database}

Realice los siguientes pasos para crear esquemas y tablas en la base de datos:

1. Cree un esquema en la base de datos con la siguiente instrucción SQL:

   ```sql
   CREATE SCHEMA `formsportal` ;
   ```

   donde **formsportal** hace referencia al nombre del esquema.

1. Cree una tabla **de datos** en el esquema de la base de datos con la siguiente instrucción SQL:

   ```sql
    CREATE TABLE `data` (
        `owner` varchar(255) DEFAULT NULL,
        `data` longblob,
        `metadataId` varchar(45) DEFAULT NULL,
        `id` varchar(45) NOT NULL,
        PRIMARY KEY (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Cree una tabla de **metadatos** en el esquema de la base de datos con la siguiente instrucción SQL:

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

1. Cree una tabla **adicional de metadatos** en el esquema de la base de datos con la siguiente instrucción SQL:

   ```sql
   CREATE TABLE `additionalmetadatatable` (
       `value` text,
       `key` varchar(255) NOT NULL,
       `id` varchar(60) NOT NULL,
       PRIMARY KEY (`id`,`key`),
       CONSTRAINT ‘additionalmetadatatable_fk’ FOREIGN KEY (`id`) REFERENCES `metadata` (`id`) ON DELETE CASCADE
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Cree una tabla de **comentarios** en el esquema de la base de datos con la siguiente instrucción SQL:

   ```sql
   CREATE TABLE `commenttable` (
       `commentId` varchar(255) DEFAULT NULL,
       `comment` text DEFAULT NULL,
       `ID` varchar(255) DEFAULT NULL,
       `commentowner` varchar(255) DEFAULT NULL,
       `time` varchar(255) DEFAULT NULL);
   ```

### Configurar la conexión entre AEM instancia y la base de datos {#configure-connection-between-aem-instance-and-database}

Realice los siguientes pasos de configuración para crear una conexión entre AEM instancia y la base de datos MYSQL:

1. Vaya a AEM página de configuración de la consola web en *http://[host]:[port]/system/console/configMgr*.
1. Haga clic para abrir **[!UICONTROL Forms Portal Draft and Submission Configuration]** en modo de edición.
1. Especifique los valores de las propiedades como se describe en la tabla siguiente:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Propiedad</strong></th> 
    <th><strong>Descripción</strong></th>
    <th><strong>Value</strong></th> 
    </tr> 
    <tr> 
    <td><p>Servicio de datos de borrador de Forms Portal</p></td> 
    <td><p>Identificador del servicio de datos de borrador</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servicio de metadatos de borrador de Forms Portal</p></td> 
    <td><p>Identificador del servicio de metadatos de borrador</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servicio de envío de datos de Forms Portal</p></td> 
    <td><p>Identificador para enviar el servicio de datos</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servicio de envío de metadatos de Forms Portal</p></td> 
    <td><p>Identificador del servicio de metadatos de envío</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servicio de datos de firma pendiente de Forms Portal</p></td> 
    <td><p>Identificador del servicio de datos de firma pendiente</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servicio de metadatos de firma pendiente de Forms Portal</p></td> 
    <td><p>Identificador del servicio de metadatos Firma pendiente</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    </tbody> 
    </table>
1. Deje otras configuraciones tal cual y haga clic en **[!UICONTROL Save]**.
1. Busque y haga clic para abrir **[!UICONTROL Apache Sling Connection Pooled DataSource]** en modo de edición en la Configuración de la consola web. Especifique los valores de las propiedades como se describe en la tabla siguiente:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Propiedad</strong></th> 
    <th><strong>Value</strong></th> 
    </tr> 
    <tr> 
    <td><p>Nombre del origen de datos</p></td> 
    <td><p>Un nombre de fuente de datos para filtrar controladores del grupo de fuentes de datos. La implementación de ejemplo utiliza FormsPortal como nombre del origen de datos.</p></td>
    </tr>
    <tr> 
    <td><p>Clase de controlador JDBC</p></td> 
    <td><p>com.mysql.jdbc.Driver</p></td>
    </tr>
    <tr> 
    <td><p>URI de conexión JDBC</p></td> 
    <td><p>jdbc:mysql://[host]:[puerto]/[nombre_esquema]</p></td>
    </tr>
    <tr> 
    <td><p>Nombre de usuario</p></td> 
    <td><p>Un nombre de usuario para autenticar y realizar acciones en tablas de base de datos</p></td>
    </tr>
    <tr> 
    <td><p>Contraseña</p></td> 
    <td><p>Contraseña asociada al nombre de usuario</p></td>
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
    <td><p>Máximo de conexiones inactivas</p></td> 
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
    <td><p>Activados</p></td>
    </tr>
     <tr> 
    <td><p>Probar mientras está inactivo</p></td> 
    <td><p>Activados</p></td>
    </tr>
     <tr> 
    <td><p>Consulta de validación</p></td> 
    <td><p>Los valores de ejemplo son SELECT 1(mysql), select 1 from dual(oracle), SELECT 1(MS Sql Server) (validationQuery)</p></td>
    </tr>
     <tr> 
    <td><p>Tiempo de espera de Consulta de validación</p></td> 
    <td><p>10 000</p></td>
    </tr>
    </tbody> 
    </table>

### Configurar y configurar el ejemplo {#set-up-and-configure-sample}

Realice los siguientes pasos, en todas las instancias de creación y publicación, para instalar y configurar el ejemplo:

1. Descargue el siguiente paquete **aem-fp-db-integration-sample-pkg-6.1.2.zip** en el sistema de archivos.

   [Obtener archivo](assets/aem-fp-db-integration-sample-pkg-6.1.2.zip)

1. Vaya a AEM administrador de paquetes en *http://[host]:[port]/crx/packmgr/*.
1. Haga clic **[!UICONTROL Upload Package]**.
1. Busque y seleccione el paquete **aem-fp-db-integration-sample-pkg-6.1.2.zip** y haga clic en **[!UICONTROL OK]**.
1. Haga clic **[!UICONTROL Install]** junto al paquete para instalar el paquete.

## Configuración del formulario adaptable convertido para la integración con Forms Portal {#configure-converted-adaptive-form-for-forms-portal-integration}

Siga estos pasos para activar el envío de formularios adaptables mediante la página de Forms Portal:
1. [Ejecute la conversión](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) para convertir un formulario de origen en un formulario adaptable.
1. Abra el formulario adaptable en modo de edición.
1. Puntee en Contenedor de formulario y seleccione Configurar ![formulario](assets/configure-adaptive-form.png)adaptable.
1. En la **[!UICONTROL Submission]** sección, seleccione **[!UICONTROL Forms Portal Submit Action]** en la lista **[!UICONTROL Submit Action]** desplegable.
1. Toque ![Guardar directiva](assets/edit_template_done.png) de plantilla para guardar la configuración.

## Crear y configurar la página de Forms Portal {#create-configure-forms-portal-page}

Siga estos pasos para crear una página de Forms Portal y configurarla de modo que pueda enviar formularios adaptables con esta página:

1. Inicie sesión en la instancia de creación de AEM y toque **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Sites]**.
1. Seleccione la ubicación en la que desea guardar la nueva página de Forms Portal y toque **[!UICONTROL Create]** > **[!UICONTROL Page]**.
1. Seleccione la plantilla de la página, toque **[!UICONTROL Next]**, especifique un título para la página y toque **[!UICONTROL Create]**.
1. Toque **[!UICONTROL Edit]** para configurar la página.
1. En el encabezado de página, toque ![Editar plantilla](assets/edit_template_sites.png) > **[!UICONTROL Edit Template]** para abrir la plantilla de la página.
1. Toque Diseño Contenedor y ![Editar directiva](assets/edit_template_policy.png)de plantilla. En la **[!UICONTROL Allowed Components]** ficha, active las opciones **[!UICONTROL Document Services]** y **[!UICONTROL Document Services Predicates]** y toque ![Guardar directiva](assets/edit_template_done.png)de plantilla.
1. Inserte **[!UICONTROL Search & Lister]** un componente en la página. Como resultado, todos los formularios adaptables existentes disponibles en la instancia de AEM se muestran en la página.
1. Inserte **[!UICONTROL Drafts & Submissions]** un componente en la página. En la página de Forms Portal aparecen dos fichas **[!UICONTROL Draft Forms]** y **[!UICONTROL Submitted Forms]**. La **[!UICONTROL Draft Forms]** ficha también muestra el formulario adaptable convertido generado mediante los pasos mencionados en [Configurar el formulario adaptable convertido para la integración con Forms Portal](#configure-converted-adaptive-form-for-forms-portal-integration)

1. Toque **[!UICONTROL Preview]**, toque el formulario adaptable convertido, especifique los valores de los campos del formulario adaptable y envíelo. Los valores especificados para los campos de formulario adaptables se envían a la base de datos integrada.
