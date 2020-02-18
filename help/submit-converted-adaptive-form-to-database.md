---
title: Enviar los formularios adaptables convertidos con un esquema JSON a la base de datos
description: Envíe los formularios adaptables convertidos con un esquema JSON a la base de datos creando un modelo de datos de formulario y haciendo referencia a él en un flujo de trabajo de AEM.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: b879a0ddecd5370c754dfe9e1bf33121dd5ecc97

---


# Integración de formularios adaptables con la base de datos mediante el flujo de trabajo de AEM {#submit-forms-to-database-using-forms-portal}

El servicio Conversión automatizada de formularios le permite convertir un formulario PDF no interactivo, un formulario Acro o un formulario PDF basado en XFA en un formulario adaptable. Al iniciar el proceso de conversión, tiene la opción de generar un formulario adaptable con o sin enlaces de datos.

Si selecciona generar un formulario adaptable sin enlaces de datos, puede integrar el formulario adaptable convertido con un modelo de datos de formulario, un esquema XML o un esquema JSON después de la conversión. Para el modelo de datos de formulario, es necesario enlazar manualmente los campos de formulario adaptables con el modelo de datos de formulario. Sin embargo, si genera un formulario adaptable con enlaces de datos, el servicio de conversión asocia automáticamente los formularios adaptables con un esquema JSON y crea un enlace de datos entre los campos disponibles en el formulario adaptable y el esquema JSON. A continuación, puede integrar el formulario adaptable con una base de datos de su elección, rellenar los datos del formulario y enviarlos a la base de datos. Del mismo modo, tras una integración correcta con la base de datos, puede configurar los campos del formulario adaptable convertido para recuperar valores de la base de datos y rellenar previamente los campos del formulario adaptable.

En la siguiente figura se muestran las diferentes etapas de integración de un formulario adaptable convertido con una base de datos:

![integración de bases de datos](assets/integrate-adaptive-form-with-database.png)

En este artículo se describen las instrucciones paso a paso para ejecutar correctamente todas estas etapas de integración.

## Requisitos previos {#pre-requisites}

* Instancia de autor de AEM 6.5 con el último Service Pack de AEM 6.5
* Última versión del paquete del complemento AEM Forms
* [Servicio de conversión automatizada de formularios](configure-service.md)
* Base de datos con la que realizar la integración. La base de datos utilizada en la implementación de muestra es MySQL 5.6.24. Sin embargo, puede integrar el formulario adaptable convertido con cualquier base de datos que desee.

## Formulario adaptable de ejemplo {#sample-adaptive-form}

Para ejecutar el caso de uso para integrar formularios adaptables convertidos con una base de datos mediante un flujo de trabajo de AEM, descargue el siguiente archivo PDF de ejemplo.

Puede descargar el formulario de contacto de ejemplo mediante:

[Obtener archivo](assets/sample_contact_us_form.pdf)

El archivo PDF sirve como entrada al servicio Conversión automatizada de formularios. El servicio convierte este archivo en un formulario adaptable. La siguiente imagen muestra el formulario de contacto con nosotros en formato PDF.

![formulario de solicitud de préstamo de muestra](assets/sample_contact_us_form.png)

## Instale el archivo mysql-Connector-java-5.1.39-bin.jar {#install-mysql-connector-java-file}

Realice los siguientes pasos, en todas las instancias de creación y publicación, para instalar el archivo mysql-Connector-java-5.1.39-bin.jar:

1. Busque `http://server:port/system/console/depfinder` y busque el paquete com.mysql.jdbc.
1. En la columna Exportado por, compruebe si el paquete lo exporta cualquier paquete. Proceda si el paquete no se exporta mediante ningún paquete.
1. Vaya a `http://server:port/system/console/bundles` y haga clic en **[!UICONTROL Install/Update]**.
1. Haga clic **[!UICONTROL Choose File]** y busque para seleccionar el archivo mysql-Connector-java-5.1.39-bin.jar. Además, seleccione **[!UICONTROL Start Bundle]** y **[!UICONTROL Refresh Packages]** casillas de verificación.
1. Haga clic en **[!UICONTROL Install]** o **[!UICONTROL Update]**. Una vez finalizado, reinicie el servidor.
1. (Solo Windows) Desactive el cortafuegos del sistema para su sistema operativo.

## Preparar datos para el modelo de formulario {#prepare-data-for-form-model}

La integración de datos de AEM Forms le permite configurar y conectar orígenes de datos dispares. Después de generar un formulario adaptable mediante el proceso de conversión, puede definir el modelo de formulario basado en un modelo de datos de formulario, XSD o un esquema JSON. Puede utilizar una base de datos, Microsoft Dynamics o cualquier otro servicio de terceros para crear un modelo de datos de formulario.

