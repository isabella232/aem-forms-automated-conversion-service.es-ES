---
title: Preguntas frecuentes
description: Consultas comunes o preguntas frecuentes
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: introduction
role: Admin, Developer
level: Beginner, Intermediate
exl-id: 3a29f8d4-8ea0-49eb-bfe0-0eab5f0c52c7
source-git-commit: e95b4ed35f27f920b26c05f3398529f825948f1f
workflow-type: tm+mt
source-wordcount: '1799'
ht-degree: 99%

---

# Preguntas frecuentes{#frequently-asked-questions}

1. **¿Qué versión de AEM Forms es compatible con el servicio de conversión automatizada de formularios?**
   <p>El servicio de conversión automatizada de formularios es compatible con AEM 6.4 Forms y AEM 6.5 Forms. Funciona tanto con AEM Forms en OSGi como con AEM Forms en JEE. Para utilizar el servicio, necesita el último paquete de complementos de AEM Forms que se encuentra en la instancia de autor de AEM. Para obtener instrucciones detalladas, consulte <a href="configure-service.md">Configurar el servicio de conversión automatizada de formularios</a>.</p> 
    <br>

1. **¿Se puede instalar el servicio de forma local?**
   <p>Adobe forma regularmente algoritmos de IA y ML del servicio de conversión automatizada de formularios con nuevos datos para mejorar la precisión de conversión. Los algoritmos actualizados se implementan en el servicio de conversión que se ejecuta en Adobe Cloud periódicamente. Todos los clientes del servicio se benefician de los algoritmos actualizados. Por lo tanto, la implementación central alojada en la nube es la más adecuada para que el servicio de conversión automatizada de formularios aprenda y ofrezca mejoras de forma continua a todos los clientes.</p> 
    <p>El servicio convierte los formularios en blanco en formularios adaptables. El servicio no es compatible con formularios rellenados ni con la extracción de datos de formularios rellenados. Elimine los datos de los formularios rellenados y elimine o incluya en la lista de permitidos la información de propiedad de los formularios antes de enviar los formularios al servicio para su conversión.</p> <br>

