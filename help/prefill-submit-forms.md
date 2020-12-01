---
title: Flujos de trabajo recomendados de relleno y envío basados en fuentes de datos para formularios adaptables
seo-title: Rellenar y enviar opciones para formularios adaptables
description: Flujos de trabajo de envío y cumplimentación previa basados en fuentes de datos para formularios adaptables generados mediante el servicio de Automated forms conversion.
seo-description: Flujos de trabajo de envío y cumplimentación previa basados en fuentes de datos para formularios adaptables generados mediante el servicio de Automated forms conversion.
uuid: 91409a82-141c-4233-82b1-1539a0b250f8
contentOwner: khsingh
topic-tags: forms
discoiquuid: cad34fff-7f9f-4a27-8b5c-d0a523903eec
privatebeta: true
translation-type: tm+mt
source-git-commit: caccb547a5741eb0e70ddf75630a661f8fe75cb3
workflow-type: tm+mt
source-wordcount: '2459'
ht-degree: 1%

---


# Flujos de trabajo recomendados de relleno y envío basados en fuentes de datos para formularios adaptables {#recommended-data-source-btased-prefill-and-submit-workflows-for-adaptive-forms}

Puede utilizar cualquiera de los siguientes orígenes de datos con formularios adaptables convertidos mediante el servicio de Automated forms conversion:

* Modelo de datos de formulario, OData o cualquier otro servicio de terceros
* Esquema JSON
* Esquema XSD

En función del origen de datos, puede elegir generar un formulario adaptable con o sin un modelo de datos.

En este artículo se describen los flujos de trabajo recomendados para rellenar previamente los valores de campo y las opciones de envío después de seleccionar un origen de datos y generar un formulario adaptable mediante el servicio de conversión.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Fuente de datos</strong></th> 
   <th><strong>Flujo de trabajo recomendado</strong></th> 
  </tr> 
  <tr> 
   <td><p>Modelo de datos de formulario, OData o cualquier otro servicio de terceros</p></td> 
   <td> 
    <p><strong>Opción 1</strong>: Se selecciona modelo de datos de formulario, OData o cualquier otro servicio de terceros como origen de datos. <a href="#generate-adaptive-forms-with-no-data-binding">genera un formulario adaptable sin enlace de datos</a> mediante el servicio de Automated forms conversion. Los campos de formulario adaptables se enlazan manualmente a entidades del modelo de datos de formulario y se utiliza la opción Servicio de relleno previo del modelo de datos de formulario para rellenar previamente los valores de campo. La opción Enviar mediante el modelo de datos de formulario se utiliza para enviar el formulario adaptable.</p></td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
   <p><strong>Opción 2</strong>: Se selecciona modelo de datos de formulario, OData o cualquier otro servicio de terceros como origen de datos. <a href="#generate-adaptive-forms-with-no-data-binding">genera un formulario adaptable sin enlace de datos</a> mediante el servicio de Automated forms conversion. Los campos de formulario adaptables se enlazan mediante el editor de reglas para rellenar previamente los valores de campo. Si es necesario, modifique los valores de los campos y envíe los datos al repositorio crx.</p>
    </td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
    <p>Para obtener instrucciones paso a paso para ejecutar estos flujos de trabajo, consulte <a href="#sqldatasource">Utilizar la base de datos, OData o cualquier servicio de terceros como fuente de datos.</a></p> </td> 
  </tr>
  <tr>
  <td><p>Esquema JSON</p></td> 
   <td> 
    <p>Puede seleccionar esquema JSON como fuente de datos. En función de la fuente de datos seleccionada:</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>Opción 1</strong>: Puede  <a href="#generate-adaptive-forms-with-no-data-binding">generar un formulario adaptable sin </a> enlaces de datos mediante el servicio de Automated forms conversion y configurar el esquema JSON como el origen de datos. Los campos de formulario adaptables se enlazan manualmente al esquema JSON y <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">se utiliza cualquiera de los protocolos admitidos</a> para rellenar previamente los valores de campo. Si es necesario, modifique los valores de los campos y envíe los datos al repositorio crx.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>Para obtener instrucciones paso a paso para ejecutar los flujos de trabajo, consulte <a href="#jsondatasource">Usar el esquema JSON como fuente de datos.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>Opción 2</strong>: Puede  <a href="#generate-adaptive-forms-with-json-binding">generar un formulario adaptable con </a> enlaces de datos JSON mediante el servicio de Automated forms conversion. El servicio de cumplimentación previa y el envío de formularios funcionan sin problemas. No necesita ningún paso de configuración.</p> </td> 
  </tr>
   <tr>
  <td></td> 
   <td> 
    <p>Para obtener instrucciones paso a paso para ejecutar los flujos de trabajo, consulte <a href="#jsonwithdatabinding">Usar el esquema JSON como el origen de datos.</a></p> </td> 
  </tr>
  <tr>
  <td><p>Esquema XSD</p></td> 
   <td> 
    <p>Puede seleccionar esquema XSD como fuente de datos. Según el origen de datos seleccionado, <a href="#generate-adaptive-forms-with-no-data-binding">genera un formulario adaptable sin enlace de datos</a> mediante el servicio de Automated forms conversion y configura el esquema XSD como el origen de datos. Los campos de formulario adaptables se enlazan manualmente al esquema XSD y <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">se utiliza cualquiera de los protocolos admitidos</a> para rellenar previamente los valores de campo. Si es necesario, modifique los valores de los campos y envíe los datos al repositorio crx.</p>
    </td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>Para obtener instrucciones paso a paso para ejecutar los flujos de trabajo, consulte <a href="#xsddatasource">Usar el esquema XSD como el origen de datos.</a></p>
    </td> 
  </tr>
 </tbody> 
