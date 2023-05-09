---
title: Problemas conocidos
seo-title: Known Issues
description: problemas conocidos y limitaciones del servicio de conversión automatizada de formularios
seo-description: Before you begin using AEM Forms Automated Forms Conversion service, learn about the known issues and limitations of the service
uuid: b1dc661b-ccd3-457f-acbb-4bd25db86e1e
topic-tags: introduction
discoiquuid: 9cd2363c-47a0-46e9-98cd-1fe088b9cd6e
exl-id: 35f59e02-e38e-473a-94c8-123e0a85ac8e
source-git-commit: 47261710e6616c27c210ac53bffcc2387a06ea7a
workflow-type: ht
source-wordcount: '794'
ht-degree: 100%

---

# Problemas conocidos y limitaciones {#known-issues-limitations}

Antes de empezar a utilizar el servicio de conversión automatizada de formularios de AEM Forms, revise los siguientes problemas conocidos y limitaciones:

## Problemas conocidos {#known-issues}

* La carpeta que contiene los formularios para la conversión no debe tener más de 15 formularios y 50 páginas en total. El tamaño de la carpeta de origen no debe superar los 10 MB. No cree subcarpetas en la carpeta de origen.
* Algunos objetos de formulario son fácilmente visibles para las personas, pero [difíciles de identificar para el servicio](styles-and-pattern-considerations-and-best-practices.md). Use el [editor Revisar y corregir](review-correct-ui-edited.md) para identificar y convertir dichos objetos de formulario.
* Editor Revisar y corregir:

   * No tiene la acción Deshacer. El botón Guardar guarda los cambios de forma permanente.
   * No admite paneles repetibles para formularios basados en XFA.
   * Si modifica la lista de una tabla con el editor Revisar y corregir, la anchura de la fila no se ajusta automáticamente y el texto puede pasar a la siguiente fila.
   * La característica **[!UICONTROL Auto-detect multi-column layout from input forms]** no funciona con el editor Revisar y corregir ni los fragmentos de formulario.
   * La firma manuscrita creada con el editor Revisar y corregir no se carga en los formularios adaptables publicados.


* Respecto de los formularios basados en XFA:
   * No se admite la extracción de fragmentos de un formulario basado en XFA.
   * Los scripts XFA no son compatibles. Por ejemplo, los scripts para la generación automática de valores para un componente desplegable.
   * El metamodelo no funciona para el grupo de elección.
   * No se identifica la opción Grupos de elección con un solo carácter.
   * Cuando el documento de origen es un XFA dinámico (.XDP) y [define el comportamiento de las propiedades XFA en un formulario adaptable](https://helpx.adobe.com/es/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr), no se respeta la propiedad de presencia del documento de origen. Por ejemplo, un campo del documento de origen se marca como oculto y un script hace que sea visible. Entonces, permanece visible en el formulario adaptable de salida.

* Al usar la opción **Utilizar un AcroForm de entrada como documento de registro (DoR) para los formularios adaptables generados**, considere lo siguiente:

<table>
    <tr>
        <td>Los enlaces y los datos se pierden en los campos de texto compuestos. Los campos de texto compuestos tienen varios cuadros de texto alineados entre sí. Por ejemplo, en un AcroForm, el número de una tarjeta de crédito se divide en varios cuadros de texto y cada uno tiene un enlace por separado. Cuando un AcroForm se convierte en un formulario adaptable, el resultado tiene un enlace único para todos los cuadros de texto. Como solución alternativa, antes de convertir un AcroForm a un formulario adaptable, modifíquelo para utilizar un cuadro de texto único para los números de tarjetas de crédito.</td>
        <td><img  src="assets/creditCard_Composite.png"/>                                                            </td>
    </tr>
    <tr>
        <td>Los enlaces y los datos se pierden en los campos de fecha compuestos. Los campos de fecha compuestos están formados por tres campos diferentes. Por ejemplo, un campo de fecha de nacimiento de un AcroForm se divide en tres campos independientes. El formulario adaptable proporciona un componente de selector de fechas por defecto. Para utilizar el componente de selector de fechas del formulario adaptable manteniendo los enlaces del AcroForm, antes de convertirlo a un formulario adaptable, modifíquelo para utilizar un campo de fecha único.</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>Si el tamaño de las casillas de verificación es mayor que el texto que las acompaña, no se detectan y se pierden los enlaces del AcroForm. Modifique el AcroForm para que el tamaño de las casillas de verificación sea menor que el texto que las acompaña.</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>Si los campos de entrada no se alinean con el campo de texto correspondiente, no se detectan.  </td>
        <td><img  src="assets/non-alingned-fields.png"/></td>
    </tr>
    <tr >
        <td>El servicio convierte todas las casillas de verificación de un AcroForm en grupos de elección independientes. Se crean grupos de elección independientes para conservar los enlaces del AcroForm. No combine grupos de elección en el formulario adaptable. Esto hace que se pierdan los enlaces. Si combina los grupos de elección, vuelva a convertir el formulario para recuperar los enlaces perdidos. </td>
        <td></td>
    </tr>
    <tr >
        <td>Los límites de algunas tablas se extienden fuera de la página en el documento de registro (DoR) generado automáticamente. </td>
        <td></td>
    </tr>
</table>

## Restricciones {#limitations}

* Los formularios PDF con un diseño dinámico complejo, los campos con contorno de puntos o los campos rellenados no son compatibles.
* Las imágenes y el texto dentro de las imágenes no se identifican. Agregue manualmente las imágenes a los formularios convertidos.
* Los documentos XDP de ilustraciones no son compatibles.
* No se admiten los formularios PDF de más de 15 páginas.
* Los documentos cifrados, con contraseña y protegidos, no se convierten. Elimine el cifrado o las contraseñas antes de ejecutar la conversión.
* No se admiten las tablas complejas sin bordes, anidadas y con valores de marcador de posición. Utilice el editor de formularios adaptables para añadir o modificar tablas complejas después de la conversión. Solo se admiten tablas simples, con campos vacíos, encabezados adecuados y límites delimitados.
* El servicio convierte únicamente los formularios en inglés, francés, alemán, español, italiano y portugués a formularios adaptables. Puede traducir los formularios adaptables convertidos a otro idioma con el [Flujo de trabajo de traducción de AEM](https://helpx.adobe.com/es/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html).
* AEM 6.4 Forms no admite la detección automática de diseños de varias columnas de los formularios de entrada.
* La información codificada con colores en el formulario PDF de origen no se transfiere al formulario adaptable.
* Los colores del formulario PDF de origen no se transfieren a las temáticas de formulario adaptable.
* Los formularios PDF en color se tratan como formularios en escala de grises y los campos se detectan en consecuencia.
