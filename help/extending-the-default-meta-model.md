---
title: Ampliar el metamodelo predeterminado
seo-title: Ampliar el metamodelo predeterminado
description: Amplíe el metamodelo predeterminado para agregar patrones, validaciones y entidades específicas de su organización y aplique configuraciones a campos de formulario adaptables mientras ejecuta el servicio de Automated forms conversion.
seo-description: Amplíe el metamodelo predeterminado para agregar patrones, validaciones y entidades específicas de su organización y aplique configuraciones a campos de formulario adaptables mientras ejecuta el servicio de Automated forms conversion.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
exl-id: f679059c-18aa-4cb5-8368-ed27e96c20de
source-git-commit: 3f91fc0541f8fe8dbc997ae0b401c8a0a49347dd
workflow-type: tm+mt
source-wordcount: '2569'
ht-degree: 1%

---

# Ampliar el metamodelo predeterminado {#extend-the-default-meta-model}

El servicio de automated forms conversion identifica y extrae objetos de formulario de los formularios de origen. El asignador semántico ayuda al servicio a decidir cómo se representan los objetos extraídos en un formulario adaptable. Por ejemplo, un formulario de origen puede tener muchos tipos diferentes de representaciones de una fecha. El asignador semántico ayuda a asignar todas las representaciones de los objetos de formulario de fecha del formulario de origen con el componente de fecha de los formularios adaptables. El asignador semántico también permite que el servicio preconfigure y aplique validaciones, reglas, patrones de datos, texto de ayuda y propiedades de accesibilidad a los componentes de formulario adaptables durante la conversión.

![](assets/meta-model.gif)

El metamodelo es un esquema JSON. Antes de empezar con el metamodelo, asegúrese de tener una amplia experiencia con JSON. Debe tener experiencia en la creación, edición y lectura de datos guardados en formato JSON.

## Metamomodelo predeterminado {#default-meta-model}

El servicio de automated forms conversion tiene un metamodelo predeterminado. Es un esquema JSON y reside en Adobe Cloud con otros componentes del servicio de Automated forms conversion. Puede encontrar una copia del metamodelo en el servidor de AEM local en: http://&lt;server>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/metamodel/`global.schema.json`. También puede [hacer clic aquí](assets/en.globalschema.json) para acceder o descargar el esquema de idioma inglés. El metamodelo para los idiomas [French](assets/fr.globalschema.json), [German](assets/de.globalschema.json) y [Spanish](assets/es.globalschema.json) también está disponible para su descarga.

El esquema de metamodelo se deriva de entidades de esquema en https://schema.org/docs/schemas.html. Tiene Person, PostalAddress, LocalBusiness y más entidades tal como se definen en https://schema.org. Cada entidad del metamodelo se adhiere al tipo de objeto de esquema JSON. El siguiente código representa una estructura de metamodelo de ejemplo:

```
   "Entity": {
      "id": "Entity",
      "properties": {
        "name": {
          "type": "string"
        },

        "description": {
          "type": "string",
          "description": "Description of the item"
        }
      }
    }
```

## Descargar el metamodelo predeterminado {#download-the-default-meta-model}

Realice los siguientes pasos para descargar el metamodelo predeterminado en el sistema de archivos local:

1. Inicie sesión en la instancia de AEM Forms.
1. Vaya a la carpeta **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** **** **[!UICONTROL Meta Model]** .
1. Seleccione el archivo **[!UICONTROL global.schema.json]** y pulse **[!UICONTROL Download]**. Aparece un cuadro de diálogo de descarga. Seleccione la opción **[!UICONTROL Download asset(s) as binary files]**. Tocar **[!UICONTROL Download]**. Se descarga un archivo.

   <!--
   Comment Type: draft

   <li><p>Extract the archive and open the global.schema.json file for editing. </p> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

## Explicación del metamodelo {#understanding-the-meta-model}

Un metamodelo hace referencia a un archivo de esquema JSON que contiene entidades. Todas las entidades del archivo de esquema JSON incluyen un nombre y un ID. Cada entidad puede incluir varias propiedades. Las entidades y sus propiedades pueden variar en función del dominio. Puede aumentar un archivo de esquema con palabras clave y configuraciones de campo para asignar propiedades de esquema a componentes de formulario adaptables.

