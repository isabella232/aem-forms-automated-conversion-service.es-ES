---
title: Flujos de trabajo de relleno automático recomendados y envío basados en fuentes de datos para formularios adaptables
seo-title: Prefill and submit options for adaptive forms
description: Flujos de trabajo de relleno automático y envío basados en fuentes de datos para formularios adaptables generados mediante el servicio de conversión automatizada de formularios.
seo-description: Data-source based prefill and submit workflows for adaptive forms generated using Automated Forms Conversion Service.
uuid: 91409a82-141c-4233-82b1-1539a0b250f8
contentOwner: khsingh
topic-tags: forms
discoiquuid: cad34fff-7f9f-4a27-8b5c-d0a523903eec
privatebeta: true
exl-id: 5deef8f5-5098-47c1-b696-b2db59e92931
source-git-commit: 1a3f79925f25dcc7dbe007f6e634f6e3a742bf72
workflow-type: ht
source-wordcount: '2437'
ht-degree: 100%

---

# Flujos de trabajo de relleno automático recomendados y envío basados en fuentes de datos para formularios adaptables {#recommended-data-source-btased-prefill-and-submit-workflows-for-adaptive-forms}

Puede utilizar cualquiera de las siguientes fuentes de datos con formularios adaptables convertidos mediante el servicio de conversión automatizada de formularios:

* Modelo de datos de formulario, OData o cualquier otro servicio de terceros
* Esquema JSON
* Esquema XSD

En función de la fuente de datos, puede optar por generar un formulario adaptable con o sin un modelo de datos.

En este artículo se describen los flujos de trabajo recomendados para rellenar automáticamente los valores de campo y las opciones de envío después de seleccionar una fuente de datos y generar un formulario adaptable mediante el servicio de conversión.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Fuente de datos</strong></th> 
   <th><strong>Flujo de trabajo recomendado</strong></th> 
  </tr> 
  <tr> 
   <td><p>Modelo de datos de formulario, OData o cualquier otro servicio de terceros</p></td> 
   <td> 
    <p><strong>Opción 1</strong>: se selecciona el modelo de datos de formulario, OData o cualquier otro servicio de terceros como fuente de datos. Puede <a href="#generate-adaptive-forms-with-no-data-binding">generar un formulario adaptable sin enlace de datos</a> mediante el servicio de conversión automática de formularios. Los campos de formulario adaptables se vinculan manualmente a las entidades del modelo de datos de formulario y se utiliza la opción Servicio de relleno automático del modelo de datos de formulario para rellenar automáticamente los valores de los campos. Para enviar el formulario adaptable se utiliza la opción Enviar con el modelo de datos de formulario.</p></td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
   <p><strong>Opción 2</strong>: seleccione el modelo de datos de formulario, OData o cualquier otro servicio de terceros como fuente de datos. Puede <a href="#generate-adaptive-forms-with-no-data-binding">generar un formulario adaptable sin enlace de datos</a> mediante el uso del servicio de conversión automática de formularios. Los campos de formulario adaptables se enlazan con el editor de reglas para rellenar automáticamente los valores de campo. Modifique los valores de los campos, si es necesario, y envíe datos al repositorio de crx.</p>
    </td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
    <p>Para obtener instrucciones paso a paso sobre la ejecución de estos flujos de trabajo, consulte <a href="#sqldatasource">Utilice la base de datos, OData o cualquier servicio de terceros como fuente de datos.</a></p> </td> 
  </tr>
  <tr>
  <td><p>Esquema JSON</p></td> 
   <td> 
    <p>El esquema JSON se selecciona como fuente de datos. En función de la fuente de datos seleccionada:</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>Opción 1</strong>: para <a href="#generate-adaptive-forms-with-no-data-binding">generar un formulario adaptable sin enlace de datos</a> mediante el uso del servicio de conversión automática de formularios y la configuración del esquema JSON como fuente de datos. Los campos de formulario adaptables se enlazan manualmente al esquema JSON y <a href="https://helpx.adobe.com/es/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">usar cualquiera de los protocolos admitidos</a> para rellenar automáticamente los valores de campo. Modifique los valores de los campos, si es necesario, y envíe datos al repositorio de crx.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>Para obtener instrucciones paso a paso para ejecutar los flujos de trabajo, consulte <a href="#jsondatasource">Utilización del esquema JSON como fuente de datos.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>Opción 2</strong>: puede <a href="#generate-adaptive-forms-with-json-binding">generar un formulario adaptable con enlace de datos JSON</a> mediante el uso del servicio de conversión automática de formularios. El servicio de relleno automático y el envío de formularios funcionan sin problemas. No necesita ningún paso de configuración.</p> </td> 
  </tr>
   <tr>
  <td></td> 
   <td> 
    <p>Para obtener instrucciones paso a paso para ejecutar los flujos de trabajo, consulte <a href="#jsonwithdatabinding">Utilización del esquema JSON como fuente de datos.</a></p> </td> 
  </tr>
  <tr>
  <td><p>Esquema XSD</p></td> 
   <td> 
    <p>El esquema XSD se selecciona como fuente de datos. En función de la fuente de datos seleccionada, puede <a href="#generate-adaptive-forms-with-no-data-binding">generar un formulario adaptable sin enlace de datos</a> mediante el uso del servicio de conversión automatizada de formularios y la configuración del esquema XSD como fuente de datos. Los campos de formulario adaptables se enlazan manualmente al esquema XSD y <a href="https://helpx.adobe.com/es/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">usar cualquiera de los protocolos admitidos</a> para rellenar automáticamente los valores de campo. Modifique los valores de los campos, si es necesario, y envíe datos al repositorio de crx.</p>
    </td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>Para obtener instrucciones paso a paso para ejecutar los flujos de trabajo, consulte <a href="#xsddatasource">Utilización del esquema XSD como fuente de datos.</a></p>
    </td> 
  </tr>
 </tbody> 
