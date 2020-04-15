---
title: 'Prácticas recomendadas y consideraciones '
seo-title: 'Prácticas recomendadas y consideraciones '
description: Prácticas recomendadas y consideraciones para el servicio Conversión automatizada de formularios
seo-description: Lista de estilos y patrones en formularios PDF de origen que el servicio Conversión automatizada de formularios encuentra difícil de identificar
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
translation-type: tm+mt
source-git-commit: 12b4df8feb19fdc6e723c4d7301d299f26676716

---


# Prácticas recomendadas y patrones complejos conocidos {#Best-practices-and-considerations2}

Este documento proporciona directrices y recomendaciones de las que pueden beneficiarse los administradores, autores y desarrolladores de formularios al trabajar con el servicio Conversión automatizada de formularios. Se analizan las prácticas recomendadas desde la preparación de formularios de origen hasta la corrección de patrones complejos que requieren un esfuerzo adicional para la conversión automatizada. Estas optimizaciones contribuyen de forma colectiva al rendimiento general y al resultado del servicio de conversión automatizada de formularios.

## Prácticas recomendadas  

El servicio de conversión convierte los formularios PDF disponibles en la instancia de AEM Forms en formularios adaptables. Las optimizaciones que se enumeran a continuación le ayudan a mejorar la velocidad y la precisión de conversión. Además, estas optimizaciones le ayudan a ahorrar tiempo empleado en actividades posteriores a la conversión.

### Antes de cargar formularios de origen
Puede cargar todos los formularios PDF de una vez o de forma gradual, según sea necesario. Antes de cargar los formularios, tenga en cuenta lo siguiente:

* Mantenga el número de formularios en una carpeta por debajo de 15 y el número total de páginas en una carpeta por debajo de 50.
* Mantenga el tamaño de la carpeta por debajo de los 10 MB. No mantenga los formularios en una subcarpeta.
* Mantenga el número de páginas de un formulario por debajo de 15.
* Organizar documentos de origen en un lote de 8 a 15 documentos. Mantener formularios de origen con fragmentos de formulario adaptables comunes en un solo lote.
* No cargue los formularios protegidos. El servicio no convierte formularios protegidos por contraseña ni protegidos por contraseña.
* Do not upload the [PDF Portfolios](https://helpx.adobe.com/es/acrobat/using/overview-pdf-portfolios.html). El servicio no convierte una cartera PDF a un formulario adaptable.
* No cargue formularios escaneados, coloreados, que no estén en inglés ni rellenados. Estas clases de formulario no se admiten.
* No cargue formularios de origen con espacios en el nombre del archivo. Quite el espacio del nombre del archivo antes de cargar los formularios.

Cuando utilice un formulario XDP para la conversión, realice los siguientes pasos antes de cargar los formularios XPD de origen:

* Analice el formulario XDP y corrija problemas visuales. Asegúrese de que el documento de origen utilice los controles y estructuras deseados. Por ejemplo, el formulario de origen puede tener casillas de verificación en lugar de botones de opción para una sola selección. Cambie las casillas de verificación por botones de opción para crear un formulario adaptable con los componentes deseados.
* [Añada enlaces al formulario](http://www.adobe.com/go/learn_aemforms_designer_65) XDP antes de iniciar la conversión. Cuando los enlaces están disponibles en el formulario XDP de origen, el servicio aplica automáticamente los enlaces a los campos de formulario adaptables correspondientes durante la conversión. Le ahorra el tiempo necesario para aplicar manualmente los enlaces.
* [Añada las etiquetas](https://helpx.adobe.com/sign/using/text-tag.html) de Adobe Sign en el archivo XDP. El servicio convierte automáticamente las etiquetas de Adobe Sign en los campos de formulario adaptables correspondientes. Los formularios adaptables admiten un número limitado de campos de Adobe Sign. Para obtener la lista completa de los campos admitidos, consulte [Uso de Adobe Sign en la documentación de un formulario](https://docs.adobe.com/content/help/en/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html) adaptable.
* Utilice subformularios en documentos XDP para crear paneles en formularios adaptables. Service convierte cada subformulario en un panel de formulario adaptable durante la conversión.
* Convierta tablas complejas en documentos XDP en tablas simples, si es posible.

### Antes de realizar el inicio de la conversión

* Cree plantillas de formulario adaptables. Las plantillas ayudan a especificar una estructura uniforme para los formularios de su organización o departamento.
* Especifique el encabezado y el pie de página en las plantillas de formulario adaptables. El servicio omite el encabezado y el pie de página de los documentos de origen y utiliza el encabezado y el pie de página especificados en la plantilla de formulario adaptable.
* Crear temáticas de formulario adaptables. Las Temáticas ayudan a proporcionar una apariencia uniforme a las formas de su organización o departamento.
* Configure el modelo de datos de formulario para guardar y recuperar datos de un origen de datos. Cree y configure servicios de lectura y escritura para el modelo de datos de formulario.
* Cree fragmentos de formulario adaptables y configure el servicio para que utilice sus fragmentos de formulario adaptables.
* Prepare modelos de flujo de trabajo comunes para los formularios que requieren la automatización de procesos empresariales.
* Configurar Adobe Analytics, si es necesario


## Conocer patrones complejos

El servicio de conversión automatizada de AEM Forms utiliza inteligencia artificial y algoritmos de aprendizaje automático para comprender la presentación y los campos del formulario de origen. Cada servicio de aprendizaje automático aprende continuamente de los datos de origen y produce una salida mejorada con cada repetición. Estos servicios aprenden de la experiencia como humanos.

El servicio Conversión automatizada de formularios se capacita en un gran conjunto de formularios. Identifica fácilmente los campos de un formulario de origen y genera formularios adaptables. Sin embargo, hay algunos campos y estilos en formularios PDF que son fácilmente visibles para el ojo humano pero difíciles de entender para el servicio. El servicio puede asignar tipos de campos o paneles diferentes de los aplicables a algunos campos o estilos. Todos estos patrones de estilo y campo se enumeran a continuación.

El servicio tiene el inicio de identificar y asignar los campos o paneles correctos a estos patrones, ya que sigue aprendiendo de los datos de origen. Por el momento, puede utilizar el editor [Revisar y corregir](review-correct-ui-edited.md) para corregir estos problemas. Antes de inicio de corregir los problemas o leer más, familiarícese con los componentes [de formulario](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)adaptables.

### Patrones generales {#general}

| Patrón | Ejemplo |
|--- |--- |
| **El servicio de patrones** <br> no convierte los formularios PDF de color en formularios adaptables. <br><br>**Resolución **<br>Utilice formularios PDF en blanco y negro o en escala de grises. | ![Formulario en color](assets/best-practice-coloured-forms.png) |
| **El** servicio de patrones <br>no convierte los formularios PDF rellenados en formularios adaptables. <br><br>**Resolución **<br>Utilice formularios adaptables vacíos. | ![Formulario rellenado](assets/best-practice-filled-forms.png) |
| **El** servicio de patrones <br>puede no reconocer texto y campos de forma densa. <br><br>**Resolución **<br>Aumente la anchura entre el texto y los campos de un formulario denso antes de iniciar la conversión. |  |
| **El** servicio de patrones <br>no admite formularios digitalizados. <br><br>**Resolución **No<br>utilice formularios digitalizados. | ![Formulario digitalizado](assets/scanned-forms.png) |
| **El** servicio de patrones <br>no extrae imágenes ni texto en las imágenes. <br><br>**Resolución **<br>Agregue imágenes o texto manualmente a los formularios convertidos. | ![Imagen con texto Formulario](assets/best-practice-image-with-text.png) |
| **No se convierten** las tablas de patrones <br>con bordes y contornos de puntos o no claros. <br><br>**Resolución **<br>Utilice tablas con bordes y límites explícitos claros. compatible. | ![Formulario de tabla no transparente](assets/best-practice-table-dotted-non-clear.png) |
| **Patrón**<br> El formulario adaptable no admite texto vertical fuera del cuadro. Por lo tanto, el servicio no convierte el texto vertical al texto correspondiente de formularios adaptables. <br><br>**Resolución **<br>Utilice el editor de formularios adaptables para agregar texto vertical, si es necesario. | ![Formulario de tabla no transparente](assets/vertical-text.png) |



### Grupo de opciones {#choice-group}

| Patrón | Resolución |
|--- |--- |
| **Patrón** <br> Las opciones de grupo de opciones con formas distintas de cuadro o círculo no se convierten en los componentes de formulario adaptables correspondientes. <br><br>**Resolución **<br>Cambie las formas de opciones de opciones a cuadro o círculo o utilice el editor Revisar y corregir para identificar las formas. | ![Campos de opciones ](assets/best-practice-choice-group-options.png) |

### Form fields {#form-fields}

| Patrón | Resolución |
|--- |--- |
| **El servicio de patrones** <br> no identifica campos sin bordes claros. <br><br>**Resolución **<br>Utilice el editor Revisar y corregir para identificar dichos campos. | ![campos con límites no claros](assets/best-practice-fields-without-clear-borders.png) |
| **Puede que el servicio de patrones** <br> no identifique algunos campos de formulario de grupo de opciones con rótulos en la parte inferior o derecha de un formulario. <br><br>**Resolución **<br>Utilice el editor Revisar y corregir para identificar dichos campos | ![Campos de opciones](assets/best-practice-caption-bottom-right.png) |
| **El servicio de patrones** <br> combina o asigna un tipo incorrecto a algunos campos de formulario que están muy cerca entre sí o que no tienen bordes claros. <br><br>**Resolución **<br>Utilice el editor Revisar y corregir para identificar dichos campos. | ![Campos de opciones](assets/best-practice-placed-very-near.png) |
| **El servicio de patrones** <br> puede no reconocer los campos con rótulos lejanos o una línea de puntos entre el rótulo y el campo de entrada. <br><br>**Resolución **<br>Utilice los campos de formulario con límites claros o el editor Revisar y corregir para corregir estos problemas. | ![Campos lejanos o línea de puntos entre el campo del rótulo](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### Listas {#lists}

| Patrón | Resolución |
|--- |--- |
| **Las** Listas de patrones <br>que contienen campos de formulario se combinan o no se convierten en los componentes de formulario adaptables correspondientes <br><br>**Resolución **<br>Utilice los campos de formulario con límites claros o utilice el editor Revisar y corregir para corregir estos problemas. | ![listas que contienen grupos de opciones](assets/best-practice-lists-containing-form-fields.png) |
| **El** servicio de patrones <br>puede dejar algunas listas anidadas sin identificar <br><br>**Resolución **<br>Utilice el editor Revisar y corregir para corregir estos problemas. | ![listas que contienen grupos de opciones](assets/best-practice-nested-lists.png) |
| **El servicio de patrones** <br> combina algunas listas que contienen grupos de opciones entre sí <br><br>**Resolución **<br>Utilice el editor Revisión y Correcto para corregir estos problemas. | ![listas que contienen grupos de opciones](assets/best-practice-check-box-in-table-cells.png) |

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