```
"Event": {
      "id": "Eventid",
      "allOf": [
        {
          "$ref": "#Entity"
        },
        {
          "properties": {
            "startDate": {
              "type": "string",
              "format": "date",
              "description": "Specify the start date and time of the event in ISO 8601 date format."
            },
            "endDate": {
              "type": "string",
              "format": "date",
              "description": "Specify the end date and time of the event in ISO 8601 date format."
            },
            "location": {
              "$ref": "#PostalAddress",
              "description": "Specify the location of the event."
            }
          }
        }
      ]
    }
```

En este ejemplo, **Event** representa el nombre de una entidad con un valor para **id** como **Eventid**. La entidad Event incluye varias propiedades:

* startDate
* endDate
* ubicación

La construcción **allOf** en el metamodelo permite la herencia entre entidades.

Cada propiedad puede incluir además:

* [Propiedades del esquema JSON](#jsonschemaproperties)
* [Búsqueda basada en palabras clave para aplicar propiedades a campos de formulario adaptables generados](#keywordsearch)
* [Propiedades adicionales](#additionalproperties)

![Propiedades del metamodelo](assets/meta_model_elements.gif)

En función de las palabras clave a las que se hace referencia mediante **aem:affKeyword**, el servicio de conversión realiza una operación de búsqueda en los campos del formulario de origen. El servicio de conversión aplica las propiedades del esquema JSON y propiedades adicionales a los campos que cumplen los criterios de búsqueda.

En este ejemplo, el servicio de conversión busca las palabras clave de teléfono, teléfono, teléfono móvil, teléfono del trabajo, teléfono doméstico, número de teléfono, número de teléfono y número de teléfono en el formulario de origen. En función de los campos que incluyen estas palabras clave, el servicio de conversión aplica el tipo, patrón y aem:afProperties a los campos de formulario adaptables después de la conversión.

### Propiedades del esquema JSON para campos de formulario adaptables generados {#jsonschemaproperties}

El metamodelo admite las siguientes propiedades comunes de esquema JSON para campos de formulario adaptables generados mediante el servicio de Automated forms conversion:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Nombre de propiedad</strong></th> 
   <th><strong>Descripción</strong></th> 
  </tr> 
  <tr> 
   <td><p>el título</p></td> 
   <td> 
    <p>El texto mencionado dentro de la propiedad title en un metamodelo sirve como palabra clave de búsqueda para realizar acciones en los campos de formulario adaptables generados. Por ejemplo, modificar la etiqueta de un campo de formulario adaptable. Para obtener más información, consulte <strong>Modificación de la etiqueta de un campo de formulario</strong> en <a href="#custommetamodelexamples">Ejemplos de metamodelos personalizados.</a></p> </td> 
  </tr>
  <td><p>Descripción</p></td> 
   <td> 
    <p>La propiedad description define el texto de la Ayuda para el campo de formulario adaptable generado. Para obtener más información, consulte <strong>Agregar texto de ayuda a un campo de formulario</strong> en <a href="#custommetamodelexamples">Ejemplos de metamodelos personalizados.</a></p> </td> 
  </tr>
  <td><p>tipo</p></td> 
   <td> 
    <p>La propiedad type define el tipo de datos del campo de formulario adaptable generado. Los valores posibles de la propiedad title incluyen:</p>
    <ul> 
     <li>cadena: Genera un campo de formulario adaptable de tipo de datos de texto.</li> 
     <li>número: Genera un campo de formulario adaptable de tipo de datos numérico.</li>
     <li>entero: Genera un campo de formulario adaptable de tipo de datos numérico con el subtipo definido como entero.</li>
     <li>booleano: Genera un componente de formulario adaptable de conmutación.</li>
     </ul><p>Para obtener más información sobre el uso de la propiedad type en un metamodelo, consulte <strong>Modificación del tipo de un campo de formulario</strong> en <a href="#custommetamodelexamples">Ejemplos de metamodelos personalizados.</a></p></td> 
  </tr>
  <td><p>pattern</p></td> 
   <td> 
    <p>La propiedad pattern restringe el valor del campo de formulario adaptable generado en función de una expresión regular. Por ejemplo, el siguiente código del metamodelo restringe el valor del campo de formulario adaptable generado a diez dígitos:<br>"pattern": "/\\d{10}/"<br>De manera similar, el siguiente código del metamodelo restringe el valor de un campo a un formato de fecha específico.<br> "pattern": "date{DD MMMM, AAAA}",</p> </td> 
  </tr>
  <td><p>format</p></td> 
   <td> 
    <p>La propiedad format restringe el valor del campo de formulario adaptable generado basándose en un patrón con nombre en lugar de en una expresión regular. Los valores posibles de la propiedad format incluyen:<ul><li>correo electrónico: Genera un componente de formulario adaptable de correo electrónico.</li><li>hostname: Genera un componente de formulario adaptable de cuadro de texto.</li></ul>Para obtener más información sobre el uso de la propiedad format en un metamodelo, consulte <strong>Modificación del formato de un campo de formulario</strong> en <a href="#custommetamodelexamples">Ejemplos de metamodelos personalizados.</a></p> </td> 
  </tr>
  <td><p>enum y enumNames</p></td> 
   <td> 
    <p>Las propiedades enum y enumNames restringen los valores de los campos desplegable, casilla de verificación o botón de radio a un conjunto fijo. Los valores enumerados en enumNames se muestran en la interfaz de usuario. Los valores enumerados con la propiedad enum se utilizan para el cálculo.<br>Para obtener más información, consulte  <strong>Conversión de un campo de formulario en casillas de verificación de opción múltiple en el formulario</strong> adaptable,  <strong>Conversión de un campo de texto en una lista desplegable en el formulario</strong> adaptable y  <strong>Adición de opciones adicionales a la lista </strong> desplegable en ejemplos de metamodelos  <a href="#custommetamodelexamples">personalizados.</a></p> </td> 
  </tr>
 </tbody> 
</table>

### Búsqueda basada en palabras clave para aplicar propiedades a campos de formulario adaptables generados {#keywordsearch}

El servicio de automated forms conversion realiza una búsqueda de palabras clave en el formulario de origen durante la conversión. Después de filtrar los campos que cumplen los criterios de búsqueda, el servicio de conversión aplica las propiedades definidas para esos campos en el metamodelo a los campos de formulario adaptable generados.

Se hace referencia a las palabras clave mediante la propiedad **aem:affKeyword**.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

En este ejemplo, el servicio de conversión utiliza el texto **aem:affKeyword** como palabra clave de búsqueda. Después de recuperar el texto **Bank account number** en el formulario, el servicio de conversión convierte el campo en un tipo **number** utilizando la propiedad **type**.

### Propiedades adicionales para campos de formulario adaptables generados {#additionalproperties}

Puede utilizar la propiedad **aem:afProperties** del metamodelo para definir las siguientes propiedades adicionales para los campos de formularios adaptables generados mediante el servicio de Automated forms conversion:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Nombre de propiedad</strong></th> 
   <th><strong>Descripción</strong></th> 
  </tr> 
  <tr> 
   <td><p>multiLine</p></td> 
   <td> 
    <p>La propiedad multiLine convierte un campo de formulario de origen en un campo multilínea del formulario adaptable después de la conversión. Para obtener más información, consulte <strong>Convertir un campo de cadena en un campo multilínea</strong> en <a href="#custommetamodelexamples">Ejemplos de metamodelos personalizados.</a></p> </td> 
  </tr>
  <td><p>obligatorio</p></td> 
   <td> 
    <p>La propiedad mandatory define como obligatoria la entrada de un campo de formulario adaptable después de la conversión.<br>Para obtener más información, consulte  <strong>Agregar validaciones a campos de formulario adaptables </strong> en ejemplos de metamodelos  <a href="#custommetamodelexamples">personalizados.</a></p>
    </td> 
  </tr>
  <td><p>jcr:title</p></td> 
   <td> 
    <p>La propiedad jcr:title, con la propiedad title JSON schema , permite modificar la etiqueta de un campo de formulario adaptable después de la conversión.<br>Para obtener más información, consulte  <strong>Modificación de la etiqueta de un </strong> campo de formulario en ejemplos de metamodelos  <a href="#custommetamodelexamples">personalizados.</a><br>Consulte  <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html" target="_blank">Creación de formularios adaptables mediante </a> esquemas JSON para obtener información sobre más propiedades que se pueden aplicar a campos de formulario adaptables mediante el esquema JSON.</p>
    <p></p></td> 
  </tr>
  <td><p>sling:resourceType y guideNodeClass</p></td> 
   <td> 
    <p>las propiedades sling:resourceType y guideNodeClass permiten asignar un campo de formulario a un componente de formulario adaptable correspondiente.<br>Para obtener más información, consulte  <strong>Conversión de un campo de formulario en casillas de verificación de opción múltiple en el </strong> formulario adaptable y  <strong>Conversión de un campo de texto en lista desplegable en el </strong> formulario adaptable  <a href="#custommetamodelexamples">Ejemplos de metamodelos personalizados.</a></p> </td> 
  </tr>
  <td><p>validatePictureClause</p></td> 
   <td> 
    <p>La propiedad validatePictureClause establece una validación en el formato permitido en el campo de formulario adaptable después de la conversión.<br>Para obtener más información, consulte  <strong>Agregar validaciones a campos de formulario adaptables </strong> en ejemplos de metamodelos  <a href="#custommetamodelexamples">personalizados.</p> </td> 
  </tr>
 </tbody> 
</table>

## Crear un modelo personalizado en su propio idioma{#language-specific-meta-model}

Puede crear un metamodelo específico del idioma. Este metamodelo le ayuda a crear reglas de asignación en el idioma que elija. El servicio de automated forms conversion le permite crear metamodelos en los siguientes idiomas:

* Inglés(en)
* Francés(fr)
* Alemán(de)
* Español()

Agregue la etiqueta de metaetiqueta *aem:Language* a la parte superior de un metamodelo para especificar su idioma. Por ejemplo,

```JSON
"metaTags": {
        "aem:Language": "de"
    }
```

El inglés es el idioma predeterminado de los metamodelos.

### Consideraciones para crear un metamodelo específico de un idioma

* Asegúrese de que el nombre de cada clave esté en inglés. Por ejemplo, emailAddress.
* Asegúrese de que todas las referencias de entidad y los valores predefinidos de todas las claves *id* estén en inglés. Por ejemplo, &quot;id&quot;: &quot;ContactPoint&quot; / &quot;$ref&quot;: &quot;Entidad&quot;.
* Asegúrese de que la descripción o los mensajes incluidos en un metamodelo para las claves siguientes correspondan al idioma del metamodelo:
   * aem:affKeyword
   * el título
   * Descripción
   * enumNames
   * shortDescription
   * validatePictureClauseMessage

   Por ejemplo, cuando el idioma del metamodelo es francés (&quot;aem:Language&quot;: &quot;fr&quot;), asegúrese de que todas las descripciones y mensajes estén en francés.

* Asegúrese de que todas las [propiedades del esquema JSON](#jsonschemaproperties) utilizan solo valores admitidos.

La siguiente imagen muestra ejemplos del metamodelo en inglés y el metamodelo en francés correspondiente:

![](assets/language-specific-meta-model-comparison.png)

## Modificación de campos de formulario adaptables utilizando un metamodelo personalizado {#modify-adaptive-form-fields-using-custom-meta-model}

Su organización puede tener patrones y validaciones además de las que aparecen en el metamodelo predeterminado. Puede ampliar el metamodelo predeterminado para añadir patrones, validaciones y entidades específicas de su organización. El servicio de automated forms conversion aplica el metamodelo personalizado a los campos de formulario durante la conversión. Puede seguir actualizando el metamodelo a medida que se descubran nuevos patrones, validaciones y entidades específicas de su organización.

El servicio de automated forms conversion utiliza un metamodelo predeterminado guardado en la siguiente ubicación para asignar campos de formulario de origen a los campos de formulario adaptables durante la conversión:

http://&lt;server>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json

Sin embargo, puede guardar un metamodelo personalizado en una carpeta y modificar las propiedades del servicio de conversión para utilizar el metamodelo personalizado durante la conversión.

### Usar metamodelo personalizado durante la conversión {#use-custom-meta-model-during-conversion}

Ejecute los siguientes pasos para utilizar un metamodelo personalizado durante la conversión:

1. Cree una carpeta en **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** y cargue el archivo de esquema JSON de metamodelo personalizado en la carpeta .
1. Abra las propiedades del servicio de conversión mediante:

   **[!UICONTROL Tools]** >  **[!UICONTROL Cloud Services]** >  **[!UICONTROL Automated Forms Conversion Configuration]**>  **&lt;>Propiedades de la configuración** seleccionada>****

1. En la pestaña **[!UICONTROL Basic]**, especifique la ubicación del metamodelo personalizado en el campo **[!UICONTROL Custom Meta-model]** y pulse **[!UICONTROL Save & Close]**.
1. [Ejecute la ](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) conversión para aplicar el metamodelo personalizado al proceso de conversión.

### Ejemplos de metamodelos personalizados {#custommetamodelexamples}

Algunos ejemplos comunes del uso de un metamodelo personalizado para modificar las propiedades de los campos de formulario adaptables son:

* Modificación de la etiqueta de un campo de formulario
* Modificación del tipo de campo de formulario
* Agregar texto de ayuda a un campo de formulario
* Conversión de un campo de formulario en botones de opción de opción múltiple en el formulario adaptable
* Modificación del formato de un campo de formulario
* Agregar validaciones a campos de formulario adaptables
* Conversión de un campo de formulario en opciones de lista desplegable en el formulario adaptable
* Agregar opciones adicionales a la lista desplegable
* Conversión de un campo de cadena en un campo multilínea

#### Modificación de la etiqueta de un campo de formulario {#modify-the-label-of-a-form-field}

**Ejemplo:** modifique la etiqueta de número de cuenta bancaria del formulario a Número de cuenta personalizado en el formulario adaptable después de la conversión.

En este metamodelo personalizado, el servicio de conversión utiliza la propiedad **title** como palabra clave de búsqueda. Después de recuperar el texto **Bank account number** en el formulario, el servicio de conversión reemplaza el texto por la cadena **Customer account number** mencionada con la propiedad **jcr:title** en la sección **aem:afProperties**.

```
{
  "numberfields": {
      "type": "number",
   "title": "Bank account number",
   "aem:afProperties" : {
    "jcr:title" : "Customer account number"
   }
   }
}
```

#### Modificación del tipo de campo de formulario {#modify-the-type-of-a-form-field}

**Ejemplo**: Modifique el campo  **Número de cuenta** bancaria del tipo de texto del formulario antes de la conversión a un campo de tipo numérico en el formulario adaptable después de la conversión.

En este metamodelo personalizado, el servicio de conversión utiliza el texto dentro de **aem:affKeyword** como palabra clave de búsqueda. Después de recuperar el texto **Bank account number** en el formulario, el servicio de conversión convierte el campo en un tipo de número mediante la propiedad **type**.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

#### Agregar texto de ayuda a un campo de formulario {#add-help-text-to-a-form-field}

**Ejemplo**: Agregue texto de ayuda al campo  **Número de cuenta** bancaria del formulario adaptable.

En este metamodelo personalizado, el servicio de conversión utiliza el texto dentro de **aem:affKeyword** como palabra clave de búsqueda. Después de recuperar el texto **Bank account number** en el formulario, el servicio de conversión agrega el texto de Ayuda al campo del formulario adaptable utilizando la propiedad **description**.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "description": "Specify your bank account number."
 }
}
```

#### Conversión de un campo de formulario en casillas de verificación de opción múltiple en el formulario adaptable {#convert-a-form-field-to-multiple-choice-check-boxes-in-the-adaptive-form}

**Ejemplo**: Convierta el campo  **** País del tipo de cadena en el formulario antes de la conversión en casillas de verificación del formulario adaptable después de la conversión.

En este metamodelo personalizado, el servicio de conversión utiliza texto dentro de **aem:affKeyword** como palabra clave de búsqueda. Después de recuperar el texto **Country** en el formulario, el servicio de conversión convierte el campo en las siguientes casillas de verificación mediante la propiedad **enum** :

* India
* Inglaterra
* Australia
* Nueva Zelanda

**sling:** resourceType y  **** guideNodeClassproperties asignan un campo de formulario al componente de formulario adaptable de la casilla de verificación.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidecheckbox",
      "guideNodeClass": "guidecheckbox"
    }
  }
}
```

#### Modificación del formato de un campo de formulario {#modify-the-format-of-a-form-field}

**Ejemplo**: Modifique el formato del campo  **Dirección de** correo electrónico a un formato de correo electrónico.

En este metamodelo personalizado, el servicio de conversión utiliza texto dentro de **aem:affKeyword** como palabra clave de búsqueda. Después de recuperar el texto **Email Address** en el formulario, el servicio de conversión convierte el campo en un formato de correo electrónico con la propiedad **format**.

```
{
   "additionalDetails" : {
      "aem:affKeyword": ["E-mail Address"],
       "type" : "string",
       "format" : "email"
  } 
}
```

#### Agregar validaciones a campos de formulario adaptables {#add-validations-to-adaptive-form-fields}

**Ejemplo 1:** agregue una validación al campo  **Código** postal del formulario adaptable.

En este metamodelo personalizado, el servicio de conversión usa texto dentro de **aem:affKeyword** como palabra clave de búsqueda. Después de recuperar el texto **Código postal** en el formulario, el servicio de conversión agrega una validación al campo utilizando la propiedad **validatePictureClause** definida en la sección **aem:afProperties**. En función de la validación, la entrada especificada para el campo **Código postal** del formulario adaptable después de la conversión debe incluir seis caracteres.

```
{
   "postalCode" : {
      "aem:affKeyword": ["Postal Code"],
      "type" : "string",
      "aem:afProperties" : {
        "validatePictureClause" : "\\d{6}"
      } 
   }
}
```

**Ejemplo 2:** agregue una validación al campo  **Número de cuenta** bancaria del formulario adaptable.

En este metamodelo personalizado, el servicio de conversión usa texto dentro de **aem:affKeyword** como palabra clave de búsqueda. Después de recuperar el texto **Bank account number** en el formulario, el servicio de conversión agrega una validación al campo utilizando la propiedad **mandatory** definida en la sección **aem:afProperties**. En función de la validación, debe especificar un valor para el campo **Bank account number** antes de enviar el formulario después de la conversión.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "aem:afProperties" : {
        "mandatory": "true"
      }   
   }
}
```

#### Conversión de un campo de texto en una lista desplegable del formulario adaptable {#convert-a-text-field-to-drop-down-list-in-the-adaptive-form}

**Ejemplo**: Convierta el campo  **** País del tipo de cadena en el formulario antes de la conversión a las opciones desplegables del formulario adaptable después de la conversión.

En este metamodelo personalizado, el servicio de conversión usa texto dentro de **aem:affKeyword** como palabra clave de búsqueda. Después de recuperar el texto **Country** en el formulario, el servicio de conversión convierte el campo en las siguientes opciones de lista desplegable utilizando la propiedad **enum** :

* India
* Inglaterra
* Australia
* Nueva Zelanda

**sling:** resourceType y  **** guideNodeClassproperties asignan un campo de formulario al componente de formulario adaptable desplegable.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidedropdownlist",
      "guideNodeClass": "guideDropDownlist"
    }
  }
}
```

