---
title: Preguntas frecuentes
seo-title: Preguntas frecuentes
description: Consultas comunes o preguntas más frecuentes
seo-description: preguntas más frecuentes sobre el servicio automatizado de conversión de Forms
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
translation-type: tm+mt
source-git-commit: 14e6d1fba9f27fde4fe24de83cb00c9847ea4e90
workflow-type: tm+mt
source-wordcount: '1822'
ht-degree: 4%

---


# Preguntas frecuentes{#frequently-asked-questions}

1. **¿Qué versión de AEM Forms admite el servicio Conversión automatizada de Forms?**

   <p>El servicio de conversión automatizada de Forms es compatible con AEM 6.4 Forms y AEM 6.5 Forms. Funciona con AEM Forms en OSGi y AEM formularios en JEE. Para utilizar el servicio, debe disponer del paquete de AEM Forms Add-on más reciente que AEM instancia de creación. For detailed instructions, see <a href="configure-service.md">Configure the Automated Forms Conversion</a> service.</p> 
    <br>

1. **¿Puede instalarse el servicio in situ?**

   <p>Adobe forma regularmente algoritmos AI y ML del servicio de conversión automatizada de Forms con nuevos conjuntos de datos para mejorar la precisión de conversión. Los algoritmos actualizados se implementan en el servicio de conversión que se ejecuta en Adobe Cloud a intervalos periódicos. Todos los clientes del servicio se benefician de los algoritmos actualizados. Por lo tanto, la implementación central alojada en la nube es la mejor opción para el servicio de conversión automatizada de Forms para aprender y ofrecer mejoras de forma continua a todos los clientes.</p> 
    <p>El servicio convierte los formularios en blanco en formularios adaptables. El servicio no admite formularios rellenados ni extracción de datos de formularios rellenados. Elimine datos de los formularios rellenados y elimine o lista de permitidos la información de propiedad de los formularios antes de enviarlos al servicio para su conversión</p> <br>