Este tutorial utiliza la base de datos MySQL como origen para crear un modelo de datos de formulario. Cree un esquema en la base de datos y agregue una tabla de **contactos** al esquema en función de los campos disponibles en el formulario adaptable.

![Datos de muestra mysql](assets/db_entries_sample_form.png)

Puede utilizar la siguiente instrucción DDL para crear la **tabla de contactus** en la base de datos.

```sql
CREATE TABLE `contactus` (
   `name` varchar(45) NOT NULL,
   `email` varchar(45) NOT NULL,
   `phonenumber` varchar(10) DEFAULT NULL,
   `issuedesc` varchar(1000) DEFAULT NULL,
   PRIMARY KEY (`email`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

## Configurar la conexión entre la instancia de AEM y la base de datos {#configure-connection-between-aem-instance-and-database}

Realice los siguientes pasos de configuración para crear una conexión entre la instancia de AEM y la base de datos MYSQL:

1. Vaya a la página de configuración de la consola web de AEM en `http://server:port/system/console/configMgr`.
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
    <td><p>Tiempo de espera de consulta de validación</p></td> 
    <td><p>10 000</p></td>
    </tr>
    </tbody> 
    </table>

## Create form data model {#create-form-data-model}

Una vez que haya configurado MYSQL como el origen de datos, ejecute los siguientes pasos para crear un modelo de datos de formulario:

1. En la instancia de creación de AEM, vaya a **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]**.

1. Tocar **[!UICONTROL Create]** > **[!UICONTROL Form Data Model]**.

1. En el **[!UICONTROL Create Form Data Model]** asistente, especifique **workflow_submit** como nombre para el modelo de datos de formulario. Tocar **[!UICONTROL Next]**.

1. Seleccione el origen de datos MYSQL que ha configurado en la sección anterior y toque **[!UICONTROL Create]**.

1. Toque **[!UICONTROL Edit]** y expanda el origen de datos que aparece en el panel izquierdo para seleccionar la tabla de **contacto** , **[!UICONTROL get]** y los servicios **[!UICONTROL insert]** , y toque **[!UICONTROL Add Selected]**.

   ![Datos de muestra mysql](assets/fdm_details_workfdlow_submit.png)

1. Seleccione el objeto del modelo de datos en el panel derecho y toque **[!UICONTROL Edit Properties]**. Seleccione **[!UICONTROL get]** y **[!UICONTROL insert]** en las listas **[!UICONTROL Read Service]** y **[!UICONTROL Write Service]** desplegables. Especifique los argumentos del servicio de lectura y toque **[!UICONTROL Done]**.

1. En la **[!UICONTROL Services]** ficha, seleccione el **[!UICONTROL get]** servicio y toque **[!UICONTROL Edit Properties]**. Seleccione el **[!UICONTROL Output Model Object]**, desactive el **[!UICONTROL Return array]** alternador y toque **[!UICONTROL Done]**.

1. Seleccione el **[!UICONTROL Insert]** servicio y toque **[!UICONTROL Edit Properties]**. Seleccione el **[!UICONTROL Input Model Object]** y toque **[!UICONTROL Done]**.

1. Toque **[!UICONTROL Save]** para guardar el modelo de datos de formulario.

Puede descargar el modelo de datos de formulario de ejemplo mediante:

[Obtener archivo](assets/DownloadedFormsPackage_1497728018502500.zip)

## Generar formularios adaptables con enlace JSON {#generate-adaptive-forms-with-json-binding}