#### Agregar opciones adicionales a la lista desplegable {#add-additional-options-to-the-drop-down-list}

**Ejemplo:** añada  **Sri** Lankaas como opción adicional a una lista desplegable existente utilizando un metamodelo personalizado.

Para agregar una opción adicional, actualice la propiedad **enum** con la nueva opción. En este ejemplo, actualice la propiedad **enum** con **Sri Lanka** como opción adicional. Los valores enumerados en la propiedad **enum** se muestran en la lista desplegable.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand",
   "Sri Lanka"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidecheckbox",
      "guideNodeClass": "guidecheckbox"
    }
  }
}
```

#### Conversión de un campo de cadena en un campo multilínea {#convert-a-string-field-to-a-multi-line-field}

**Ejemplo:** convierta el campo  **** Dirección del tipo de cadena en un campo de varias líneas del formulario después de la conversión.

En este metamodelo personalizado, el servicio de conversión usa texto dentro de **aem:affKeyword** como palabra clave de búsqueda. Después de recuperar el texto **Address** en el formulario, el servicio convierte el campo de texto en un campo multilínea utilizando la propiedad **multiLine** definida en la sección **aem:afProperties**.

```
{
 "multiLine" : {
   "aem:affKeyword": [
      "Address"
    ],
    "type" : "string",
    "aem:afProperties": {
      "multiLine": "true"
    }
  }
}
```
