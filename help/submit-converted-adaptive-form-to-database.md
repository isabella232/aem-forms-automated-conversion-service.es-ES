---
title: Enviar los formularios adaptables convertidos con un esquema JSON a la base de datos
description: Envíe los formularios adaptables convertidos con un esquema JSON a la base de datos creando un modelo de datos de formulario y haciendo referencia a él en un flujo de trabajo AEM.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: c552f4073ac88ca9016a746116a27a5898df7f7d
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 2%

---


# Integrar el formulario adaptable con la base de datos mediante el flujo de trabajo de AEM {#submit-forms-to-database-using-forms-portal}

El servicio de automated forms conversion permite convertir un formulario PDF no interactivo, un formulario Acro Form o un formulario PDF basado en XFA en un formulario adaptable. Al iniciar el proceso de conversión, tiene la opción de generar un formulario adaptable con o sin enlaces de datos.

Si selecciona generar un formulario adaptable sin enlaces de datos, puede integrar el formulario adaptable convertido con un modelo de datos de formulario, un esquema XML o un esquema JSON después de la conversión. Para el modelo de datos de formulario, es necesario enlazar manualmente los campos de formulario adaptables con el modelo de datos de formulario. Sin embargo, si se genera un formulario adaptable con enlaces de datos, el servicio de conversión asocia automáticamente los formularios adaptables con un esquema JSON y crea un enlace de datos entre los campos disponibles en el formulario adaptable y el esquema JSON. A continuación, puede integrar el formulario adaptable con una base de datos de su elección, rellenar los datos del formulario y enviarlos a la base de datos. Del mismo modo, tras una integración correcta con la base de datos, puede configurar los campos del formulario adaptable convertido para recuperar valores de la base de datos y rellenar previamente los campos del formulario adaptable.

En la siguiente figura se muestran las diferentes etapas de integración de un formulario adaptable convertido con una base de datos:

![integración de bases de datos](assets/integrate-adaptive-form-with-database.png)

En este artículo se describen las instrucciones paso a paso para ejecutar correctamente todas estas etapas de integración.

## Requisitos previos {#pre-requisites}

