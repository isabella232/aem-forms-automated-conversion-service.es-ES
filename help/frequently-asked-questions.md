---
title: Preguntas frecuentes
seo-title: Preguntas frecuentes
description: Consultas comunes o preguntas más frecuentes
seo-description: preguntas más frecuentes sobre el servicio de Automated forms conversion
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
exl-id: 3a29f8d4-8ea0-49eb-bfe0-0eab5f0c52c7
source-git-commit: af05922f9eb76b7b0a30601824c6006fe555ea80
workflow-type: tm+mt
source-wordcount: '1830'
ht-degree: 4%

---

# Preguntas frecuentes{#frequently-asked-questions}

1. **¿Qué versión de AEM Forms admite el servicio de Automated forms conversion?**

   <p>El servicio de automated forms conversion es compatible con AEM 6.4 Forms y AEM 6.5 Forms. Funciona tanto con AEM Forms en OSGi como con AEM formularios en JEE. Para utilizar el servicio, necesita el último paquete de complementos de AEM Forms que se encuentra sobre AEM instancia de creación. Para obtener instrucciones detalladas, consulte <a href="configure-service.md">Configuración del servicio de Automated forms conversion</a>.</p> 
    <br>

1. **¿Se puede instalar el servicio in situ?**

   <p>Adobe forma regularmente algoritmos de Automated forms conversion de IA y ML con nuevos datos para mejorar la precisión de conversión. Los algoritmos actualizados se implementan en el servicio de conversión que se ejecuta en Adobe Cloud a intervalos periódicos. Todos los clientes del servicio se benefician de los algoritmos actualizados. Por lo tanto, la implementación central alojada en la nube es la más adecuada para que el servicio de Automated forms conversion aprenda y ofrezca mejoras continuas a todos los clientes.</p> 
    <p>El servicio convierte los formularios en blanco en formularios adaptables. El servicio no admite formularios rellenados ni la extracción de datos de formularios rellenados. Elimine los datos de los formularios rellenados y elimine o lista de permitidos la información de propiedad de los formularios antes de enviar los formularios al servicio para su conversión</p> <br>