1. **¿Admite el servicio todos los formatos de PDF forms? ¿Qué idiomas son compatibles?**

   <p>El servicio puede convertir PDF forms no interactivos, XDP y PDF forms basados en XFA y AcroForms en formularios adaptables. El servicio no admite formularios escaneados o rellenados. Para ver otras limitaciones, consulte el artículo sobre problemas <a href="known-issues.md"></a> conocidos.<br /> </p> 
    <p>Generalmente agregamos compatibilidad con otros tipos de fuentes. Mantenga la sección de formularios <a href="introduction.md">PDF</a> admitidos en la lista de observación para obtener una actualización periódica de las funciones y funciones recientemente agregadas.</p>

   El servicio solo puede convertir formularios en inglés a formularios adaptables. Puede traducir los formularios adaptables que se generan a otro idioma mediante el [flujo de trabajo de traducción de AEM.](https://helpx.adobe.com/es/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **¿Puede el servicio producir un XDP en lugar de un formulario adaptable?**

   <p>El servicio no produce una salida XDP. Estamos añadiendo funciones y servicios con regularidad. Mantenga la sección de idiomas y PDF forms <a href="introduction.md"></a> admitidos en la lista de observación para obtener una actualización periódica de las funciones y funciones recientemente agregadas.</p> <br>

1. **¿Cuál es el tipo de esquema generado?**

   <p>Puede utilizar el servicio para generar: </p>

   * un formulario adaptable enlazado a un esquema JSON y
   * un formulario adaptable no enlazado a ningún esquema <br><br>

1. **¿Puede el servicio convertir un formulario de Microsoft Word en formularios adaptables?**

   <p>No, el servicio no convierte un formulario de Microsoft Word a un formulario adaptable. Puede guardar un formulario de Microsoft Word en un formulario PDF y convertirlo en un formulario adaptable. El proceso completo es </p> <br>

   1. Utilice Adobe Acrobat para [convertir Word Document en un PDF](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html)no interactivo.
   1. Utilice Adobe Acrobat para [convertir los PDF forms producidos en formularios](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html)PDF rellenables.
   1. Utilice Adobe Acrobat para actualizar y corregir manualmente los campos del formulario.
   1. Guarde el formulario PDF. Ahora puede utilizar el formulario con el servicio de conversión para generar un formulario adaptable. También puede utilizar el formulario como Documento de la plantilla Registro.


1. **¿Puede el servicio convertir formularios impresos digitalizados y formularios coloreados en formularios adaptables?**

   <p>El servicio puede convertir PDF forms de color en formularios adaptables. El servicio no admite formularios escaneados o rellenados. Para ver otras limitaciones, consulte el artículo sobre problemas <a href="known-issues.md"></a> conocidos.</p> <br>

1. **¿Puede el servicio convertir un formulario digitalizado o solo una imagen de un formulario en un formulario adaptable?**

   <p>El servicio no admite la conversión de formularios digitalizados o una imagen de un formulario en una lista para usar adaptable. Sin embargo, puede utilizar Adobe Acrobat para convertir la imagen de un formulario a un formulario PDF. Por lo tanto, use el servicio para convertir el formulario PDF a un formulario adaptativo. Utilice siempre una imagen de alta calidad del formulario para la conversión en Acrobat. Mejora la calidad de la conversión.</p> <br>

1. **Algunos formularios basados en XDP utilizan fragmentos de formulario, ¿dónde se deben cargar estos fragmentos de formulario?**

   <p class="MsoNormal">Cargue fragmentos de formulario en la carpeta de conversión y conserve la estructura de carpetas original. Ayuda a conservar las rutas relativas utilizadas en los formularios basados en XDP y en los fragmentos de formulario.</p> <br>

1. **¿Admite el servicio formularios XDP enlazados con esquema? Si tengo un XDP enlazado a un esquema, ¿necesito incrustar esquema a XDP?**

   <p>Sí, el servicio admite formularios XDP enlazados a esquemas y requiere que el esquema se incruste en el formulario XDP de origen. Al convertir un formulario XDP enlazado a esquema, el servicio genera un esquema JSON. El esquema JSON es estructuralmente similar al esquema XSD de los formularios XDP de origen.</p> <br>

1. **El servicio no ha podido convertir los formularios. ¿Cuál es la razón y cómo resolver el problema?**
Las razones más comunes para que la conversión falle son:
</p>
   * Se proporcionan PDF forms seguros para la conversión. No utilice PDF forms protegidos por contraseña o protegidos para la conversión.
   * Se ha interrumpido la conexión a Internet. Asegúrese de estar conectado a Internet durante la conversión.
   * El PDF de origen tiene una imagen del formulario en lugar del formulario real.
   * El servicio está configurado incorrectamente, no se proporciona la dirección URL del servicio o la dirección URL del servicio proporcionada es incorrecta. Compruebe la configuración [del](configure-service.md#configure-the-cloud-service) servicio en **[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**.
   * La configuración de IMS no está configurada correctamente. Realice una comprobación de estado en la configuración de IMS para asegurarse de que funciona correctamente. Para comprobar si la configuración de IMS es correcta o no:
      1. Ir a `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. Seleccione la configuración. Haga clic en el **[!UICONTROL Check Health]** encabezado y haga clic en **[!UICONTROL Check]**. Si tiene éxito, recibirá **[!UICONTROL Token retrieved successfully!]** un mensaje. <br> <br>

1. **¿El uso de fuentes personalizadas afecta a la conversión?**

   <p>Cuando un formulario PDF no interactivo se convierte en un formulario adaptable, para mejorar la calidad de la conversión, las fuentes se incrustan en el formulario PDF. La compatibilidad con la incrustación de fuentes está restringida a los PDF forms no interactivos. Para optimizar la conversión de PDF forms basados en AcroForm y XFA, se utilizan fuentes de reserva.</p> 
    <p>Solo los formularios disponibles en el directorio de fuentes personalizadas que aparece en el campo <strong>Directorio</strong> de fuentes del cliente de la configuración del servicio <strong></strong> CQ-DAM-Handler-Gibson Font Manager están incrustados en un formulario PDF no interactivo.</p> 
    <p> </p> <br>

1. **¿El servicio identifica y utiliza fuentes del PDF de origen en los formularios adaptables de salida?**

   <p>El estilo y la presentación de un formulario HTML interactivo suele ser diferente de un formulario PDF o en papel. Para admitir una presentación y un estilo coherentes en todas las organizaciones, los formularios adaptables utilizan <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">temáticas para aplicar estilo a un formulario</a>. El servicio de conversión utiliza las fuentes y los estilos de fuente especificados en el tema aplicado durante la conversión. Puede cambiar las fuentes y los estilos de fuente del tema para proporcionar un aspecto y una apariencia distintos a los componentes de un formulario adaptable.</p> <br>

1. **¿El servicio extrae automáticamente JavaScript de formularios basados en XDP y lo aplica a los formularios adaptables correspondientes?**

   <p>El servicio no convierte automáticamente las secuencias de comandos de formularios basados en XFA o Acro Forms a las correspondientes reglas de formularios adaptables. Los autores de formularios pueden utilizar el editor <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">de</a> reglas para agregar interactividad a un formulario adaptable.</p> <br>

1. **Algunos objetos de formulario no se convierten correctamente en componentes de formulario adaptables. ¿Cómo resolver el problema?**

   <p>El servicio de conversión automatizada de Forms se capacita en un gran conjunto de formularios. Pero las aplicaciones basadas en AI/ML están limitadas por sus datos y patrones de capacitación. Podría haber múltiples tipos de campo, diseños, patrones y contexto perceptibles para la percepción humana pero difíciles de reconocer automáticamente. Es posible que el servicio no identifique dichos objetos o que los reconozca incorrectamente. Puede utilizar el editor <a href="review-correct-ui-edited.md" target="_blank">Revisar y corregir</a> para realizar las modificaciones necesarias en la presentación familiar basada en formularios impresos del formulario de entrada.</p> <br/>

1. **Algunas correcciones se repiten en todos los formularios. ¿Puede el servicio identificar y corregir todas estas instancias en futuras conversiones?**

   El servicio está formando de manera consistente en sus formularios y patrones. Aprende nuevos patrones a diario. Todavía no se han aplicado inicios para aplicar automáticamente las correcciones repetidas en todos los formularios. Esté atento a los formularios de evaluación para la disponibilidad de dicha función. <br/><br/>

   Se puede utilizar un meta-modelo para asignar los objetos de formulario al componente de formulario adaptable de su elección y preconfigurar validaciones, reglas, patrones de datos, texto de ayuda y propiedades de accesibilidad para los componentes. Todas las propiedades especificadas se aplican durante la conversión. Puede utilizar el metamodelo para aplicar propiedades comunes a los campos. Puede ayudarle a reducir algunos problemas repetidos en los distintos formularios.<br/><br/>

1. **¿Cuáles son las opciones para los formularios con datos confidenciales como la información de identificación personal (PII)?**
El servicio solo admite formularios en blanco o sin rellenar. No cargue formularios o formularios rellenados con información de identificación personal (PII). Además, elimine los datos precargados, la información de identificación personal (PII), la información confidencial y la información de propiedad en los formularios de origen. 
<br/>

1. **¿Dónde se deben colocar el encabezado y los pies de página?**

   <p>Coloque el encabezado y el pie de página en una plantilla de formulario adaptable. Si el formulario PDF de origen tiene encabezado y pie de página, el servicio detecta y reemplaza el encabezado y pie de página detectados por el encabezado y pie de página disponibles en la plantilla de formulario adaptable durante la conversión. Si se incluye cualquier encabezado o pie de página adicional en el formulario adaptable, puede utilizar el editor <a href="review-correct-ui-edited.md">Revisar y corregir</a> para corregir o eliminar dicho encabezado o pie de página.</p> <br />

1. **¿Cuánto tiempo ahorra el servicio en comparación con el proceso manual de planificación, creación de recursos (temáticas, plantillas), creación y publicación de un formulario adaptable?**

   <p>La cantidad de tiempo depende del tamaño y la complejidad de los formularios de entrada y del número de solicitudes. El servicio tiene la intención de reducir significativamente el tiempo de respuesta al valor convirtiendo a los PDF forms en formularios adaptables a un ritmo mucho más rápido en comparación con el proceso manual de conversión de formularios. </p> <br />

1. **¿Qué hacer si se produce un error relacionado con las bibliotecas RSA? El mensaje de error es similar al que se indica a continuación:** <br/>

El error mencionado se produce cuando la delegación de inicio no está configurada para las bibliotecas RSA/BouncyCastle. Siga los pasos a continuación para resolver el problema:   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
El error mencionado se produce cuando la delegación de inicio no está configurada para las bibliotecas RSA/BouncyCastle. Siga los pasos a continuación para resolver el problema:
   <p> </p>

   1. Detenga la instancia de AEM. Vaya a la `[AEM installation directory]\crx-quickstart\conf\` carpeta. Abra el archivo sling.properties para editarlo. Si utiliza `[AEM installation directory]\crx-quickstart\bin\start.bat` para inicio de una instancia de AEM, edite el archivo sling.properties ubicado en `[AEM_root]\crx-quickstart\`.
   1. Añada las siguientes propiedades en el archivo sling.properties:<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. Guarde y cierre el archivo. <br/>
   1. Inicio la instancia de AEM.<br/>

   <br/>

1. **¿Cómo se cambia automáticamente el formato de mayúsculas y minúsculas del texto del formulario adaptable?**

   <p>Se puede utilizar un método adaptable de temáticas o un editor de estilos para cambiar la forma en mayúsculas de un campo de formulario adaptable. Por ejemplo, puede abrir el editor de temas y establecer el valor de la propiedad Case de todo el texto del formulario en mayúsculas, minúsculas o camelCase. También puede utilizar la opción Anulación de CSS en el editor de temas para crear distintos tipos de estilos.</p>

1. **¿Puedo utilizar etiquetas de texto de Adobe Sign con el servicio de conversión automatizada de Forms?**

   <p> Cuando se utiliza el servicio de conversión automatizada de Forms para convertir un formulario PDF en un formulario adaptable y el formulario PDF tiene etiquetas de texto de Adobe Sign, dichas etiquetas se convierten a los campos de formulario adaptables correspondientes y los detalles del firmante se rellenan automáticamente.  Esta función solo está disponible para Acrobat Forms y los formularios adaptables admiten un número limitado de campos de Adobe Sign.</p>  </br>

   <p> Para la lista completa de las etiquetas admitidas, abra un formulario en el editor de formularios adaptables y agregue un bloque Adobe Sign. Utilice el bloque Adobe Sign para buscar todos los campos de Adobe Sign admitidos. Proporciona una lista desplegable para seleccionar todos los campos admitidos.</p>