* Configuración de una instancia de autor de AEM 6.4 o 6.5
* Instale [Service Pack más reciente](https://helpx.adobe.com/es/experience-manager/aem-releases-updates.html) para su instancia de AEM
* Última versión del paquete del complemento AEM Forms
* Configurar [servicio de Automated forms conversion](configure-service.md)
* Configure una base de datos. La base de datos utilizada en la implementación de muestra es MySQL 5.6.24. Sin embargo, puede integrar el formulario adaptable convertido con cualquier base de datos que desee.

## Formulario adaptable de ejemplo {#sample-adaptive-form}

Para ejecutar el caso de uso para integrar formularios adaptables convertidos con la base de datos mediante un flujo de trabajo AEM, descargue el siguiente archivo PDF de ejemplo.

Puede descargar el formulario de contacto de ejemplo mediante:

[Obtener archivo](assets/sample_contact_us_form.pdf)

El archivo PDF sirve como entrada al servicio de Automated forms conversion. El servicio convierte este archivo en un formulario adaptable. La siguiente imagen muestra el formulario de contacto con nosotros en formato PDF.

![formulario de solicitud de préstamo de muestra](assets/sample_contact_us_form.png)

## Instale el archivo mysql-Connector-java-5.1.39-bin.jar {#install-mysql-connector-java-file}

Realice los siguientes pasos, en todas las instancias de creación y publicación, para instalar el archivo mysql-Connector-java-5.1.39-bin.jar:

1. Vaya a `http://server:port/system/console/depfinder` y busque el paquete com.mysql.jdbc.
1. En la columna Exportado por, compruebe si el paquete lo exporta cualquier paquete. Proceda si el paquete no se exporta mediante ningún paquete.
1. Vaya a `http://server:port/system/console/bundles` y haga clic en **[!UICONTROL Install/Update]**.
1. Haga clic en **[!UICONTROL Choose File]** y busque para seleccionar el archivo mysql-Connector-java-5.1.39-bin.jar. Además, seleccione las casillas de verificación **[!UICONTROL Start Bundle]** y **[!UICONTROL Refresh Packages]**.
1. Haga clic en **[!UICONTROL Install]** o **[!UICONTROL Update]**. Una vez finalizado, reinicie el servidor.
1. (Solo Windows) Desactive el cortafuegos del sistema para su sistema operativo.

## Preparar datos para el modelo de formulario {#prepare-data-for-form-model}

La integración de datos de AEM Forms le permite configurar y conectar fuentes de datos dispares. Después de generar un formulario adaptable mediante el proceso de conversión, puede definir el modelo de formulario basado en un modelo de datos de formulario, XSD o un esquema JSON. Puede utilizar una base de datos, Microsoft Dynamics o cualquier otro servicio de terceros para crear un modelo de datos de formulario.

Este tutorial utiliza la base de datos MySQL como origen para crear un modelo de datos de formulario. Cree un esquema en la base de datos y agregue la tabla **contactus** al esquema en función de los campos disponibles en el formulario adaptable.

![Datos de muestra mysql](assets/db_entries_sample_form.png)

Puede utilizar la siguiente instrucción DDL para crear la tabla **contactus** en la base de datos.

```sql
CREATE TABLE `contactus` (
   `name` varchar(45) NOT NULL,
   `email` varchar(45) NOT NULL,
   `phonenumber` varchar(10) DEFAULT NULL,
   `issuedesc` varchar(1000) DEFAULT NULL,
   PRIMARY KEY (`email`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

## Configurar la conexión entre AEM instancia y la base de datos {#configure-connection-between-aem-instance-and-database}

Realice los siguientes pasos de configuración para crear una conexión entre AEM instancia y la base de datos MYSQL:

1. Vaya a AEM página de configuración de la consola web en `http://server:port/system/console/configMgr`.
1. Busque y haga clic para abrir **[!UICONTROL Apache Sling Connection Pooled DataSource]** en modo de edición en la Configuración de la consola web. Especifique los valores de las propiedades como se describe en la tabla siguiente:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Propiedad</strong></th> 
    <th><strong>Value</strong></th> 
    </tr> 
    <tr> 
    <td><p>Nombre del origen de datos</p></td> 
    <td><p>Un nombre de fuente de datos para filtrar controladores del grupo de fuentes de datos.</p></td>
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

## Crear modelo de datos de formulario {#create-form-data-model}

Una vez que haya configurado MYSQL como el origen de datos, ejecute los siguientes pasos para crear un modelo de datos de formulario:

1. En AEM instancia de autor, vaya a **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]**.

1. Tocar **[!UICONTROL Create]** > **[!UICONTROL Form Data Model]**.

1. En el asistente **[!UICONTROL Create Form Data Model]**, especifique **workflow_submit** como nombre para el modelo de datos de formulario. Tocar **[!UICONTROL Next]**.

1. Seleccione el origen de datos MYSQL que configuró en la sección anterior y toque **[!UICONTROL Create]**.

1. Toque **[!UICONTROL Edit]** y expanda la fuente de datos enumerada en el panel izquierdo para seleccionar **servicios de contacto**, **[!UICONTROL get]** y **[!UICONTROL insert]** y toque **[!UICONTROL Add Selected]**.

   ![Datos de muestra mysql](assets/fdm_details_workfdlow_submit.png)

1. Seleccione el objeto del modelo de datos en el panel derecho y toque **[!UICONTROL Edit Properties]**. Seleccione **[!UICONTROL get]** y **[!UICONTROL insert]** en las listas desplegables **[!UICONTROL Read Service]** y **[!UICONTROL Write Service]**. Especifique los argumentos para el servicio de lectura y toque **[!UICONTROL Done]**.