1. **¿Admite el servicio todos los formatos de PDF forms? ¿Qué idiomas se admiten?**

   <p>El servicio puede convertir PDF forms no interactivos, XDP y PDF forms basados en XFA, y AcroForms en formularios adaptables. El servicio no admite formularios escaneados o rellenados. Para otras limitaciones, consulte el artículo <a href="known-issues.md">problemas conocidos</a>.<br /> </p> 
    <p>Con frecuencia, agregamos compatibilidad con otros tipos de fuentes. Mantenga la sección <a href="introduction.md">formularios PDF admitidos</a> en la lista de control para obtener una actualización regular de las funciones y capacidades recientemente agregadas.</p>

   El servicio solo puede convertir formularios en inglés, francés, alemán y español a formularios adaptables. Puede traducir los formularios adaptables que se generan a otro idioma mediante el [flujo de trabajo de traducción de AEM.](https://helpx.adobe.com/es/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **¿Puede el servicio producir un XDP en lugar de una forma adaptativa?**

   <p>El servicio no produce una salida XDP. Generalmente vamos a añadir funciones y al servicio. Mantenga la sección <a href="introduction.md">idiomas y PDF forms admitidos</a> en la lista de seguimiento para obtener una actualización regular de las funciones y capacidades recientemente agregadas.</p> <br>

1. **¿Cuál es el tipo de esquema generado?**

   <p>Puede utilizar el servicio para generar: </p>

   * un formulario adaptable enlazado a un esquema JSON y
   * un formulario adaptable no enlazado a ningún esquema <br><br>

1. **¿Puede el servicio convertir un formulario de Microsoft Word en formularios adaptables?**

   <p>No, el servicio no convierte un formulario de Microsoft Word a un formulario adaptable. Puede guardar un formulario de Microsoft Word en un formulario PDF y convertirlo en un formulario adaptable. El proceso completo es </p> <br>

   1. Utilice Adobe Acrobat para [convertir el documento de Word a un PDF no interactivo](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html).
   1. Utilice Adobe Acrobat para [convertir los PDF forms producidos en formularios PDF rellenables](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html).
   1. Utilice Adobe Acrobat para actualizar y corregir manualmente los campos del formulario.
   1. Guarde el formulario PDF. Ahora, puede utilizar el formulario con el servicio de conversión para generar un formulario adaptable. También puede utilizar el formulario como plantilla Documento de registro .


1. **¿Puede el servicio convertir formularios impresos escaneados y formularios coloreados en formularios adaptables?**

   <p>El servicio puede convertir PDF forms de color en formularios adaptables. El servicio no admite formularios escaneados o rellenados. Para ver otras limitaciones, consulte el artículo <a href="known-issues.md">problemas conocidos</a>.</p> <br>

1. **¿Puede el servicio convertir un formulario escaneado o solo una imagen de un formulario en un formulario adaptable?**

   <p>El servicio no admite la conversión de formularios escaneados o una imagen de un formulario a una configuración adaptativa lista para usar. Sin embargo, puede utilizar Adobe Acrobat para convertir la imagen de un formulario a un formulario PDF. Por lo tanto, use el servicio para convertir el formulario PDF a un formulario adaptativo. Utilice siempre una imagen de alta calidad del formulario para la conversión en Acrobat. Mejora la calidad de la conversión.</p> <br>

1. **Algunos formularios basados en XDP utilizan fragmentos de formulario, ¿dónde se deben cargar estos fragmentos de formulario?**

   <p class="MsoNormal">Cargue fragmentos de formulario en la carpeta de conversión y preserve la estructura de carpetas original. Ayuda a conservar las rutas relativas utilizadas en los formularios basados en XDP y en los fragmentos de formulario.</p> <br>

1. **¿Admite el servicio formularios XDP enlazados con esquema? Si tengo un XDP enlazado a un esquema, ¿necesito incrustar el esquema a XDP?**

   <p>Sí, el servicio admite formularios XDP enlazados a esquema y requiere que el esquema esté incrustado en el formulario XDP de origen. Al convertir un formulario XDP enlazado a esquema, el servicio genera un esquema JSON. El esquema JSON es estructuralmente similar al esquema XSD de los formularios XDP de origen.</p> <br>

1. **El servicio no ha podido convertir formularios. ¿Cuál es la razón y cómo resolver el problema?**
Los motivos más comunes para que la conversión falle son:
</p>
   * Se proporcionan PDF forms seguros para la conversión. No utilice PDF forms protegidos por contraseña o protegidos por contraseña para la conversión.
   * Se interrumpe la conexión a Internet. Asegúrese de estar conectado a Internet durante la conversión.
   * El PDF de origen tiene una imagen del formulario en lugar del formulario real.
   * El servicio está configurado incorrectamente, no se proporciona la dirección URL del servicio o la dirección URL del servicio es incorrecta. Compruebe la [configuración del servicio](configure-service.md#configure-the-cloud-service) en **[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**.
   * La configuración de IMS no está configurada correctamente. Compruebe el estado de la configuración de IMS para asegurarse de que funciona correctamente. Para comprobar si la configuración de IMS es correcta o no:
      1. Ir a `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. Seleccione la configuración. Haga clic en **[!UICONTROL Check Health]** en el encabezado y haga clic en **[!UICONTROL Check]**. Si se realiza correctamente, aparece el mensaje **[!UICONTROL Token retrieved successfully!]**. <br> <br>

1. **¿Afecta el uso de fuentes personalizadas a la conversión?**

   <p>Cuando un formulario PDF no interactivo se convierte en un formulario adaptable, para mejorar la calidad de la conversión, las fuentes se incrustan en el formulario PDF. La compatibilidad con la incrustación de fuentes está restringida a PDF forms no interactivos. Para optimizar la conversión de los PDF forms basados en AcroForm y XFA, se utilizan fuentes de reserva.</p> 
    <p>Solo los formularios disponibles en el directorio de fuentes personalizadas que se enumeran en el campo <strong>Directorio de fuentes del cliente</strong> de la configuración <strong> CQ-DAM-Handler-Gibson Font Manager Service</strong> están incrustados en el formulario PDF no interactivo.</p> 
    <p> </p> <br>

1. **¿El servicio identifica y utiliza fuentes del PDF de origen en los formularios adaptables de salida?**

   <p>El estilo y la presentación de un formulario HTML interactivo suelen ser diferentes de los formularios PDF o impresos. Para que el diseño y el estilo sean coherentes en todas las organizaciones, los formularios adaptables utilizan <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">temas para aplicar estilo a un formulario</a>. El servicio de conversión utiliza las fuentes y los estilos de fuente especificados en el tema aplicado durante la conversión. Puede cambiar las fuentes y los estilos de fuente del tema para proporcionar un aspecto y una apariencia distintos a los componentes de un formulario adaptable.</p> <br>

1. **¿El servicio extrae automáticamente JavaScript de formularios basados en XDP y lo aplica a los formularios adaptables correspondientes?**

   <p>El servicio no convierte automáticamente las secuencias de comandos de formularios basados en XFA o Acro Forms a las correspondientes reglas de formularios adaptables. Los autores de formularios pueden utilizar el <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">Editor de reglas</a> para agregar interactividad a un formulario adaptable.</p> <br>

1. **Algunos objetos de formulario no se convierten correctamente en componentes de formulario adaptables. ¿Cómo resolver el problema?**

   <p>El servicio de automated forms conversion está formado en un gran conjunto de formularios. Pero las aplicaciones basadas en IA/ML están limitadas por sus datos y patrones de capacitación. Puede haber múltiples tipos de campos, diseños, patrones y contexto perceptibles para la percepción humana, pero difícil para el reconocimiento automatizado. Es posible que el servicio no identifique dichos objetos o que los reconozca incorrectamente. Puede utilizar el editor <a href="review-correct-ui-edited.md" target="_blank">Revisar y corregir</a> para realizar las modificaciones necesarias en la presentación del formulario de entrada basada en formularios impresos habitual.</p> <br/>

1. **Algunas correcciones se repiten en los formularios. ¿Puede el servicio identificar y corregir todas estas instancias en conversiones futuras?**

   El servicio está formando constantemente sobre sus formularios y patrones. Aprende nuevos patrones a diario. Todavía no se han iniciado las correcciones de aplicación automática repetidas en los formularios. Esté atento a los formularios de prelanzamiento para la disponibilidad de dicha función. <br/><br/>

   Puede utilizar el metamodelo para asignar los objetos de formulario al componente de formulario adaptable de su elección y preconfigurar las validaciones, las reglas, los patrones de datos, el texto de ayuda y las propiedades de accesibilidad de los componentes. Todas las propiedades especificadas se aplican durante la conversión. Puede utilizar el metamodelo para aplicar propiedades comunes a los campos. Puede ayudarle a reducir algunos problemas repetidos en los formularios.<br/><br/>

1. **¿Cuáles son las opciones para formularios con datos confidenciales como información de identificación personal (PII)?**
El servicio solo admite formularios vacíos o sin rellenar. No cargue formularios rellenados o formularios con información de identificación personal (PII). Asimismo, elimine los datos precargados, la información de identificación personal (PII), la información confidencial y de propiedad en los formularios de origen. 
<br/>

1. **¿Dónde se deben colocar el encabezado y los pies de página?**

   <p>Colocar el encabezado y el pie de página en una plantilla de formularios adaptables. Si el formulario PDF de origen tiene encabezado y pie de página, el servicio detecta y reemplaza el encabezado y pie de página detectado por el encabezado y pie de página disponibles en la plantilla de formulario adaptable durante la conversión. Si se incluye algún encabezado o pie de página adicional en el formulario adaptable, puede utilizar el editor <a href="review-correct-ui-edited.md">Revisar y corregir</a> para corregir o eliminar dicho encabezado o pie de página.</p> <br />

1. **¿Cuánto tiempo ahorra el servicio en comparación con el proceso manual de planificación, creación de recursos (temas, plantillas), creación y publicación de un formulario adaptable?**

   <p>La cantidad de tiempo depende del tamaño y la complejidad de los formularios de entrada y del número de solicitudes. El servicio pretende reducir significativamente el tiempo de respuesta al valor convirtiendo a los PDF forms en formularios adaptables a un ritmo mucho más rápido en comparación con el proceso manual de conversión de formularios. </p> <br />

1. **¿Qué debo hacer si encuentro un error relacionado con las bibliotecas RSA? El mensaje de error es similar al mensaje mencionado a continuación:** <br/>

El error mencionado se produce cuando la delegación de arranque no está configurada para bibliotecas RSA/BouncyCastle. Realice los pasos siguientes para resolver el problema:   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
El error mencionado se produce cuando la delegación de arranque no está configurada para bibliotecas RSA/BouncyCastle. Realice los pasos siguientes para resolver el problema:
   <p> </p>

   1. Detenga la instancia de AEM. Vaya a la carpeta `[AEM installation directory]\crx-quickstart\conf\` . Abra el archivo sling.properties para editarlo. Si utiliza `[AEM installation directory]\crx-quickstart\bin\start.bat` para iniciar una instancia de AEM, edite las propiedades sling que se encuentran en `[AEM_root]\crx-quickstart\`.
   1. Agregue las siguientes propiedades al archivo sling.properties:<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. Guarde y cierre el archivo. <br/>
   1. Inicie la instancia de AEM.<br/>

   <br/>

1. **¿Cómo se cambia automáticamente el formato de mayúsculas y minúsculas del texto del formulario adaptable?**

   <p>Se puede utilizar la función adaptativa de los temas o el editor de estilos para cambiar el formato de un campo de forma adaptable. Por ejemplo, puede abrir el editor de temas y establecer el valor de la propiedad Case de todo el texto del formulario en mayúsculas, minúsculas o camelCase. También puede utilizar la opción Sustitución de CSS en el editor de temas para crear distintos tipos de estilos.</p>

1. **¿Puedo utilizar etiquetas de texto de Adobe Sign con el servicio de Automated forms conversion?**

   <p> Cuando se utiliza el servicio de Automated forms conversion para convertir un formulario PDF en un formulario adaptable y el formulario PDF tiene etiquetas de texto Adobe Sign, dichas etiquetas se convierten a los campos de formulario adaptables correspondientes y los detalles del firmante se rellenan automáticamente.  La función solo está disponible para Acro Forms y los formularios adaptables admiten un número limitado de campos de Adobe Sign.</p>  </br>

1. **¿Cómo se crea un formulario PDF habilitado para Adobe Sign?**

   </p>Para crear un formulario PDF habilitado para Adobe Sign:</p>

   Agregue [etiquetas de texto de Adobe Sign](https://helpx.adobe.com/sign/using/text-tag.html) a los nombres de campo o utilice la opción [Convertir a formulario de Adobe Sign](https://helpx.adobe.com/sign/using/create-forms-with-acrobat.html).