</table>


Para obtener más información sobre el servicio de Automated forms conversion, consulte los siguientes artículos:

* [Introducción al servicio de conversión automatizada de formularios](introduction.md)
* [Configurar el servicio de conversión automatizada de formularios](configure-service.md)
* [Convertir la impresión de formularios en formularios adaptables](convert-existing-forms-to-adaptive-forms.md)
* [Revisar y corregir formularios convertidos](review-correct-ui-edited.md)

La información proporcionada en este artículo se basa en la suposición de que cualquiera que la lea tiene conocimientos básicos de conceptos de formularios adaptables.

## Requisitos previos {#pre-requisites}

* Configurar una [instancia de autor de AEM](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html)
* Configure el servicio de Automated forms conversion [en la instancia de creación de AEM](configure-service.md)

## Formulario adaptable de ejemplo {#sample-adaptive-form}

Para ejecutar los casos de uso para rellenar previamente los valores de campo en un formulario adaptable y enviarlos al origen de datos, descargue el siguiente archivo PDF de muestra.

Formulario de solicitud de préstamo de muestra

[Obtener archivo](assets/sample_loan_application_form.pdf)

El archivo PDF sirve como entrada al servicio de Automated forms conversion. El servicio convierte este archivo en un formulario adaptable. La siguiente imagen muestra la aplicación de préstamo de ejemplo en formato PDF.

![formulario de solicitud de préstamo de muestra](assets/sample_form_new.png)

## Preparar datos para el modelo de formulario {#prepare-data-for-form-model}

La integración de datos de AEM Forms le permite configurar y conectar fuentes de datos dispares. Después de generar un formulario adaptable mediante el proceso de conversión, puede definir el modelo de formulario basado en un modelo de datos de formulario, XSD o un esquema JSON. Puede utilizar una base de datos, Microsoft Dynamics o cualquier otro servicio de terceros para crear un modelo de datos de formulario.

Este tutorial utiliza la base de datos MySQL como origen para crear un modelo de datos de formulario. Cree un esquema **solicitud de préstamo** en la base de datos y agregue una tabla **solicitante** al esquema en función de los campos disponibles en el formulario adaptable.

