---
title: 'Conversión de formularios PDF en formularios adaptables '
seo-title: Convert PDF forms to adaptive forms
description: Ejecute el servicio de Automated forms conversion para convertir PDF forms en formularios adaptables
seo-description: Run the Automated Forms Conversion service to convert PDF forms to adaptive forms
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
exl-id: 415e05b5-5a90-490c-bf7c-d3365ce95e24
source-git-commit: 5f07f5df6369007a491cf0873839f84a61827cb5
workflow-type: tm+mt
source-wordcount: '1631'
ht-degree: 7%

---

# Conversión de formularios PDF en formularios adaptables {#convert-print-forms-to-adaptive-forms}

El servicio de Automated forms conversion de AEM Forms, con tecnología de Adobe Sensei, convierte automáticamente sus PDF forms en formularios adaptables y adaptables para dispositivos. Ya sea que utilice PDF forms no interactivos, Acrobat Forms o PDF forms basados en XFA, el servicio de Automated forms conversion puede convertir fácilmente estos formularios en formularios adaptables. Para obtener información sobre las capacidades, el flujo de trabajo de conversión y la información de incorporación, consulte [automated forms conversion](introduction.md) servicio.

## Requisitos previos {#pre-requisites}

* [**Configuración del servicio de conversión**](configure-service.md)

* **Prepare el [plantillas](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html) que se aplicará a los formularios convertidos:** El uso de una plantilla permite aplicar una marca coherente a todos los formularios adaptables. Además, el servicio de Automated forms conversion no extrae ni utiliza el encabezado y pie de página de los documentos de PDF de origen. Puede utilizar plantillas de formulario adaptables para especificar el encabezado y el pie de página. El encabezado y el pie de página especificados en la plantilla se aplican al formulario adaptable durante la conversión. Cuando cree una carpeta para las plantillas, seleccione la opción **[!UICONTROL Browse configurations]** para todos.

* **Prepare el [temáticas](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html) que se aplicará a los formularios convertidos:** El uso de un tema le permite aplicar un estilo coherente a todas las formas adaptables de su organización.

* **(opcional)** [**Convertir los PDF forms de origen en un formulario de Adobe Sign**](frequently-asked-questions.md)

## Iniciar el proceso de conversión {#start-the-conversion-process}

Después de conectar la instancia de AEM con el servicio de conversión de AEM Forms, puede convertir los PDF forms en formularios adaptables. Realice los siguientes pasos en el orden enumerado para convertir los formularios:

* [Cargar PDF forms al servidor de AEM Forms](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [Ejecución de la conversión](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [Revisar y corregir los formularios convertidos](review-correct-ui-edited.md)

### Cargar PDF forms al servidor de AEM Forms {#upload-pdf-forms-to-your-aem-forms-server}

El servicio de conversión convierte los PDF forms disponibles en la instancia de AEM Forms en formularios adaptables. Puede cargar todos los PDF forms a la vez o de forma gradual, según sea necesario. Antes de cargar los formularios, tenga en cuenta lo siguiente:

* Mantenga el número de formularios en una carpeta por debajo de 15 y conserve el número total de páginas en una carpeta por debajo de 50.
* Mantenga el tamaño de la carpeta por debajo de 10 MB. No guarde formularios en una subcarpeta.
* Mantenga el número de páginas en un formulario por debajo de 15.
* No cargue los formularios protegidos. El servicio no convierte formularios protegidos por contraseña y protegidos por contraseña.
* No cargue formularios de origen con espacios en el nombre de archivo. Quite el espacio del nombre del archivo antes de cargar los formularios.
* No cargue [carpetas PDF](https://helpx.adobe.com/es/acrobat/using/overview-pdf-portfolios.html). El servicio no convierte un Portfolio PDF a un formulario adaptable.
* Lea el [Problemas conocidos](known-issues.md) y [Prácticas recomendadas y consideraciones](styles-and-pattern-considerations-and-best-practices.md) y realice los cambios sugeridos en los formularios.

Realice los siguientes pasos para cargar los formularios que desea convertir en una carpeta en la instancia de AEM Forms:

1. Inicie sesión en la instancia de AEM Forms.

1. Toque **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Tocar **[!UICONTROL Create]**> **[!UICONTROL Folder]**. Especifique **Título** y **Nombre** de la carpeta. Tocar **[!UICONTROL Create]**. Se crea una carpeta.
1. Toque para abrir la carpeta recién creada.
1. Tocar **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. Seleccione los formularios que desea cargar, haga clic en **[!UICONTROL Open]** y haga clic en **[!UICONTROL Upload]**. Los formularios se cargan.

### Ejecución de la conversión {#run-the-conversion}

Después de cargar los formularios y configurar el servicio, realice los siguientes pasos para iniciar la conversión:

1. En la instancia de AEM Forms, pulse **[!UICONTROL Adobe Experience Manager]** ![Cuadro de diálogo Configuración de conversión](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Seleccione un formulario o la carpeta que contenga PDF forms (formularios que desea convertir) y pulse **[!UICONTROL Start Automated Conversion]**. La variable **[!UICONTROL Conversion Settings]** se abre.

   ![Especificar las configuraciones](assets/conversion-settings-dialog.png)

1. En el **[!UICONTROL Basic]** en el cuadro de diálogo Configuración de conversión:

   * **[!UICONTROL Select a cloud configuration]**. Al seleccionar una configuración, ya se han especificado la plantilla y el tema predeterminados. Si es necesario, puede especificar una plantilla o un tema diferentes.
   * Especifique una ubicación para guardar los formularios adaptables generados y el esquema correspondiente. Puede utilizar rutas predeterminadas o especificar rutas personalizadas.
   * Utilice la variable **Generación de formularios adaptables sin enlaces de modelos de datos** para seleccionar si desea generar un formulario adaptable con o sin enlaces del modelo de datos.
Si no selecciona esta opción, el servicio de conversión asocia automáticamente los formularios adaptables con un esquema JSON y crea un enlace de datos entre los campos disponibles en el formulario adaptable y el esquema JSON. La variable **[!UICONTROL Save generated data model schema at]** muestra la ubicación predeterminada para guardar el esquema JSON generado. También puede personalizar la ubicación para guardar el esquema generado.
Si selecciona esta opción, el servicio de conversión genera un formulario adaptable sin enlaces del modelo de datos. Después de una conversión correcta, puede asociar un formulario adaptable a un Modelo de datos de formulario, un esquema XML o un esquema JSON. Para obtener más información, consulte [Creación de un formulario adaptable](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html).

   <!--

   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. En el **[!UICONTROL Additional]** pestaña del cuadro de diálogo Configuración de conversión,
   * Seleccione el **[!UICONTROL Extract fragment from adaptive forms]** para permitir que el servicio de conversión identifique, extraiga y descargue fragmentos de formulario para formularios convertidos. Al seleccionar la variable **[!UICONTROL Extract fragment from adaptive forms]** , están activadas las opciones para especificar rutas para guardar fragmentos de formulario extraídos y los esquemas de fragmentos de formulario correspondientes.
   * Especifique la ubicación de **[!UICONTROL existing adaptive form fragments]**, si tiene algunos fragmentos de formulario basados en esquemas JSON y esquemas menos adaptables existentes y tiene previsto utilizar estos fragmentos en formularios adaptables generados automáticamente. El servicio de conversión coincide con los fragmentos de formulario disponibles basados en esquemas JSON y esquemas menos adaptables con PDF forms de entrada (solo PDF forms no interactivos); si hay una coincidencia, el fragmento de formulario adaptable coincidente se utiliza en los formularios adaptables correspondientes.

   >[!NOTE]
   >
   >
   > * Solo puede usar **[!UICONTROL  Extract Fragment]** o **[!UICONTROL Use existing adaptive form fragments]** a la vez. No puede utilizar ambas opciones simultáneamente.
   > * Puede usar la variable **[!UICONTROL Use existing adaptive form fragments]** solo con PDF forms no interactivos. Otros tipos de formulario aún no son compatibles.
   > * Solo puede utilizar fragmentos independientes o fragmentos enlazados a un esquema JSON con el servicio de conversión automatizada. No utilice fragmentos XFA. Los fragmentos XFA no son compatibles.


   * Seleccione el **[!UICONTROL Auto-detect multi-column layout of input forms]** para conservar la presentación del formulario de origen para pantallas grandes como equipos de escritorio y portátiles. La opción es útil para conservar el diseño de varias columnas de los formularios de origen. Por ejemplo, cuando un PDF de origen tiene una presentación de dos columnas, el servicio genera un formulario adaptable de salida con una presentación de dos columnas para pantallas grandes y una presentación de una sola columna para dispositivos de pantalla pequeños como teléfonos móviles. La función tiene algunos problemas conocidos con la estructura del esquema de la fuente de datos. Para obtener más información, consulte la [problemas conocidos](known-issues.md) artículo.
   * De forma predeterminada, el servicio crea un panel independiente de nivel superior para cada página de un formulario PDF. Ahora puede usar la variable **[!UICONTROL Auto-detect logical sections]** para no crear paneles de nivel de página (paneles basados en números de página) y crear solo paneles lógicos. También agrupa los campos que no pertenecen a ninguna sección con la sección lógica anterior y los campos de una sección lógica se distribuyen en dos páginas adyacentes en una sola sección lógica. Por ejemplo, si algunos campos de una sección lógica están al final de la página uno y otros al comienzo de la página dos, todos esos campos se agrupan en una sola sección lógica.

      >[!NOTE]
      > Debe utilizar el paquete del conector 1.1.38 o superior para  **[!UICONTROL Auto-detect logical sections]** función.


* (Solo AEM Forms as a Cloud Service) El [Conversión automática de secciones en fragmentos] se aplica a los PDF forms con más de 15 páginas. Convierte las secciones de nivel superior detectadas en fragmentos. También activa la carga diferida para todos los fragmentos creados. Ayuda a mejorar la velocidad de procesamiento de los formularios convertidos y facilita la carga de formularios grandes en el editor de formularios adaptables.

   >[!NOTE]
   > No utilice plantillas de diseño adaptables mientras utiliza la opción Conversión automática de secciones a fragmentos .
   > Utilice el editor de revisiones y correcciones para combinar paneles pequeños con uno grande. Ayuda a reducir el número de fragmentos en el formulario adaptable convertido.
   > Si experimenta la excepción &quot;demasiadas llamadas&quot;,
   >
   > * reestructurar el formulario para crear una jerarquía simplificada
   > * [aumente el valor del parámetro sling.max.calls]a un número lo suficientemente alto hasta que desaparezca la excepción.
   > * [aumentar el tamaño de la caché](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/configure-aem-forms/configure-adaptive-forms-cache.html). El error se produce si el formulario es demasiado complejo, tiene un gran número de tablas y una estructura jerárquica de varios niveles.


1. Tocar **[!UICONTROL Start Conversion]**. Se inicia la conversión. El progreso de la conversión se muestra en la carpeta o en el formulario hasta que la conversión esté en curso. El mensaje se reemplaza con otro mensaje de estado (Convertido, Parcialmente convertido o Error de conversión) una vez completada la conversión. También se envía un correo electrónico de estado en la dirección de correo electrónico configurada al finalizar la conversión:

   * En una conversión correcta, el formulario adaptable convertido y el esquema relacionado se descargan a la ruta especificada en la variable **[!UICONTROL Basic]** del cuadro de diálogo de conversión. Los fragmentos de formulario y el esquema correspondiente solo se descargan si la opción Extraer fragmento está seleccionada antes de iniciar la conversión.
   * En una conversión fallida, la variable **[!UICONTROL Conversion Failed]** se muestra si no se pueden convertir todos los formularios de entrada o si no se puede realizar la **[!UICONTROL Partially Failed]** se muestra cuando solo unos pocos de todos los formularios de entrada no pueden convertirse. Se envía un correo electrónico de estado en la variable [dirección de correo electrónico configurada](configure-service.md#configureemailnotification) y se registra un error en el archivo error.log.

   Si está convirtiendo un formulario de PDF basado en XFA en un formulario adaptable, el servicio de conversión asocia automáticamente el formulario de PDF al formulario adaptable convertido como la plantilla Documento de registro. Tras la conversión, puede abrir las propiedades del formulario adaptable para ver la plantilla Documento de registro en la **[!UICONTROL Document of Record Template Configuration]** sección de **[!UICONTROL Form Model]** pestaña . </br>

   El servicio de conversión carga automáticamente el formulario del PDF en el formulario adaptable convertido como plantilla de Documento de registro solo si activa la variable **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** .

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
   >Si el proceso de conversión tarda más de 60 minutos y el formulario de PDF sigue sin convertirse en un formulario adaptable, cree una carpeta en la instancia de AEM Forms, cargue el formulario de PDF en la carpeta recién creada y reinicie la conversión.

## Revisar y corregir los formularios convertidos {#review-and-correct-the-converted-forms}

Los formularios del mundo real tienen requisitos complejos de captura de datos. Una vez completada la conversión automatizada, los clientes pueden revisar la calidad de conversión del formulario y realizar las actualizaciones necesarias en él. AEM Forms proporciona un [revisar y corregir](review-correct-ui-edited.md) para realizar los cambios necesarios. Permite mejorar la identificación automatizada de los campos de formulario y convertir los campos identificados de un tipo a otro. Por ejemplo, puede ayudar a identificar la presentación en dos columnas de un formulario y cambiar un campo identificado automáticamente como botón de opción por un campo de opciones múltiples.