1. **¿Es compatible el servicio con todos los formatos de formularios PDF? ¿Qué idiomas son compatibles?**
   <p>El servicio puede convertir formularios PDF no interactivos, formularios XDP y PDF basados en XFA y AcroForms en formularios adaptables. El servicio no es compatible con formularios escaneados o rellenados. Para otras limitaciones, consulte el artículo <a href="known-issues.md">Problemas conocidos</a>.<br /> </p> 
    <p>Se agregan compatibilidades con otros tipos de fuentes con frecuencia. Consulte la sección <a href="introduction.md">formularios PDF compatibles</a> con regularidad para mantenerse informado sobre las funciones y características nuevas.</p>

   El servicio solo puede convertir a formularios adaptables los formularios que estén en inglés, francés, alemán, español, italiano y portugués. Puede traducir los formularios adaptables que se generan a otro idioma mediante el [flujo de trabajo de traducción de AEM.](https://helpx.adobe.com/es/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **¿Puede el servicio producir un XDP en lugar de un formulario adaptativo?**
   <p>El servicio no produce un XDP como resultado. Se agregan con frecuencia características al servicio. Consulte la sección <a href="introduction.md">formularios PDF e idiomas compatibles</a> con regularidad para mantenerse informado sobre las funciones y características nuevas.</p> <br>

1. **¿Cuál es el tipo de esquema generado?**
   <p>Puede utilizar el servicio para generar lo siguiente: </p>

   * un formulario adaptable enlazado a un esquema JSON y
   * un formulario adaptable no enlazado a ningún esquema.<br><br>

1. **¿Puede el servicio convertir un formulario de Microsoft Word en un formulario adaptable?**
   <p>No, el servicio no convierte un formulario de Microsoft Word a un formulario adaptable. Puede guardar un formulario de Microsoft Word como un formulario PDF y convertir este último en uno adaptable. El proceso completo es el siguiente: </p> <br>

   1. Utilice Adobe Acrobat para [convertir el documento de Word en un PDF no interactivo](https://helpx.adobe.com/es/acrobat/how-to/create-pdf-files-word-excel-website.html).
   1. Utilice Adobe Acrobat para [convertir el formulario PDF producido en un formulario PDF rellenable](https://helpx.adobe.com/es/acrobat/how-to/convert-word-excel-paper-pdf-forms.html).
   1. Utilice Adobe Acrobat para actualizar y corregir manualmente los campos del formulario.
   1. Guarde el formulario PDF. Ahora ya podrá utilizarlo con el servicio de conversión para generar un formulario adaptable. También puede utilizar el formulario como plantilla de un Documento de registro.


1. **¿Puede el servicio convertir formularios impresos escaneados y formularios con colores en formularios adaptables?**
   <p>El servicio solo puede convertir a formularios adaptables formularios PDF de colores. El servicio no es compatible con formularios escaneados o rellenados. Para otras limitaciones, consulte el artículo <a href="known-issues.md">Problemas conocidos</a>.</p> <br>

1. **¿Puede el servicio convertir un formulario escaneado o solo una imagen de un formulario en un formulario adaptable?**
   <p>El servicio no admite la conversión de formularios escaneados o con imágenes en un formulario adaptable. Sin embargo, puede utilizar Adobe Acrobat para convertir la imagen de un formulario a un formulario PDF. Por lo tanto, use el servicio para convertir el formulario PDF a un formulario adaptativo. Utilice siempre una imagen de alta calidad del formulario para la conversión en Acrobat. Mejora la calidad de la conversión.</p> <br>

1. **Algunos formularios basados en XDP utilizan fragmentos de formulario, ¿dónde se deben cargar estos fragmentos de formularios?**
   <p class="MsoNormal">Cargue fragmentos de formularios en la carpeta de conversión y preserve la estructura de carpetas original. Ayuda a conservar las rutas relativas utilizadas en los formularios basados en XDP y en los fragmentos de formulario.</p> <br>

1. **¿Admite el servicio los formularios XDP enlazados con esquema? Si tengo un XDP enlazado a un esquema, ¿necesito incrustar el esquema a XDP?**
   <p>Sí, el servicio admite formularios XDP enlazados a esquema y requiere que el esquema esté incrustado en el formulario XDP de origen. Al convertir un formulario XDP enlazado a esquema, el servicio genera un esquema JSON. El esquema JSON tiene una estructura similar al esquema XSD de los formularios XDP de origen.</p> <br>

1. **El servicio no pudo convertir los formularios. ¿Cuál es la razón y cómo resolver el problema?**
Los motivos más comunes para que la conversión falle son los siguientes:</p>
   * Los formularios PDF proporcionados para la conversión están protegidos. No utilice los formularios PDF protegidos por contraseña para la conversión.
   * La conexión a internet no es estable. Asegúrese de estar conectado a internet durante la conversión.
   * El PDF de origen tiene una imagen del formulario en lugar del formulario original.
   * El servicio está configurado incorrectamente, no se proporciona la dirección URL del servicio o esta es incorrecta. Compruebe la [configuración del servicio](configure-service.md#configure-the-cloud-service) en **[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**.
   * La configuración de IMS no está configurada correctamente. Compruebe el estado de la configuración de IMS para asegurarse de que funcione correctamente. Para comprobar si la configuración de IMS es correcta o no, haga lo siguiente:
      1. Vaya a `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. Seleccione la configuración. Haga clic en **[!UICONTROL Check Health]** del encabezado y en **[!UICONTROL Check]**. Si tiene éxito, obtendrá el siguiente mensaje **[!UICONTROL Token retrieved successfully!]**. <br> <br>

1. **¿Afecta el uso de fuentes personalizadas a la conversión?**
   <p>Cuando un formulario PDF no interactivo se convierte en uno adaptable, para mejorar la calidad de la conversión, las fuentes se incrustan en el formulario PDF. La compatibilidad con la incrustación de fuentes está restringida a los formularios PDF no interactivos. Para optimizar la conversión de los formularios PDF basados en AcroForm y en XFA, se utilizan fuentes de reserva.</p> 
    <p>Solo los formularios disponibles en el directorio de fuentes personalizadas que aparecen en el campo <strong>Directorio de fuentes del cliente</strong> de la configuración <strong>Servicio de gestión de fuentes CQ-DAM-Handler-Gibson</strong> están incrustados en un formulario PDF no interactivo.</p> 
    <p> </p> <br>

1. **¿El servicio identifica y utiliza las fuentes del PDF de origen en los formularios adaptables de salida?**
   <p>El estilo y diseño de un formulario HTML interactivo suele ser diferente al de un PDF o al un formulario en papel. Para que el diseño y el estilo sean coherentes en todas las organizaciones, los formularios adaptables utilizan <a href="https://helpx.adobe.com/es/experience-manager/6-5/forms/using/themes.html">temáticas para aplicar los estilos a un formulario</a>. El servicio de conversión utiliza las fuentes y los estilos de fuente especificados en el tema aplicado durante la conversión. Puede cambiar las fuentes y los estilos de fuente del tema para proporcionar una apariencia distinta a los componentes del formulario adaptable.</p> <br>

1. **¿El servicio extrae automáticamente JavaScript de los formularios basados en XDP y lo aplica a los formularios adaptables correspondientes?**
   <p>El servicio no convierte automáticamente los scripts de los formularios basados en XFA o en AcroForms a las correspondientes reglas de formularios adaptables. Los autores de formularios pueden usar el <a href="https://helpx.adobe.com/es/experience-manager/6-5/forms/using/rule-editor.html">Editor de reglas</a> para que el formulario adaptable sea interactivo.</p> <br>

1. **Algunos objetos del formulario no se convierten correctamente en los componentes de formulario adaptables. ¿Cómo solucionar el problema?**
   <p>El servicio de conversión automatizada de formularios se entrena con un amplio conjunto de formularios. Sin embargo, las aplicaciones basadas en IA/ML están limitadas por sus datos y patrones de capacitación. Puede haber múltiples tipos de campos, diseños, patrones y contexto perceptibles para las personas, pero difíciles de captar para el reconocimiento automatizado. Es posible que el servicio no identifique dichos objetos o que los reconozca incorrectamente. Puede usar el editor <a href="review-correct-ui-edited.md" target="_blank">Revisar y corregir</a> para realizar las modificaciones necesarias en la presentación del formulario de entrada basado en formularios impresos que ya posee.</p> <br/>

1. **Algunas de las correcciones se repiten en el resto de los formularios. ¿Puede el servicio identificar y corregir todas estas instancias en conversiones futuras?**

   El servicio ofrece formación constante sobre los formularios y patrones. A diario incorpora patrones nuevos. Todavía no se aplican de forma automática las correcciones repetidas en los formularios. Esté atento a las versiones preliminares de los formularios para la disponibilidad de dicha función. <br/><br/>

   Puede utilizar el metamodelo para asignar los objetos del formulario al componente de formulario adaptable que usted elija y configurar previamente las validaciones, las reglas, los patrones de datos, el texto de ayuda y las propiedades de accesibilidad de los componentes. Todas las propiedades especificadas se aplicarán durante la conversión. Puede utilizar el metamodelo para aplicar propiedades comunes a los campos. Esto puede ayudarle a reducir algunos problemas que se repitan en los formularios.<br/><br/>

1. **¿Cuáles son las opciones para los formularios con datos confidenciales, como la información de identificación personal (PII)?**
El servicio solo admite formularios vacíos o sin rellenar. No cargue formularios rellenados o con información de identificación personal (PII). Asimismo, elimine de los formularios de origen los datos que se hayan agregado anteriormente, la información de identificación personal (PII), la confidencial y la información sujeta a derechos de propiedad. <br/>

1. **¿Dónde se deben colocar los encabezados y los pies de página?**
   <p>Coloque el encabezado y el pie de página en una plantilla de formularios adaptables. Si el formulario PDF de origen ya tiene un encabezado y pie de página, el servicio los detecta y los reemplaza durante la conversión por los disponibles en la plantilla de formulario adaptable. Si algún encabezado o pie de página adicional están incluidos en el formulario adaptable, puede usar la opción <a href="review-correct-ui-edited.md">Revisar y corregir</a> para corregir o eliminar dicho encabezado o pie de página.</p> <br />

1. **¿Cuánto tiempo ahorra este servicio en comparación con el proceso manual de planificación, creación de recursos (temas, plantillas), creación y publicación de un formulario adaptable?**
   <p>La cantidad de tiempo depende del tamaño y la complejidad de los formularios de entrada y del número de solicitudes. El servicio pretende reducir significativamente el tiempo de respuesta al valor, convirtiendo a los formularios PDF en formularios adaptables a un ritmo mucho más rápido, en comparación con el proceso manual de conversión de formularios. </p> <br />

1. **¿Qué debo hacer si encuentro un error relacionado con las bibliotecas RSA? El mensaje de error es similar al mensaje que se menciona a continuación:** <br/>
   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
El error mencionado se produce cuando la delegación de arranque no está configurada para las bibliotecas RSA/BouncyCastle. Siga estos pasos para resolver el problema:
   <p> </p>

   1. Detenga la instancia de AEM. Navegue hasta la carpeta `[AEM installation directory]\crx-quickstart\conf\`. Abra el archivo sling.properties para editarlo. Si usa `[AEM installation directory]\crx-quickstart\bin\start.bat` para iniciar una instancia de AEM, edite el archivo sling.properties ubicado en `[AEM_root]\crx-quickstart\`.
   1. Agregue las siguientes propiedades al archivo sling.properties:<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. Guarde y cierre el archivo. <br/>
   1. Inicie la instancia de AEM nuevamente.<br/>
   <br/>

1. **¿Cómo se cambia automáticamente el formato de mayúsculas y minúsculas del texto del formulario adaptable?**
   <p>Se puede utilizar el editor de temáticas o estilos del formulario adaptable para cambiar el formato del campo de un formulario adaptable. Por ejemplo, puede abrir el editor de temáticas y establecer el valor de la propiedad de formato de todo el texto del formulario en mayúsculas, minúsculas o camel Case. También puede utilizar la opción sustitución de CSS en el editor de temáticas para crear distintos tipos de estilos.</p>

1. **¿Puedo utilizar las etiquetas de texto de Adobe Sign con el servicio de conversión automática de formularios?**
   <p> Cuando se utiliza el servicio de conversión automática de formularios para convertir un formulario PDF en uno adaptable y el formulario PDF tiene etiquetas de texto de Adobe Sign, dichas etiquetas se convierten a los campos de formulario adaptables correspondientes y los detalles de la persona que firma se rellenan automáticamente. La función solo está disponible para AcroForms y los formularios adaptables admiten un número limitado de campos de Adobe Sign.</p>  </br>

1. **¿Cómo se crea un formulario de PDF habilitado para Adobe Sign?**
   </p>Para crear un formulario de PDF habilitado para Adobe Sign, haga lo siguiente:</p>

   Agregue [etiquetas de texto de Adobe Sign](https://helpx.adobe.com/es/sign/using/text-tag.html) para los nombres de campo o use la opción [Convertir en formulario de Adobe Sign](https://helpx.adobe.com/es/sign/using/create-forms-with-acrobat.html).