![Datos de muestra mysql](assets/sample_data_mysql.png)

Puede utilizar la siguiente instrucción DDL para crear la tabla **solicitante** en la base de datos.

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

Para obtener más información sobre el uso de esquema XSD como modelo de formulario en formularios adaptables, consulte [Creación de formularios adaptables con esquema XML](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-xml-schema-form-model.html).

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

Esquema JSON de solicitud de préstamo de muestra

[Obtener archivo](assets/demo_schema.json)

Para obtener más información sobre el uso de esquema JSON como modelo de formulario en formularios adaptables, consulte [Creación de formularios adaptables con esquema JSON](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html).

## Generar formularios adaptables sin enlace de datos {#generate-adaptive-forms-with-no-data-binding}

Utilice el servicio de Automated forms conversion [para convertir](convert-existing-forms-to-adaptive-forms.md) el [formulario de solicitud de préstamo de muestra](#sample-adaptive-form) en un formulario adaptable sin enlace de datos. Asegúrese de seleccionar la casilla de verificación **[!UICONTROL Generate adaptive form(s) without data bindings]** para generar el formulario adaptable sin enlace de datos.

![Formulario adaptable sin enlace de datos](assets/generate_af_without_binding.png)

Después de generar un formulario adaptable sin enlace de datos, seleccione un origen de datos para el formulario adaptable:

* [Base de datos, OData o cualquier servicio de terceros](#sqldatasource)
* [Esquema JSON](#jsondatasource)
* [Esquema XSD](#xsddatasource)

>[!NOTE]
> Si el formulario adaptable que se convierte mediante el servicio de Automated forms conversion contiene varios campos con el mismo nombre, asegúrese de que dichos campos están enlazados a entidades de origen de datos para evitar una posible pérdida de datos durante el envío.


### Utilizar base de datos, OData o cualquier servicio de terceros como fuente de datos {#sqldatasource}

Caso de uso: Puede generar un formulario adaptable sin enlace de datos mediante el servicio de Automated forms conversion y configurar la base de datos MYSQL como el origen de datos. Los campos de formulario adaptables se enlazan manualmente a entidades del modelo de datos de formulario y se utiliza la opción **[!UICONTROL Form Data Model Prefill Service]** para rellenar previamente los valores de campo. Utilice la opción **[!UICONTROL Submit using Form Data Model]** para enviar el formulario adaptable.

Antes de ejecutar el caso de uso:

* [Configurar la base de datos MySQL como fuente de datos](https://helpx.adobe.com/experience-manager/6-5/forms/using/configure-data-sources.html#configurerelationaldatabase)
* [Crear el modelo de datos de formulario](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html)

En función del caso de uso, cree el modelo de datos de formulario **aplicación de préstamo** y enlace el argumento de servicio de lectura a un valor **[!UICONTROL Literal]**. El valor literal del número telefónico debe ser de uno de los registros configurados en el esquema **solicitante** de la base de datos MySQL. Los servicios utilizan el valor como argumento para recuperar detalles del origen de datos. También puede seleccionar [Atributo de Perfil de usuario o Atributo de solicitud](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html#bindargument) en la lista desplegable **[!UICONTROL Binding To]**

![Configurar modelo de datos de formulario](assets/configure_model_object.png)

>[!NOTE]
>
>Asegúrese de agregar servicios **get** e **insert** al modelo de datos de formulario, configurar y probar los servicios antes de ejecutar el caso de uso.

Siga estos pasos:

1. Seleccione el **formulario de solicitud de préstamo de ejemplo convertido** disponible en la carpeta **[!UICONTROL output]** y toque **[!UICONTROL Properties]**.
1. Toque la ficha **[!UICONTROL Form Model]**, seleccione **[!UICONTROL Form Data Model]** en la lista desplegable **[!UICONTROL Select From]** y toque **[!UICONTROL Select Form Data Model]** para seleccionar el modelo de datos de formulario **aplicación de préstamo**. Toque **[!UICONTROL Save & Close]** para guardar el formulario.
1. Seleccione el **formulario de solicitud de préstamo de muestra** y toque **[!UICONTROL Edit]**.
1. En la ficha **[!UICONTROL Content]**, toque el icono de configuración:

   ![configurar contenedor de formulario](assets/configure_form_container.png)

   1. En la sección **[!UICONTROL Basic]**, seleccione **[!UICONTROL Form Data Model Prefill service]** en la lista desplegable **[!UICONTROL Prefill Service]**.

   1. En la sección **[!UICONTROL Submission]**, seleccione **[!UICONTROL Submit using Form Data Model]** en la lista desplegable **[!UICONTROL Submit Action]**.

   1. Seleccione el modelo de datos mediante el campo **[!UICONTROL Data Model to submit]**.
   1. Toque ![icono hecho](assets/save_icon.svg) para guardar las propiedades.

1. Puntee en el cuadro de texto Nombre del solicitante y seleccione ![configurar icono](assets/configure_icon.svg) (Configurar).

   1. En el campo Referencia de enlace, seleccione **Solicitante** > **Nombre** y toque ![icono hecho](assets/save_icon.svg) para guardar las propiedades. Del mismo modo, cree un enlace de datos para **Dirección**, **Número de teléfono**, **Correo electrónico**, **Ocupación**, **Salario anual (en dólares)** y **No. de los campos miembros de la familia dependientes** con las entidades del modelo de datos de formulario.

   ![Enlazar referencias](assets/bind_references.png)

1. Toque **[!UICONTROL Preview]** para vista de los valores de campo de formulario adaptable rellenados previamente.
1. Si es necesario, modifique los valores de los campos y envíe el formulario adaptable. Los valores de campo se envían a la base de datos MySQL. Puede actualizar la tabla **solicitante** de la base de datos para vista de los valores actualizados en la tabla.

**Caso de uso:** se genera un formulario adaptable sin enlace de datos mediante el servicio de Automated forms conversion y se configura la base de datos MYSQL como origen de datos. Los campos de formulario adaptables se enlazan mediante el editor de reglas para rellenar previamente los valores de campo. Si es necesario, modifique los valores de los campos y envíe los datos al repositorio crx.

Ejecute los siguientes pasos para utilizar [editor de reglas](https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html) para invocar el servicio del modelo de datos de formulario para enlazar campos y rellenar valores previamente en un formulario adaptable:

1. Seleccione el **formulario de solicitud de préstamo de muestra** en la carpeta **[!UICONTROL output]** y toque **[!UICONTROL Edit]**.
1. En la ficha **[!UICONTROL Content]**, toque el icono de configuración:

   ![configurar contenedor de formulario](assets/configure_form_container.png)

   En la sección **[!UICONTROL Basic]**, seleccione **[!UICONTROL Form Data Model Prefill service]** en la lista desplegable **[!UICONTROL Prefill Service]**.

1. Toque el cuadro de texto **[!UICONTROL Applicant Name]** y toque **[!UICONTROL Edit Rules]**.

   ![Editar reglas para crear un enlace de datos](assets/edit_rules_bind_reference.png)

1. Puntee **[!UICONTROL Create]** en la página Editor de reglas.
1. En la página **[!UICONTROL Rule Editor]**:

   1. Seleccione un estado para el cuadro de texto Nombre del solicitante. Por ejemplo, **[!UICONTROL is initialized]**, que resulta en la ejecución de la condición **[!UICONTROL Then]** al procesar el formulario en modo **[!UICONTROL Preview]**.

   1. En la sección **[!UICONTROL Then]**, seleccione **[!UICONTROL Invoke Service]** en la lista desplegable **[!UICONTROL Select Action]**. Todos los servicios de la instancia de Forms se muestran en la lista desplegable.

   1. Seleccione un servicio **[!UICONTROL Get]** en la sección que enumera los modelos de datos de formulario. El campo Entrada muestra **número de teléfono**, que es la clave principal definida para el modelo de datos **solicitante**. El sistema recupera y antepone los valores del formulario adaptable a los campos de la sección Salida en función de este campo.

   1. Cree un enlace para los campos de formulario adaptables con las entidades del modelo de datos de formulario mediante la sección Salida. Por ejemplo, enlace el campo de formulario adaptable **[!UICONTROL Applicant Name]** con la entidad **name**.

   1. Tocar **[!UICONTROL Done]**. Vuelva a tocar **[!UICONTROL Done]** en la página Editor de reglas.

   ![Editor de reglas para enlazar referencias](assets/rule_editor_bind_references.png)

1. Toque **[!UICONTROL Preview]** para vista de los valores de campo de formulario adaptable rellenados previamente.

   >[!NOTE]
   >
   >Asegúrese de que la propiedad **[!UICONTROL Return Array]** está establecida en OFF para la propiedad de servicio **get** en el modelo de datos de formulario asociado al formulario adaptable.

1. Si es necesario, modifique los valores de los campos y envíe el formulario adaptable. Los datos enviados están disponibles en la siguiente ubicación del repositorio crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### Utilizar el esquema JSON como fuente de datos {#jsondatasource}

**Caso de uso:** puede generar un formulario adaptable sin enlace de datos mediante el servicio de Automated forms conversion y configurar el esquema JSON como el origen de datos. Los campos de formulario adaptables se enlazan manualmente al esquema JSON y se utiliza la opción **Previsualización con datos** para rellenar previamente los valores de campo. Si es necesario, modifique los valores de los campos y envíe los datos al repositorio crx.

Antes de ejecutar el caso de uso, asegúrese de que:

* [un esquema JSON válido compatible con la estructura de esquema JSON](#prepare-data-for-form-model)
* [un formulario adaptable sin enlace de datos](#generate-adaptive-forms-with-no-data-binding)

Siga estos pasos:

1. Seleccione el **formulario de solicitud de préstamo de ejemplo convertido** disponible en la carpeta **output** y toque **[!UICONTROL Properties]**.
1. Toque la ficha **[!UICONTROL Form Model]**, seleccione **[!UICONTROL Schema]** en la lista desplegable **[!UICONTROL Select From]** y toque **[!UICONTROL Select Schema]** para cargar el esquema **demo.esquema JSON** guardado en el sistema de archivos local. Toque **[!UICONTROL Save & Close]** para guardar el formulario.
1. Seleccione el **formulario de solicitud de préstamo de muestra** y toque **[!UICONTROL Edit]**.
1. Puntee en el cuadro de texto Nombre del solicitante y seleccione ![configurar icono](assets/configure_icon.svg) (Configurar).

   En el campo Referencia de enlace, seleccione **Solicitante** > **Nombre** y toque ![icono hecho](assets/save_icon.svg) para guardar las propiedades. Del mismo modo, cree un enlace de datos para **Dirección**, **Número de teléfono**, **Correo electrónico**, **Ocupación**, **Salario anual (en dólares)** y **No. de los campos de miembros de la familia dependientes** con las entidades de esquema JSON.

1. Seleccione el **formulario de solicitud de préstamo de ejemplo convertido** disponible en la carpeta **[!UICONTROL output]** de nuevo y seleccione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Descargar archivo de datos de ejemplo</br>

   [Obtener archivo](assets/json_data_file.txt)</br>

1. Si es necesario, modifique los valores de los campos y envíe el formulario adaptable. Los datos enviados están disponibles en la siguiente ubicación del repositorio crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### Utilice el esquema XSD como fuente de datos {#xsddatasource}

**Caso de uso:** puede generar un formulario adaptable sin enlace de datos mediante el servicio de Automated forms conversion y configurar el esquema XSD como el origen de datos. Los campos de formulario adaptables se enlazan manualmente al esquema XSD y se utiliza la Previsualización **con datos** para rellenar previamente los valores de campo. Si es necesario, modifique los valores de los campos y envíe los datos al repositorio crx.

Antes de ejecutar el caso de uso, asegúrese de que:

* [un esquema XSD válido compatible con la estructura de esquema XML](#prepare-data-for-form-model)
* [un formulario adaptable sin enlace de datos](#generate-adaptive-forms-with-no-data-binding)

Siga estos pasos:

1. Seleccione el **formulario de solicitud de préstamo de ejemplo convertido** disponible en la carpeta **[!UICONTROL output]** y toque **[!UICONTROL Properties]**.
1. Toque la ficha **[!UICONTROL Form Model]**, seleccione **[!UICONTROL Schema]** en la lista desplegable **[!UICONTROL Select From]** y toque **[!UICONTROL Select Schema]** para cargar el esquema **aplicación de préstamo** XSD guardado en el sistema de archivos local. Seleccione el elemento raíz para el esquema XSD y toque **[!UICONTROL Save & Close]** para guardar el formulario.
1. Seleccione el **formulario de solicitud de préstamo de muestra** y toque **[!UICONTROL Edit]**.
1. Puntee en el cuadro de texto Nombre del solicitante y seleccione ![configurar icono](assets/configure_icon.svg) (Configurar).
En el campo Referencia de enlace, seleccione **Solicitante** > **Nombre** y toque ![Icono hecho](assets/save_icon.svg) para guardar las propiedades. Del mismo modo, cree un enlace de datos para **Dirección**, **Número de teléfono**, **Correo electrónico**, **Ocupación**, **Salario anual (en dólares)** y **No. de los campos de miembros de la familia dependientes** con las entidades de esquema XSD.

1. Seleccione el **formulario de solicitud de préstamo de muestra convertido** disponible en la carpeta **output** nuevamente y seleccione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Descargar archivo de datos de ejemplo</br>

   [Obtener archivo](assets/loan-application-data-xml-data.zip)</br>


1. Si es necesario, modifique los valores de los campos y envíe el formulario adaptable. Los datos enviados están disponibles en la siguiente ubicación del repositorio crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## Generar formularios adaptables con enlace JSON {#generate-adaptive-forms-with-json-binding}

Utilice el servicio de Automated forms conversion [para convertir](convert-existing-forms-to-adaptive-forms.md) el [formulario de solicitud de préstamo de muestra](#sample-adaptive-form) en un formulario adaptable con enlace de datos. Asegúrese de no seleccionar la casilla de verificación **[!UICONTROL Generate adaptive form(s) without data bindings]** al generar el formulario adaptable.

![Formulario adaptable con enlace JSON](assets/generate_af_with_data_bindings.png)

### Utilizar el esquema JSON como fuente de datos {#jsonwithdatabinding}

**Caso de uso:** se genera un formulario adaptable con enlace de datos JSON mediante el servicio de Automated forms conversion. El servicio de cumplimentación previa y el envío de formularios funcionan sin problemas. No necesita ningún paso de configuración.

Antes de ejecutar el caso de uso, asegúrese de que tiene [un formulario adaptable con enlace de datos](#generate-adaptive-forms-with-json-binding).

Siga estos pasos:

1. Seleccione el **formulario de solicitud de préstamo de ejemplo convertido** disponible en la carpeta **[!UICONTROL output]** de nuevo y seleccione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Descargar archivo de datos de ejemplo</br>

   [Obtener archivo](assets/loan_application_data_source_json_data_binding.txt)</br>

1. Si es necesario, modifique los valores de los campos y envíe el formulario adaptable. Los datos enviados están disponibles en la siguiente ubicación del repositorio crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## Convertir datos JSON de formulario adaptable enviados al formato XML {#convert-submitted-adaptive-form-data-to-xml}

Cuando se introducen valores en campos de formulario adaptables y se envían, los datos están disponibles en formato JSON en el repositorio crx. Puede convertir el formato de los datos JSON a XML mediante la API [org.apache.sling.commons.json.xml](https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString) o el siguiente código de muestra:

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
