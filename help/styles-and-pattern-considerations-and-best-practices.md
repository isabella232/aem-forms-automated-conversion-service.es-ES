---
title: 'Prácticas recomendadas y consideraciones '
seo-title: 'Prácticas recomendadas y consideraciones '
description: Prácticas recomendadas y consideraciones del servicio de Automated forms conversion
seo-description: Lista de estilos y patrones en los PDF forms de origen que el servicio de Automated forms conversion encuentra difícil de identificar
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
exl-id: 9ada091a-e7c6-40e9-8196-c568f598fc2a
source-git-commit: c070651253877408466231ab80a6b7e0d04a9fab
workflow-type: tm+mt
source-wordcount: '1257'
ht-degree: 3%

---

# Prácticas recomendadas y patrones complejos conocidos {#Best-practices-and-considerations2}

Este documento proporciona directrices y recomendaciones de las que pueden beneficiarse el administrador de formularios, los autores y los desarrolladores al trabajar con [!DNL Automated Forms Conversion service]. Se analizan las prácticas recomendadas, desde la preparación de formularios de origen hasta la corrección de patrones complejos que requieren un esfuerzo adicional para la conversión automatizada. Estas prácticas recomendadas contribuyen colectivamente al rendimiento general y a la salida de [!DNL Automated Forms Conversion service].

## Prácticas recomendadas

El servicio de conversión convierte los PDF forms disponibles en la instancia de AEM [!DNL Forms] a formularios adaptables. Las prácticas recomendadas que se enumeran a continuación le ayudan a mejorar la velocidad y precisión de conversión. Además, estas prácticas recomendadas le ayudan a ahorrar tiempo invertido en las actividades posteriores a la conversión.

### Antes de cargar el origen

Puede cargar todos los PDF forms a la vez o de forma gradual, según sea necesario. Antes de cargar los formularios, tenga en cuenta lo siguiente:

* Mantenga el número de formularios en una carpeta por debajo de 15 y conserve el número total de páginas en una carpeta por debajo de 50.
* Mantenga el tamaño de la carpeta por debajo de 10 MB. No guarde formularios en una subcarpeta.
* Mantenga el número de páginas en un formulario por debajo de 15.
* Organice los documentos de origen en un lote de 8 a 15 documentos. Mantener los formularios de origen con fragmentos de formulario adaptables comunes en un único lote.
* No cargue los formularios protegidos. El servicio no convierte formularios protegidos por contraseña y protegidos por contraseña.
* No cargue los [Portfolio PDF](https://helpx.adobe.com/es/acrobat/using/overview-pdf-portfolios.html). El servicio no convierte un Portfolio PDF a un formulario adaptable.
* No cargue formularios escaneados y rellenados. Estas clases de formulario no se admiten.
* No cargue formularios de origen con espacios en el nombre de archivo. Quite el espacio del nombre del archivo antes de cargar los formularios.

Cuando utilice un formulario XDP para la conversión, realice los siguientes pasos antes de cargar los formularios XPD de origen:

* Analice el formulario XDP y corrija problemas visuales. Asegúrese de que el documento de origen utiliza los controles y estructuras deseados. Por ejemplo, el formulario de origen puede tener casillas de verificación en lugar de botones de opción para una sola selección. Cambie las casillas de verificación por botones de opción para crear un formulario adaptable con los componentes deseados.
* [Agregue enlaces al ](http://www.adobe.com/go/learn_aemforms_designer_65) formulario XDP antes de iniciar la conversión. Cuando los enlaces están disponibles en el formulario XDP de origen, el servicio aplica automáticamente los enlaces a los campos de formulario adaptables correspondientes durante la conversión. Le ahorra el tiempo necesario para aplicar manualmente los enlaces.
* [Agregue ](https://helpx.adobe.com/sign/using/text-tag.html) etiquetas de Adobe Sign al archivo XDP. El servicio convierte automáticamente las etiquetas de Adobe Sign en los campos de formulario adaptables correspondientes. Forms adaptable admite un número limitado de campos de Adobe Sign. Para obtener la lista completa de los campos admitidos, consulte la documentación [Uso de Adobe Sign en un formulario adaptable](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html?lang=en) .
* Convierta tablas complejas en documentos XDP en tablas simples, si es posible. Una tabla con campos de formulario en celdas de tabla, celdas de tamaño desigual, celdas distribuidas en filas o columnas, celdas combinadas, bordes parciales o sin borde visible se considera una tabla compleja. Una tabla con cualquiera de los elementos mencionados anteriormente se considera una tabla compleja.
<!-- * Use sub-forms in XDP documents to create panels in adaptive forms. Service converts each sub-form to one or more adaptive form panels during conversion. -->

### Antes de iniciar la conversión

* Cree plantillas de formulario adaptables. Las plantillas ayudan a especificar una estructura uniforme para los formularios de su organización o departamento.
* Especifique el encabezado y el pie de página en las plantillas de formulario adaptables. El servicio ignora el encabezado y pie de página de los documentos de origen y utiliza el encabezado y pie de página especificados en la plantilla de formulario adaptable.
* Cree temas de formulario adaptables. Los temas ayudan a proporcionar una apariencia uniforme a las formas de su organización o departamento.
* Configure el Modelo de datos de formulario para guardar y recuperar desde un origen de datos. Cree y configure servicios de lectura y escritura para el Modelo de datos de formulario.
* Cree fragmentos de formulario adaptables y configure el servicio para que utilice sus fragmentos de formulario adaptables.
* Prepare modelos de flujo de trabajo comunes para los formularios que requieran automatización de procesos empresariales.
* Configure Adobe Analytics, si es necesario


## Conocer los patrones complejos

AEM [!DNL Forms Automated Conversion service] utiliza inteligencia artificial y algoritmos de aprendizaje automático para comprender el diseño y los campos del formulario de origen. Cada servicio de aprendizaje automático aprende continuamente de los datos de origen y produce una salida mejorada con cada pérdida. Estos servicios aprenden de la experiencia como humanos.

[!DNL Automated Forms Conversion service] está formado en un gran conjunto de formularios. Identifica fácilmente los campos de un formulario de origen y produce formularios adaptables. Sin embargo, hay algunos campos y estilos en los PDF forms que son fácilmente visibles para el ojo humano pero difíciles de entender para el servicio. El servicio puede asignar diferentes tipos de campos o paneles aplicables a algunos campos o estilos. A continuación se enumeran todos estos patrones de estilo y campo.

El servicio empezaría a identificar y asignar los campos o paneles correctos a estos patrones a medida que sigue aprendiendo de los datos de origen. Por el momento, puede utilizar el editor [Revisar y corregir](review-correct-ui-edited.md) para solucionar estos problemas. Antes de empezar a corregir los problemas o a leer más, familiarícese con [los componentes de formulario adaptables](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html).

### Patrones generales {#general}

| Patrón | Ejemplo |
|--- |--- |
| **** <br>PatternService no convierte los PDF forms rellenos a un formulario adaptable. <br><br>**** <br>SoluciónUtilice formularios adaptables vacíos. | ![Formulario rellenado](assets/best-practice-filled-forms.png) |
| **** <br>PatternService puede no reconocer el texto y los campos de forma densa. <br><br>**** <br> SoluciónAumente la anchura entre el texto y los campos de un formulario denso antes de iniciar la conversión. |  |
| **** <br>PatternService no admite formularios escaneados. <br><br>**** <br>SoluciónNo utilice formularios escaneados. | ![Formulario digitalizado](assets/scanned-forms.png) |
| **** <br>PatternService no extrae imágenes ni texto en imágenes. <br><br>**** <br> SoluciónAgregue manualmente imágenes o texto a formularios convertidos. | ![Imagen con texto Formulario](assets/best-practice-image-with-text.png) |
| **** <br>Las tablas de patrones con límites y bordes punteados o no claros no se convierten. <br><br>**** <br>SoluciónUtilice tablas con límites y bordes explícitos claros. compatible. | ![Formulario de tabla no transparente](assets/best-practice-table-dotted-non-clear.png) |
| **** <br> PatrónLos formularios adaptables no admiten texto vertical. Por lo tanto, el servicio no convierte el texto vertical al texto correspondiente de Adaptive Forms. <br><br>**** <br> SoluciónUtilice el editor de formularios adaptables para agregar texto vertical, si es necesario. | ![Formulario de tabla no transparente](assets/vertical-text.png) |



### Grupo de opciones  {#choice-group}

| Patrón | Resolución |
|--- |--- |
| **** <br> Las opciones de grupo PatternChoice con formas que no sean cuadro o círculo no se convierten a los componentes de formulario adaptables correspondientes. <br><br>**** <br> SoluciónCambie las opciones de las formas para que estén en cuadro o en círculo, o utilice el editor Revisar y corregir para identificar las formas. | ![Campos de opciones  ](assets/best-practice-choice-group-options.png) |

### Campos de formulario {#form-fields}

| Patrón | Resolución |
|--- |--- |
| **** <br> PatternService no identifica campos sin bordes claros. <br><br>**** <br> SoluciónUtilice el editor de revisiones y correcciones para identificar dichos campos. | ![campos con límites no claros](assets/best-practice-fields-without-clear-borders.png) |
| **** <br> Puede que PatternService no identifique algunos campos de formulario de grupo de opciones con rótulos en la parte inferior o derecha de un formulario. <br><br>**** <br> SoluciónUtilice el editor de revisiones y correcciones para identificar dichos campos | ![Campos de opciones](assets/best-practice-caption-bottom-right.png) |
| **** <br> PatternService combina o asigna un tipo incorrecto a algunos campos de formulario que están muy cerca entre sí o que no tienen bordes claros. <br><br>**** <br> SoluciónUtilice el editor de revisiones y correcciones para identificar dichos campos. | ![Campos de opciones](assets/best-practice-placed-very-near.png) |
| **** <br> PatternService puede no reconocer campos con rótulos lejanos o una línea de puntos entre el rótulo y el campo de entrada. <br><br>**** <br> SoluciónUtilice campos de formulario con límites claros o utilice el editor Revisar y corregir para solucionar estos problemas. | ![Campos alejados o línea de puntos entre campos de rótulo](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### Listas {#lists}

| Patrón | Resolución |
|--- |--- |
| **** <br>PatrónLas listas que contienen campos de formulario se combinan o no se convierten a los componentes de formulario adaptable correspondientes  <br><br>**** <br>ResoluciónUtilice campos de formulario con límites claros o utilice el editor de revisiones y correcciones para solucionar estos problemas. | ![listas que contienen grupos de opciones](assets/best-practice-lists-containing-form-fields.png) |
| **** <br>PatternService puede dejar algunas listas anidadas sin identificar  <br><br>**** <br> ResoluciónUtilice el editor de revisiones y correcciones para solucionar estos problemas. | ![listas que contienen grupos de opciones](assets/best-practice-nested-lists.png) |
| **** <br> PatternService combina algunas listas que contienen grupos de opciones entre sí  <br><br>**** <br> SoluciónUtilice el editor de revisiones y correcciones para solucionar estos problemas. | ![listas que contienen grupos de opciones](assets/best-practice-check-box-in-table-cells.png) |

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fields without borders are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->