1. En la ficha **[!UICONTROL Services]**, seleccione el servicio **[!UICONTROL get]** y toque **[!UICONTROL Edit Properties]**. Seleccione **[!UICONTROL Output Model Object]**, deshabilite el **[!UICONTROL Return array]** alternador y toque **[!UICONTROL Done]**.

1. Seleccione el servicio **[!UICONTROL Insert]** y toque **[!UICONTROL Edit Properties]**. Seleccione **[!UICONTROL Input Model Object]** y toque **[!UICONTROL Done]**.

1. Toque **[!UICONTROL Save]** para guardar el modelo de datos de formulario.

Puede descargar el modelo de datos de formulario de ejemplo mediante:

[Obtener archivo](assets/DownloadedFormsPackage_1497728018502500.zip)

## Generar formularios adaptables con enlace JSON {#generate-adaptive-forms-with-json-binding}

Utilice el servicio de Automated forms conversion [para convertir](convert-existing-forms-to-adaptive-forms.md) el [formulario de contacto](#sample-adaptive-form) en un formulario adaptable con enlace de datos. Asegúrese de no seleccionar la casilla de verificación **[!UICONTROL Generate adaptive form(s) without data bindings]** al generar el formulario adaptable.

![Formulario adaptable con enlace JSON](assets/generate_af_with_data_bindings.png)

Seleccione el formulario **Contacto** convertido disponible en la carpeta **[!UICONTROL output]** de **[!UICONTROL Forms & Documents]** y toque **[!UICONTROL Edit]**. Toque **[!UICONTROL Preview]**, introduzca valores en los campos del formulario adaptable y toque **[!UICONTROL Submit]**.

Inicie sesión en **crx-repository** y navegue a */content/forms/fp/admin/submit/data* para vista de los valores enviados en formato JSON. A continuación se muestran los datos de ejemplo en formato JSON al enviar el formulario adaptable **Contacto** convertido:

```json
{
  "afData": {
    "afUnboundData": {
      "data": {}
    },
    "afBoundData": {
      "data": {
        "name1": "Gloria",
        "email": "abc@xyz.com",
        "phone_number": "2346578965",
        "issue_description": "Test message"
      }
    },
    "afSubmissionInfo": {
      "computedMetaInfo": {},
      "stateOverrides": {},
      "signers": {},
      "afPath": "/content/dam/formsanddocuments/docs_conversion/output/sample_form_json",
      "afSubmissionTime": "20191204014007"
    }
  }
}
```

Ahora debe crear un modelo de flujo de trabajo que pueda procesar estos datos y enviarlos a la base de datos de MYSQL utilizando el modelo de datos de formulario que ha creado en las secciones anteriores.

## Crear un modelo de flujo de trabajo para procesar datos JSON {#create-workflow-model}

Siga los pasos siguientes para crear un modelo de flujo de trabajo y enviar los datos de formulario adaptables a la base de datos:

1. Abra la consola Modelos de flujo de trabajo. La dirección URL predeterminada es `https://server:port/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.

1. Seleccione **[!UICONTROL Create]** y luego **[!UICONTROL Create Model]**. Aparece el cuadro de diálogo **[!UICONTROL Add Workflow Model]**.

1. Introduzca **[!UICONTROL Title]** y **[!UICONTROL Name]** (opcional). Por ejemplo, **workflow_json_submit**. Toque **[!UICONTROL Done]** para crear el modelo.

1. Seleccione el modelo de flujo de trabajo y toque **[!UICONTROL Edit]** para abrirlo en modo de edición. Toque + y agregue **[!UICONTROL Invoke Form Data Model Service]** paso al modelo de flujo de trabajo.

1. Toque el paso **[!UICONTROL Invoke Form Data Model Service]** y toque ![Configurar](assets/configure_icon.png).

1. En la ficha **[!UICONTROL Form Data Model]**, seleccione el modelo de datos de formulario que ha creado en el campo **[!UICONTROL Form Data Model path]** y seleccione **[!UICONTROL insert]** en la lista desplegable **[!UICONTROL Service]**.

1. En la ficha **[!UICONTROL Input for Service]**, seleccione **[!UICONTROL Provide input data using literal, variable, or a workflow metadata, and a JSON file]** en la lista desplegable, seleccione la casilla **[!UICONTROL Map input fields from input JSON]**, seleccione **[!UICONTROL Relative to payload]** y proporcione **data.xml** como valor para el campo **[!UICONTROL Select input JSON document using]**.

1. En la sección **[!UICONTROL Service Arguments]**, proporcione los siguientes valores para los argumentos del modelo de datos de formulario:

   ![Invocar servicio de modelo de datos de formulario](assets/invoke_form_data_model_service.png)

   Observe que los campos del modelo de datos de formulario, por ejemplo, contactus dot name, están asignados a **afData.afBoundData.data.name1**, que hace referencia a los enlaces de esquema JSON para el formulario adaptable enviado.

## Configurar el envío de formularios adaptables {#configure-adaptive-form-submission}

Ejecute los siguientes pasos para enviar el formulario adaptable al modelo de flujo de trabajo que ha creado en la sección anterior:

1. Seleccione el formulario Contacto convertido disponible en la carpeta **[!UICONTROL output]** de **[!UICONTROL Forms & Documents]** y toque **[!UICONTROL Edit]**.

1. Abra las propiedades del formulario adaptable tocando **[!UICONTROL Form Container]** y, a continuación, tocando ![Configurar](assets/configure_icon.png).

1. En la sección **[!UICONTROL Submission]**, seleccione **[!UICONTROL Invoke an AEM workflow]** en la lista desplegable **[!UICONTROL Submit Action]**, seleccione el modelo de flujo de trabajo que creó en la sección anterior y especifique **data.xml** en el campo **[!UICONTROL Data File Path]**.

1. Toque ![Guardar](assets/save_icon.png) para guardar las propiedades.

1. Toque **[!UICONTROL Preview]**, introduzca valores en los campos del formulario adaptable y toque **[!UICONTROL Submit]**. Los valores enviados ahora se muestran en la tabla de la base de datos MYSQL en lugar de **crx-repository**.

## Configuración de formularios adaptables para rellenar previamente los valores de la base de datos

Ejecute los siguientes pasos para configurar el formulario adaptable para rellenar previamente los valores de la base de datos MYSQL en función de la clave principal definida en la tabla (correo electrónico en este caso):

1. Toque el campo **Correo electrónico** en el formulario adaptable y toque ![Editar regla](assets/edit-rules.png).

1. Toque **[!UICONTROL Create]** y seleccione **[!UICONTROL is changed]** en la lista desplegable **[!UICONTROL Select State]** en la sección **[!UICONTROL When]**.

1. En la sección **[!UICONTROL Then]**, seleccione **[!UICONTROL Invoke Service]** y **get** como servicio para el modelo de datos de formulario que ha creado en una sección anterior de este artículo.

1. Seleccione **Correo electrónico** en la sección **[!UICONTROL Input]** y los tres campos restantes del modelo de datos de formulario, **Nombre**, **Número de teléfono** y **Descripción del problema** en la sección **[!UICONTROL Output]**. Toque **[!UICONTROL Done]** para guardar la configuración.

   ![Configuración de la configuración previa de correo electrónico](assets/email_prefill_settings.png)

   Como resultado, según las entradas de correo electrónico existentes en la base de datos MYSQL, puede rellenar previamente los valores de los tres campos restantes en el modo **[!UICONTROL Preview]** del formulario adaptable. Por ejemplo, si especifica aya.tan@xyz.com en el campo **Correo electrónico** (según los datos existentes en la sección [Preparar modelo de datos de formulario](#prepare-data-for-form-model) de este artículo) y salir del campo, los tres campos restantes, **Nombre**, **Número de teléfono** y **Descripción del problema** se muestran automáticamente en el formulario adaptable.

Puede descargar el formulario adaptable convertido de ejemplo mediante:

[Obtener archivo](assets/DownloadedFormsPackage_1498226829041200.zip)
