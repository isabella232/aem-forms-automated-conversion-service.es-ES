---
title: 'Conversión de formularios PDF en formularios adaptables '
seo-title: 'Conversión de formularios PDF en formularios adaptables '
description: Ejecución del servicio de Automated forms conversion para convertir PDF forms en formularios adaptables
seo-description: Ejecución del servicio de Automated forms conversion para convertir PDF forms en formularios adaptables
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
translation-type: tm+mt
source-git-commit: c4f0d07b38cdb6aa162a0b61abe12fe9d1677a8c
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 8%

---


# Conversión de formularios PDF en formularios adaptables {#convert-print-forms-to-adaptive-forms}

El servicio de Automated forms conversion de AEM Forms, equipado con Adobe Sensei, convierte automáticamente a sus PDF forms en formularios adaptables adaptables adaptables y adaptables para dispositivos. Tanto si utiliza PDF forms no interactivos, Acro Forms o PDF forms basados en XFA, el servicio de Automated forms conversion puede convertir fácilmente estos formularios en formularios adaptables. Para obtener información sobre las capacidades, el flujo de trabajo de conversión y la información de integración, consulte el servicio [Automated forms conversion](introduction.md).

## Requisitos previos {#pre-requisites}

* [**Configurar el servicio de conversión**](configure-service.md)

* **Prepare las  [](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html) plantillas que se aplicarán a los formularios convertidos:** el uso de una plantilla le permite aplicar una marca coherente en todos los formularios adaptables. Además, el servicio de Automated forms conversion no extrae ni utiliza el encabezado ni el pie de página de los documentos PDF de origen. Puede utilizar plantillas de formulario adaptables para especificar el encabezado y el pie de página. El encabezado y el pie de página especificados en la plantilla se aplican al formulario adaptable durante la conversión. Cuando cree una carpeta para las plantillas, seleccione la opción **[!UICONTROL Browse configurations]** para todos.

* **Prepare los  [](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html) temas que se aplicarán a los formularios convertidos:** el uso de un tema permite aplicar un estilo coherente a todos los formularios adaptables de la organización.

* **(opcional)** [**Convertir los PDF forms de origen en un formulario de Adobe Sign**](frequently-asked-questions.md)


## Inicio del proceso de conversión {#start-the-conversion-process}

Después de conectar la instancia de AEM con el servicio de conversión de AEM Forms, puede convertir los PDF forms en formularios adaptables. Realice los siguientes pasos en el orden indicado para convertir los formularios:

* [Cargar PDF forms en el servidor de AEM Forms](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [Ejecutar la conversión](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [Revisar y corregir los formularios convertidos](review-correct-ui-edited.md)

### Cargar PDF forms a su servidor AEM Forms {#upload-pdf-forms-to-your-aem-forms-server}

El servicio de conversión convierte los PDF forms disponibles en la instancia de AEM Forms en formularios adaptables. Puede cargar todos los PDF forms a la vez o de forma gradual, según sea necesario. Antes de cargar los formularios, tenga en cuenta lo siguiente:

* Mantenga el número de formularios en una carpeta por debajo de 15 y el número total de páginas en una carpeta por debajo de 50.
* Mantenga el tamaño de la carpeta por debajo de los 10 MB. No mantenga los formularios en una subcarpeta.
* Mantenga el número de páginas de un formulario por debajo de 15.
* No cargue los formularios protegidos. El servicio no convierte formularios protegidos por contraseña ni protegidos por contraseña.
* No cargue formularios de origen con espacios en el nombre del archivo. Quite el espacio del nombre del archivo antes de cargar los formularios.
* No cargue [carpetas PDF](https://helpx.adobe.com/es/acrobat/using/overview-pdf-portfolios.html). El servicio no convierte un Portfolio PDF en un formulario adaptable.
* Lea las secciones [Problemas conocidos](known-issues.md) y [Prácticas recomendadas y consideraciones](styles-and-pattern-considerations-and-best-practices.md) y realice los cambios sugeridos en los formularios.

Siga los pasos siguientes para cargar los formularios que se van a convertir en una carpeta en la instancia de AEM Forms:

1. Inicie sesión en la instancia de AEM Forms.

1. Puntee **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Tocar **[!UICONTROL Create]**> **[!UICONTROL Folder]**. Especifique **Título** y **Nombre** de la carpeta. Tocar **[!UICONTROL Create]**. Se crea una carpeta.
1. Toque para abrir la carpeta recién creada.
1. Tocar **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. Seleccione los formularios que desea cargar, haga clic en **[!UICONTROL Open]** y, a continuación, en **[!UICONTROL Upload]**. Los formularios se cargan.

### Ejecute la conversión {#run-the-conversion}

Después de cargar los formularios y configurar el servicio, realice los siguientes pasos para realizar la inicio:

1. En la instancia de AEM Forms, toque **[!UICONTROL Adobe Experience Manager]** ![Cuadro de diálogo Configuración de conversión](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Seleccione un formulario o la carpeta que contenga PDF forms (formularios que convertir) y toque **[!UICONTROL Start Automated Conversion]**. Aparece el cuadro de diálogo **[!UICONTROL Conversion Settings]**.

   ![Especifique las configuraciones](assets/conversion-settings-dialog.png)

1. En la ficha **[!UICONTROL Basic]** del cuadro de diálogo Configuración de conversión:

   * **[!UICONTROL Select a cloud configuration]**. Al seleccionar una configuración, ya se especifican la plantilla y el tema predeterminados. Puede especificar una plantilla o un tema diferente, si es necesario.
   * Especifique una ubicación para guardar los formularios adaptables generados y el esquema correspondiente. Puede utilizar rutas predeterminadas o especificar rutas personalizadas.
   * Utilice la opción **Generar formularios adaptables sin enlaces de modelo de datos** para seleccionar si desea generar un formulario adaptable con o sin enlaces de modelo de datos.
Si no selecciona esta opción, el servicio de conversión asocia automáticamente los formularios adaptables con un esquema JSON y crea un enlace de datos entre los campos disponibles en el formulario adaptable y el esquema JSON. El campo **[!UICONTROL Save generated data model schema at]** muestra la ubicación predeterminada para guardar el esquema JSON generado. También puede personalizar la ubicación para guardar el esquema generado.
Si selecciona esta opción, el servicio de conversión genera un formulario adaptable sin enlaces de modelo de datos. Tras una conversión correcta, puede asociar un formulario adaptable a un modelo de datos de formulario, un esquema XML o un esquema JSON. Para obtener más información, consulte [Creación de un formulario adaptable](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html).

   <!--
   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. En la ficha **[!UICONTROL Additional]** del cuadro de diálogo Configuración de conversión,
   * Seleccione la opción **[!UICONTROL Extract fragment from adaptive forms]** para permitir que el servicio de conversión identifique, extraiga y descargue fragmentos de formulario para formularios convertidos. Cuando selecciona la opción **[!UICONTROL Extract fragment from adaptive forms]**, se activan las opciones para especificar rutas para guardar fragmentos de formulario extraídos y los correspondientes esquemas de fragmentos de formulario.
   * Especifique la ubicación de **[!UICONTROL existing adaptive form fragments]**, si ya tiene fragmentos de formulario basados en esquemas JSON y de esquema menos adaptables y tiene pensado utilizar estos fragmentos en formularios adaptables generados automáticamente. El servicio de conversión coincide con los fragmentos de formulario disponibles basados en esquemas JSON y con los fragmentos de formulario menos adaptables de esquema con PDF forms de entrada (solo PDF forms no interactivos). Si hay una coincidencia, el fragmento de formulario adaptable coincidente se utiliza en los formularios adaptables correspondientes.

   >[!NOTE]
   >
   >
   > * Sólo puede utilizar la opción **[!UICONTROL  Extract Fragment]** o **[!UICONTROL Use existing adaptive form fragments]** a la vez. No puede usar ambas opciones simultáneamente.
   > * Puede utilizar la opción **[!UICONTROL Use existing adaptive form fragments]** solo con PDF forms no interactivos. Aún no se admiten otros tipos de formularios.
   > * Solo puede utilizar fragmentos o fragmentos independientes enlazados a un esquema JSON con el servicio de conversión automatizada. No utilice fragmentos XFA. No se admiten los fragmentos XFA.


   * Seleccione la opción **[!UICONTROL Auto-detect multi-column layout of input forms]** para conservar la presentación del formulario de origen para pantallas grandes como computadoras de escritorio y portátiles. Esta opción es útil para conservar el diseño de varias columnas de los formularios de origen. Por ejemplo, cuando un PDF de origen tiene una presentación de dos columnas, el servicio genera un formulario adaptable de salida con una presentación de dos columnas para pantallas grandes y una presentación de una sola columna para dispositivos de pantalla pequeños como teléfonos móviles. La función tiene algunos problemas conocidos con la estructura del esquema del origen de datos. Para obtener más información, consulte el artículo [known-issues](known-issues.md).
   * De forma predeterminada, el servicio crea un panel independiente de nivel superior para cada página de un formulario PDF. Ahora puede utilizar la opción **[!UICONTROL Auto-detect logical sections]** para no crear paneles de nivel de página (paneles basados en números de página) y crear únicamente paneles lógicos. También agrupa los campos que no pertenecen a ninguna sección con la sección lógica anterior y los campos de una sección lógica se distribuyen en dos páginas adyacentes en una sola sección lógica. Por ejemplo, si algunos campos de una sección lógica están al final de la página uno y otros al comienzo de la página dos, todos esos campos se agrupan en una sola sección lógica.

      >[!NOTE]
      > Debe utilizar la función **[!UICONTROL Auto-detect logical sections]** para el paquete de conector 1.1.38 o superior.



1. Tocar **[!UICONTROL Start Conversion]**. Se ha iniciado la conversión. El progreso de conversión se muestra en la carpeta o en el formulario hasta que la conversión esté en curso. El mensaje se sustituye por otro mensaje de estado (Convertido, Conversión parcial o Error de conversión) una vez finalizada la conversión. También se envía un mensaje de correo electrónico de estado en la dirección de correo electrónico configurada una vez finalizada la conversión:

   * En una conversión correcta, el formulario adaptable convertido y el esquema relacionado se descargan en la ruta especificada en la ficha **[!UICONTROL Basic]** del cuadro de diálogo de conversión. Los fragmentos de formulario y el esquema correspondiente solo se descargan si se selecciona la opción Extraer fragmento antes de iniciar la conversión.
   * En una conversión fallida, se muestra el mensaje **[!UICONTROL Conversion Failed]** si no se pueden convertir todos los formularios de entrada o se muestra el mensaje **[!UICONTROL Partially Failed]** cuando sólo algunos de los formularios de entrada no se pueden convertir. Se envía un correo electrónico de estado en la [dirección de correo electrónico configurada](configure-service.md#configureemailnotification) y se registra un error en el archivo error.log.

   Si va a convertir un formulario PDF basado en XFA en un formulario adaptable, el servicio de conversión asocia automáticamente el formulario PDF al formulario adaptable convertido como el Documento de la plantilla de registro. Después de la conversión, puede abrir las propiedades del formulario adaptable para la vista del Documento de la plantilla Registro en la sección **[!UICONTROL Document of Record Template Configuration]** de la ficha **[!UICONTROL Form Model]**. </br>

   El servicio de conversión carga automáticamente el formulario PDF en el formulario adaptable convertido como el Documento de la plantilla de registro sólo si activa la opción **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]**.

   <!--
   Comment Type: draft

   <note type="note">
   <p>By default, the adaptive form produces a JSON schema instead of XML schema on submission. JSON schema of a converted adaptive form is complaint with XML schema of an XFA-based form. You can use the <a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString">org.apache.sling.commons.json.xml API</a> to convert a JSON schema to XML schema. You can also use the following sample code for conversion:</p>
   <p><code class="code">import org.apache.sling.commons.json.JSONException;
   <discoiqbr /> import org.apache.sling.commons.json.JSONObject;
   <discoiqbr /> import org.apache.sling.commons.json.xml.XML;
   <discoiqbr />
   <discoiqbr /> public class ConversionUtils {
   <discoiqbr />
   <discoiqbr /> public static String jsonToXML(String jsonString) throws JSONException {
   <discoiqbr /> //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
   <discoiqbr /> //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
   <discoiqbr /> //Note: Need to extract boundData part before converting to XML
   <discoiqbr /> return XML.toString(new JSONObject(jsonString));
   <discoiqbr /> }
   <discoiqbr /> }</code><br /> </p>
   </note>
   -->

   >[!NOTE]
   >
   >Si el proceso de conversión tarda más de 60 minutos y el formulario PDF aún no se convierte en un formulario adaptable, cree una carpeta en la instancia de AEM Forms, cargue el formulario PDF en la carpeta recién creada y reinicie la conversión.

## Revisar y corregir los formularios convertidos {#review-and-correct-the-converted-forms}

Los formularios del mundo real tienen requisitos de captura de datos complejos. Una vez completada la conversión automatizada, los clientes pueden revisar la calidad de conversión del formulario y realizar las actualizaciones necesarias en el mismo. AEM Forms proporciona una [revisión y un editor correcto](review-correct-ui-edited.md) para realizar los cambios necesarios. Permite mejorar la identificación automatizada de los campos de formulario y convertir los campos identificados de un tipo a otro. Por ejemplo, puede ayudar a identificar la presentación en dos columnas de un formulario y cambiar un campo identificado automáticamente como botón de opción a un campo de varias opciones.