Utilice el servicio Conversión de formularios [automatizados para convertir](convert-existing-forms-to-adaptive-forms.md) el formulario [](#sample-adaptive-form) Contactar con nosotros en un formulario adaptable con enlace de datos. Asegúrese de no seleccionar la **[!UICONTROL Generate adaptive form(s) without data bindings]** casilla de verificación al generar el formulario adaptable.

![Formulario adaptable con enlace JSON](assets/generate_af_with_data_bindings.png)

Seleccione el formulario **Contacto convertido disponible en la** carpeta de **[!UICONTROL output]** y toque **[!UICONTROL Forms & Documents]** **[!UICONTROL Edit]**. Toque **[!UICONTROL Preview]**, introduzca valores en los campos del formulario adaptable y toque **[!UICONTROL Submit]**.

Inicie sesión en **crx-repository** y navegue hasta */content/forms/fp/admin/submit/data* para ver los valores enviados en formato JSON. A continuación se muestran los datos de ejemplo en formato JSON al enviar el formulario adaptable **Contact Us** convertido:

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

1. Seleccione **[!UICONTROL Create]** y luego **[!UICONTROL Create Model]**. Aparecerá el **[!UICONTROL Add Workflow Model]** cuadro de diálogo.

1. Introduzca el valor **[!UICONTROL Title]** y **[!UICONTROL Name]** (opcional). Por ejemplo, **workflow_json_submit**. Toque **[!UICONTROL Done]** para crear el modelo.

1. Seleccione el modelo de flujo de trabajo y toque **[!UICONTROL Edit]** para abrirlo en modo de edición. Toque + y agregue **[!UICONTROL Invoke Form Data Model Service]** paso al modelo de flujo de trabajo.

1. Toque el **[!UICONTROL Invoke Form Data Model Service]** paso y toque ![Configurar](assets/configure_icon.png).

1. En la **[!UICONTROL Form Data Model]** ficha, seleccione el modelo de datos de formulario que ha creado en el **[!UICONTROL Form Data Model path]** campo y seleccione **[!UICONTROL insert]** en la lista **[!UICONTROL Service]** desplegable.

1. En la **[!UICONTROL Input for Service]** ficha, seleccione **[!UICONTROL Provide input data using literal, variable, or a workflow metadata, and a JSON file]** en la lista desplegable, seleccione **[!UICONTROL Map input fields from input JSON]** , seleccione **[!UICONTROL Relative to payload]** y proporcione **data.xml** como valor para el **[!UICONTROL Select input JSON document using]** campo.

1. En la **[!UICONTROL Service Arguments]** sección , proporcione los siguientes valores para los argumentos del modelo de datos de formulario:

   ![Invocar servicio de modelo de datos de formulario](assets/invoke_form_data_model_service.png)

   Observe que los campos del modelo de datos de formulario, por ejemplo, contactus dot name, están asignados a **afData.afBoundData.data.name1**, que hace referencia a los enlaces de esquema JSON para el formulario adaptable enviado.

## Configuración del envío de formularios adaptables {#configure-adaptive-form-submission}

Ejecute los siguientes pasos para enviar el formulario adaptable al modelo de flujo de trabajo que ha creado en la sección anterior:

1. Seleccione el formulario Contacto convertido disponible en la **[!UICONTROL output]** carpeta en **[!UICONTROL Forms & Documents]** y toque **[!UICONTROL Edit]**.

1. Abra las propiedades del formulario adaptable tocando **[!UICONTROL Form Container]** y luego ![Configurar](assets/configure_icon.png).

1. En la **[!UICONTROL Submission]** sección, seleccione **[!UICONTROL Invoke an AEM workflow]** en la lista **[!UICONTROL Submit Action]** desplegable, seleccione el modelo de flujo de trabajo que creó en la sección anterior y especifique **data.xml** en el **[!UICONTROL Data File Path]** campo.

1. Toque ![Guardar](assets/save_icon.png) para guardar las propiedades.

1. Toque **[!UICONTROL Preview]**, introduzca valores en los campos del formulario adaptable y toque **[!UICONTROL Submit]**. Los valores enviados ahora se muestran en la tabla de la base de datos MYSQL en lugar de **crx-repository**.

## Configuración de formularios adaptables para rellenar previamente los valores de la base de datos

Ejecute los siguientes pasos para configurar el formulario adaptable para rellenar previamente los valores de la base de datos MYSQL en función de la clave principal definida en la tabla (correo electrónico en este caso):

1. Puntee en el campo Correo **electrónico** del formulario adaptable y en ![Editar regla](assets/edit-rules.png).

1. Toque **[!UICONTROL Create]** y seleccione **[!UICONTROL is changed]** en la lista **[!UICONTROL Select State]** desplegable de la **[!UICONTROL When]** sección.

1. En la **[!UICONTROL Then]** sección , seleccione **[!UICONTROL Invoke Service]** y **obtenga** como servicio para el modelo de datos de formulario que ha creado en una sección anterior de este artículo.

1. Seleccione Correo **electrónico** en la **[!UICONTROL Input]** sección y los tres campos restantes del modelo de datos de formulario, **Nombre**, Número **de** teléfono y Descripción **de** problema en la **[!UICONTROL Output]** sección . Toque **[!UICONTROL Done]** para guardar la configuración.

   ![Configuración de la configuración previa de correo electrónico](assets/email_prefill_settings.png)

   Como resultado, según las entradas de correo electrónico existentes en la base de datos de MYSQL, puede rellenar previamente los valores de los tres campos restantes en el **[!UICONTROL Preview]** modo del formulario adaptable. Por ejemplo, si especifica aya.tan@xyz.com en el campo Correo **electrónico** (en función de los datos existentes en la sección [Preparar modelo](#prepare-data-for-form-model) de datos de formulario de este artículo) y salir del campo, los tres campos restantes, **Nombre**, Número **de** teléfono y Descripción **de** número, se mostrarán automáticamente en el formulario adaptable.

Puede descargar el formulario adaptable convertido de ejemplo mediante:

[Obtener archivo](assets/DownloadedFormsPackage_1498226829041200.zip)