</table>


Para obtener más información sobre el servicio de conversión automatizada de formulario, consulte los siguientes artículos:

* [Introducción al servicio de conversión automatizada de formularios](introduction.md)
* [Configurar el servicio de conversión automatizada de formularios](configure-service.md)
* [Conversión de formularios impresos en formularios adaptables](convert-existing-forms-to-adaptive-forms.md)
* [Revisar y corregir formularios convertidos](review-correct-ui-edited.md)

La información proporcionada en este artículo se basa en la suposición de que cualquiera que la lea tiene conocimientos básicos sobre los conceptos de formularios adaptables.

## Requisitos previos {#pre-requisites}

* Configurar una [instancia de autor de AEM](https://helpx.adobe.com/es/experience-manager/6-5/sites/deploying/using/deploy.html).
* Configurar el [servicio de conversión automatizada de formularios en la instancia de autor de AEM](configure-service.md).

## Formulario adaptable de ejemplo {#sample-adaptive-form}

Para ejecutar los casos de uso con el fin de rellenar automáticamente los valores de campo en un formulario adaptable y enviarlos a la fuente de datos, descargue el siguiente archivo PDF de ejemplo.

Formulario de solicitud de préstamo de ejemplo

[Obtener archivo](assets/sample_loan_application_form.pdf)

El archivo PDF sirve como entrada al servicio de conversión automatizada de formularios. El servicio convierte este archivo en un formulario adaptable. La siguiente imagen muestra la aplicación de un préstamo de ejemplo en formato PDF.

![formulario de solicitud de préstamo de ejemplo](assets/sample_form_new.png)

## Preparación de datos para el modelo de formulario {#prepare-data-for-form-model}

La integración de datos de AEM Forms le permite configurar y conectarse a fuentes de datos diferentes. Después de generar un formulario adaptable mediante el proceso de conversión, puede definir el modelo de formulario basado en un modelo de datos de formulario, XSD o un esquema JSON. Puede utilizar una base de datos, Microsoft Dynamics o cualquier otro servicio de terceros para crear un modelo de datos de formulario.

Este tutorial utiliza la base de datos MySQL como fuente para crear un modelo de datos de formulario. Cree un esquema de **aplicación de préstamo** en la base de datos y añada un **solicitante** al esquema en función de los campos disponibles en el formulario adaptable.

![Datos de muestra MySQL](assets/sample_data_mysql.png)

Puede utilizar la siguiente sentencia DDL para crear la tabla **solicitante** en la base de datos.

```sql
CREATE TABLE `applicant` (
   `name` varchar(45) DEFAULT NULL,
   `address` varchar(45) DEFAULT NULL,
   `phonenumber` int(11) NOT NULL,
   `email` varchar(45) DEFAULT NULL,
   `occupation` varchar(45) DEFAULT NULL,
   `annualsalary` varchar(45) DEFAULT NULL,
   `familymembers` int(11) DEFAULT NULL,
   PRIMARY KEY (`phonenumber`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

Si utiliza un esquema XSD como modelo de formulario para ejecutar los casos de uso, cree un archivo XSD con el siguiente texto:

```xml
<?xml version="1.0" encoding="utf-8" ?>
    <xs:schema targetNamespace="http://adobe.com/sample.xsd"
                    xmlns="http://adobe.com/sample.xsd"
                    xmlns:xs="http://www.w3.org/2001/XMLSchema">

<xs:element name="sample" type="SampleType"/>

  <xs:complexType name="SampleType">
    <xs:sequence>
      <xs:element name="name" type="xs:string"/>
   <xs:element name="address" type="xs:string"/>
   <xs:element name="phonenumber" type="xs:int"/>
   <xs:element name="email" type="xs:string"/>
   <xs:element name="occupation" type="xs:string"/>
   <xs:element name="annualsalary" type="xs:string"/>
   <xs:element name="familymembers" type="xs:string"/>
 </xs:sequence>
  </xs:complexType>

  </xs:schema>
```

O descargue el esquema XSD en el sistema de archivos local.

Esquema XSD de aplicación de préstamo de muestra

[Obtener archivo](assets/loanapplication.xsd)

Para obtener más información sobre el uso del esquema XSD como modelo de formulario en formularios adaptables, consulte [Creación de formularios adaptables con esquema XML](https://helpx.adobe.com/es/experience-manager/6-5/forms/using/adaptive-form-xml-schema-form-model.html).

Si utiliza un esquema JSON como modelo de formulario para ejecutar los casos de uso, cree un archivo JSON con el siguiente texto:

```JSON
{
    "$schema": "http://json-schema.org/draft-04/schema#",
    "definitions": {
        "loanapplication": {
            "type": "object",
            "properties": {
                "name": {
                    "type": "string"
                },
                "address": {
                    "type": "string"
                },
    "phonenumber": {
                    "type": "number"
                },
    "email": {
                    "type": "string"
                },
    "occupation": {
                    "type": "string"
                },
    "annualsalary": {
                    "type": "string"
                },
    "familymembers": {
                    "type": "number"
                }
            }
        }
 },
 "type": "object",
    "properties": {
        "employee": {
            "$ref": "#/definitions/loanapplication"
        }
    }
}
```

O descargue el esquema JSON en el sistema de archivos local.

Esquema JSON de aplicación de préstamo de muestra

[Obtener archivo](assets/demo_schema.json)

Para obtener más información sobre el uso del esquema JSON como modelo de formulario en formularios adaptables, consulte [Creación de formularios adaptables mediante el esquema JSON](https://helpx.adobe.com/es/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html).

## Generar formularios adaptables sin enlace de datos {#generate-adaptive-forms-with-no-data-binding}

Utilice el [servicio de conversión automatizada de formularios para convertir](convert-existing-forms-to-adaptive-forms.md) el [formulario de solicitud de préstamo de ejemplo](#sample-adaptive-form) a un formulario adaptable sin enlace de datos. Asegúrese de seleccionar la casilla **[!UICONTROL Generate adaptive form(s) without data bindings]** para generar el formulario adaptable sin enlace de datos.

![Formulario adaptable sin enlace de datos](assets/generate_af_without_binding.png)

Después de generar un formulario adaptable sin enlace de datos, seleccione una fuente de datos para el formulario adaptable:

* [Base de datos, OData o cualquier servicio de terceros](#sqldatasource)
* [Esquema JSON](#jsondatasource)
* [Esquema XSD](#xsddatasource)

>[!NOTE]
> Si el formulario adaptable que convierte mediante el servicio de conversión automatizada de formularios contiene varios campos con el mismo nombre, asegúrese de que dichos campos estén enlazados a entidades de la fuente de datos para evitar una posible pérdida de datos durante el envío.

### Utilizar base de datos, OData o cualquier servicio de terceros como fuente de datos {#sqldatasource}

Caso de uso: puede generar un formulario adaptable sin enlace de datos utilizando el servicio de conversión automatizada de formularios y configurar la base de datos MySQL como fuente de datos. Los campos de formulario adaptables se enlazan manualmente a las entidades del modelo de datos de formulario y se usa la opción **[!UICONTROL Form Data Model Prefill Service]** para rellenar automáticamente los valores de campo. Utilice la opción **[!UICONTROL Submit using Form Data Model]** para enviar el formulario adaptable.

Antes de ejecutar el caso de uso:

* [Configure la base de datos MySQL como fuente de datos ](https://helpx.adobe.com/es/experience-manager/6-5/forms/using/configure-data-sources.html#configurerelationaldatabase)
* [Cree un modelo de datos de formulario](https://helpx.adobe.com/es/experience-manager/6-5/forms/using/work-with-form-data-model.html)

En función del caso de uso, cree el modelo de datos de formulario **aplicación de préstamo** y enlace el argumento de servicio de lectura al valor **[!UICONTROL Literal]**. El valor literal del número de teléfono debe ser de uno de los registros configurados en el esquema **solicitante** de la base de datos MySQL. Los servicios utilizan el valor como argumento para recuperar detalles de la fuente de datos. También puede seleccionar el [Atributo de perfil de usuario o atributo de solicitud](https://helpx.adobe.com/es/experience-manager/6-5/forms/using/work-with-form-data-model.html#bindargument) de la lista desplegable **[!UICONTROL Binding To]**.

![Configurar un modelo de datos de formulario](assets/configure_model_object.png)

>[!NOTE]
>
>Asegúrese de agregar los servicios **get** y **insert** al modelo de datos de formulario, configurar y probar los servicios antes de ejecutar el caso de uso.

Siga estos pasos:

1. Seleccione el **formulario de solicitud de préstamo de ejemplo** convertido disponible en la carpeta **[!UICONTROL output]** y toque **[!UICONTROL Properties]**.
1. Desde la pestaña **[!UICONTROL Form Model]**, seleccione **[!UICONTROL Form Data Model]** desde la lista desplegable **[!UICONTROL Select From]** y pulse **[!UICONTROL Select Form Data Model]** para seleccionar el modelo de datos del formulario **aplicación de préstamo**. Toque **[!UICONTROL Save & Close]** para guardar el formulario.
1. Seleccione el **formulario de solicitud de préstamo de ejemplo** y toque **[!UICONTROL Edit]**.
1. En la pestaña **[!UICONTROL Content]**, pulse el icono configurar:

   ![configurar el contenedor de formulario](assets/configure_form_container.png)

   1. En la sección **[!UICONTROL Basic]**, elija **[!UICONTROL Form Data Model Prefill service]** desde la lista desplegable **[!UICONTROL Prefill Service]**.

   1. En la sección **[!UICONTROL Submission]**, seleccione **[!UICONTROL Submit using Form Data Model]** desde la **[!UICONTROL Submit Action]** lista desplegable.

   1. Seleccione el modelo de datos con el campo **[!UICONTROL Data Model to submit]**.
   1. Pulse ![done_icon](assets/save_icon.svg) para guardar las propiedades.

1. Pulse el cuadro de texto Nombre del solicitante y seleccione ![icono de configuración](assets/configure_icon.svg) (Configurar).

   1. En el campo Referencia de enlace, seleccione **Solicitante** > **Nombre** y presione ![icono Listo](assets/save_icon.svg) para guardar las propiedades. Del mismo modo, cree un enlace de datos para los campos **Dirección**, **Número de teléfono**, **Correo electrónico**, **Ocupación**, **Salario anual (en dólares)** y **cantidad de familiares dependientes** con las entidades del modelo de datos de formulario.

   ![Enlazar referencias](assets/bind_references.png)

1. Toque **[!UICONTROL Preview]** para ver los valores de campo de formulario adaptable rellenados previamente de forma automática.
1. Modifique los valores de los campos si es necesario y envíe el formulario adaptable. Los valores de campo se envían a la base de datos MySQL. Puede actualizar la tabla **solicitante** para ver los valores actualizados de la tabla.

**Caso de uso:** puede generar un formulario adaptable sin enlace de datos utilizando el Servicio de conversión automatizada de formularios y configurar la base de datos MySQL como la fuente de datos. Los campos de formulario adaptables se enlazan con el editor de reglas para rellenar automáticamente los valores de campo. Modifique los valores de los campos, si es necesario, y envíe datos al repositorio de crx.

Siga estos pasos para utilizar el [editor de reglas](https://helpx.adobe.com/es/experience-manager/6-5/forms/using/rule-editor.html) para invocar el servicio del modelo de datos de formulario para enlazar campos y rellenar automáticamente los valores en un formulario adaptable.

1. Seleccione el **formulario de solicitud de préstamo de ejemplo** en la carpeta **[!UICONTROL output]** y toque **[!UICONTROL Edit]**.
1. En la pestaña **[!UICONTROL Content]**, pulse el icono configurar:

   ![configurar contenedor de formulario](assets/configure_form_container.png)

   En la sección **[!UICONTROL Basic]**, elija **[!UICONTROL Form Data Model Prefill service]** desde la lista desplegable **[!UICONTROL Prefill Service]**.

1. Toque el cuadro de texto **[!UICONTROL Applicant Name]** y elija **[!UICONTROL Edit Rules]**.

   ![Editar reglas para crear enlaces de datos](assets/edit_rules_bind_reference.png)

1. Seleccione **[!UICONTROL Create]** en la página Editor de reglas.
1. En la página **[!UICONTROL Rule Editor]**:

   1. Seleccione un estado para el cuadro de texto Nombre del solicitante. Por ejemplo, **[!UICONTROL is initialized]**, lo que resulta en la ejecución de la condición **[!UICONTROL Then]** cuando se procesa el formulario en el modo **[!UICONTROL Preview]**.

   1. En la sección **[!UICONTROL Then]**, elija **[!UICONTROL Invoke Service]** de la lista desplegable **[!UICONTROL Select Action]**. Todos los servicios de la instancia de formularios se muestran en la lista desplegable.

   1. Seleccione un servicio **[!UICONTROL Get]** desde la sección que enumera los modelos de datos de formulario. Se muestra el campo Entrada **númerodeteléfono**, que es la clave principal definida para el modelo de datos **solicitante**. El sistema recupera y rellena automáticamente los valores del formulario adaptable de los campos de la sección Salida basándose en este campo.

   1. Cree un enlace para los campos de formulario adaptables con las entidades del modelo de datos de formulario utilizando la sección Salida. Por ejemplo, enlace el campo del formulario adaptable **[!UICONTROL Applicant Name]** con la entidad **nombre**.

   1. Toque **[!UICONTROL Done]**. Toque **[!UICONTROL Done]** de nuevo en la página Editor de reglas.

   ![Editor de reglas para enlazar referencias](assets/rule_editor_bind_references.png)

1. Toque **[!UICONTROL Preview]** para ver los valores de campo de formulario adaptable rellenados de forma automática previamente.

   >[!NOTE]
   >
   >Asegúrese de que la propiedad **[!UICONTROL Return Array]** se desactive para la propiedad del servicio **GET** en el modelo de datos de formulario asociado al formulario adaptable.

1. Modifique los valores de los campos si es necesario y envíe el formulario adaptable. Los datos enviados están disponibles en la siguiente ubicación del repositorio crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### Usar el esquema JSON como fuente de datos {#jsondatasource}

**Caso de uso:** puede generar un formulario adaptable sin enlace de datos mediante el servicio de conversión automatizada de formularios y configurar el esquema JSON como fuente de datos. Los campos del formulario adaptable se enlazan manualmente al esquema JSON y se utiliza la opción **Vista previa con los datos** para rellenar automáticamente los valores del campo. Modifique los valores de los campos, si es necesario, y envíe datos al repositorio de crx.

Antes de ejecutar el caso de uso, asegúrese de lo siguiente:

* [un esquema JSON válido que cumpla la estructura del esquema JSON](#prepare-data-for-form-model)
* [un formulario adaptable sin enlace de datos](#generate-adaptive-forms-with-no-data-binding)

Siga estos pasos:

1. Seleccione el **formulario de solicitud de préstamo de ejemplo** convertido disponible en la carpeta de **Salida** y toque **[!UICONTROL Properties]**.
1. Toque la pestaña **[!UICONTROL Form Model]**, seleccione **[!UICONTROL Schema]** de la lista desplegable **[!UICONTROL Select From]** y pulse **[!UICONTROL Select Schema]** para cargar el esquema **JSON de demo.schema** guardado en el sistema de archivos local. Toque **[!UICONTROL Save & Close]** para guardar el formulario.
1. Seleccione el **formulario de solicitud de préstamo de ejemplo** y toque **[!UICONTROL Edit]**.
1. Pulse el cuadro de texto Nombre del solicitante y seleccione ![icono de configuración](assets/configure_icon.svg) (Configurar).

   En el campo Referencia de enlace, seleccione **Solicitante** > **Nombre** y presione ![icono Listo](assets/save_icon.svg) para guardar las propiedades. Del mismo modo, cree un enlace de datos para los campos **Dirección**, **Número de teléfono**, **Correo electrónico**, **Ocupación**, **Salario anual (en dólares)** y **cantidad de familiares dependientes** con las entidades del esquema JSON.

1. Seleccione nuevamente el **formulario de solicitud de préstamo de ejemplo** convertido disponible en la carpeta **[!UICONTROL output]** y presione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Descargar archivo de datos de ejemplo</br>

   [Obtener archivo](assets/json_data_file.txt)</br>

1. Modifique los valores de los campos si es necesario y envíe el formulario adaptable. Los datos enviados están disponibles en la siguiente ubicación del repositorio crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### Utilizar el esquema XSD como fuente de datos {#xsddatasource}

**Caso de uso:** puede generar un formulario adaptable sin enlace de datos utilizando el servicio de conversión automatizada de formularios y configurar el esquema XSD como fuente de datos. Los campos de formulario adaptables se enlazan manualmente al esquema XSD y se utiliza la variable **Vista previa con datos** para rellenar automáticamente los valores de campo. Modifique los valores de los campos, si es necesario, y envíe datos al repositorio de crx.

Antes de ejecutar el caso de uso, asegúrese de lo siguiente:

* [un esquema XSD válido compatible con la estructura del esquema XML](#prepare-data-for-form-model)
* [un formulario adaptable sin enlace de datos](#generate-adaptive-forms-with-no-data-binding)

Siga estos pasos:

1. Seleccione el **formulario de solicitud de préstamo de ejemplo** convertido disponible en la carpeta **[!UICONTROL output]** y toque **[!UICONTROL Properties]**.
1. Toque la pestaña **[!UICONTROL Form Model]**, seleccione **[!UICONTROL Schema]** de la lista desplegable **[!UICONTROL Select From]** y pulse **[!UICONTROL Select Schema]** para cargar el esquema XSD **aplicación de préstamo** guardado en el sistema de archivos local. Seleccione el elemento raíz para el esquema XSD y pulse **[!UICONTROL Save & Close]** para guardar el formulario.
1. Seleccione el **formulario de solicitud de préstamo de ejemplo** y toque **[!UICONTROL Edit]**.
1. Pulse el cuadro de texto Nombre del solicitante y seleccione ![icono de configuración](assets/configure_icon.svg) (Configurar).
En el campo Referencia de enlace, seleccione **Solicitante** > **Nombre** y presione ![icono Listo](assets/save_icon.svg) para guardar las propiedades. Del mismo modo, cree un enlace de datos para los campos **Dirección**, **Número de teléfono**, **Correo electrónico**, **Ocupación**, **Salario anual (en dólares)** y **cantidad de familiares dependientes** con las entidades de esquema XSD.

1. Seleccione nuevamente el **formulario de solicitud de préstamo de ejemplo** convertido disponible en la carpeta **salida** y presione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Descargar archivo de datos de ejemplo</br>

   [Obtener archivo](assets/loan-application-data-xml-data.zip)</br>


1. Modifique los valores de los campos si es necesario y envíe el formulario adaptable. Los datos enviados están disponibles en la siguiente ubicación del repositorio crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## Generación de formularios adaptables con enlace JSON {#generate-adaptive-forms-with-json-binding}

Utilice el [servicio de conversión automatizada de formularios para convertir](convert-existing-forms-to-adaptive-forms.md) el [formulario de solicitud de préstamo de ejemplo](#sample-adaptive-form) a un formulario adaptable con enlace de datos. Asegúrese de no seleccionar la casilla **[!UICONTROL Generate adaptive form(s) without data bindings]** para generar el formulario adaptable.

![Formulario adaptable con enlace JSON](assets/generate_af_with_data_bindings.png)

### Usar el esquema JSON como fuente de datos {#jsonwithdatabinding}

**Caso de uso:** puede generar un formulario adaptable con enlace de datos JSON mediante el servicio de conversión automatizada de formularios. El servicio de relleno automático y el envío de formularios funcionan sin problemas. No necesita ningún paso de configuración.

Antes de ejecutar el caso de uso, asegúrese de que tiene [un formulario adaptable con enlace de datos](#generate-adaptive-forms-with-json-binding).

Siga estos pasos:

1. Seleccione el **formulario de solicitud de préstamo de ejemplo** convertido disponible en la carpeta **[!UICONTROL output]** de nuevo y presione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Descargar archivo de datos de ejemplo</br>

   [Obtener archivo](assets/loan_application_data_source_json_data_binding.txt)</br>

1. Modifique los valores de los campos si es necesario y envíe el formulario adaptable. Los datos enviados están disponibles en la siguiente ubicación del repositorio crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## Conversión de datos JSON del formulario adaptable enviado al formato XML {#convert-submitted-adaptive-form-data-to-xml}

Cuando se introducen valores en campos de formulario adaptables y se envían, los datos están disponibles en formato JSON en el repositorio crx. Puede convertir el formato de los datos JSON a XML con la API [org.apache.sling.commons.json.xml](https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString) o con el siguiente código de ejemplo:

```
import org.apache.sling.commons.json.JSONException;
import org.apache.sling.commons.json.JSONObject;
import org.apache.sling.commons.json.xml.XML;
 
public class ConversionUtils {
 
    public static String jsonToXML(String jsonString) throws JSONException {
        //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
        //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
        //Note: Need to extract boundData part before converting to XML
        return XML.toString(new JSONObject(jsonString));
    }
}
```
