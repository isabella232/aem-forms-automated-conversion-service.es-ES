---
title: Problemas conocidos
seo-title: Problemas conocidos
description: problemas conocidos y limitaciones del servicio de Automated forms conversion
seo-description: Antes de empezar a utilizar el servicio de Automated forms conversion de AEM Forms, conozca los problemas y limitaciones conocidos del servicio
uuid: b1dc661b-ccd3-457f-acbb-4bd25db86e1e
topic-tags: introduction
discoiquuid: 9cd2363c-47a0-46e9-98cd-1fe088b9cd6e
exl-id: 35f59e02-e38e-473a-94c8-123e0a85ac8e
source-git-commit: af05922f9eb76b7b0a30601824c6006fe555ea80
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 1%

---

# Problemas y limitaciones conocidos {#known-issues-limitations}

Antes de empezar a utilizar el servicio de Automated forms conversion de AEM Forms, revise los siguientes problemas y limitaciones conocidos:

## Problemas conocidos {#known-issues}

* La carpeta que contiene los formularios para la conversión no debe tener más de 15 formularios y 50 páginas en total. El tamaño de la carpeta de origen no debe superar los 10 MB. No cree subcarpetas en la carpeta de origen.
* Algunos objetos de formulario son fácilmente visibles para el ojo humano, pero son [difíciles de identificar para el servicio](styles-and-pattern-considerations-and-best-practices.md). Utilice [Revisar y corregir editor](review-correct-ui-edited.md) para identificar y convertir dichos objetos de formulario.
* Revisar y corregir editor:

   * No tiene una acción de deshacer. El botón Guardar guarda los cambios de forma permanente.
   * No admite paneles repetibles para formularios basados en XFA.
   * Si modifica una lista de una tabla con el editor Revisar y corregir , el ancho de fila no se ajusta automáticamente y el texto podría extenderse a la siguiente fila de la tabla.
   * La función **[!UICONTROL Auto-detect multi-column layout from input forms]** no funciona con el editor de revisiones y correcciones y con los fragmentos de formulario.
   * La firma manuscrita creada con el editor de revisiones y correcciones no se carga para los formularios adaptables publicados.


* Para formularios basados en XFA:
   * No se admite la extracción de fragmentos de un formulario basado en XFA.
   * Los scripts XFA no son compatibles. Por ejemplo, secuencias de comandos para la generación automática de valores para un componente desplegable.
   * El metamodelo no funciona para el grupo de opciones
   * La opción Grupos de opciones con un solo carácter no se identifica
   * Cuando el documento de origen es un XFA dinámico (.XDP) y [define el comportamiento de las propiedades XFA en un formulario adaptable](https://helpx.adobe.com/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr), no se respeta la propiedad presence del documento de origen. Por ejemplo, un campo del documento de origen se marca como oculto y una secuencia de comandos hace que el campo sea visible y, a continuación, el campo permanece visible en el formulario adaptable de salida.

* Cuando utilice la opción **Use input AcroForm as Document of Record (DoR) para formularios adaptables generados**, tenga en cuenta lo siguiente:

<table>
    <tr>
        <td>El enlace y los datos se pierden en los campos de texto compuestos. Los campos de texto compuestos tienen varios cuadros de texto alineados entre sí. Por ejemplo, en un AcroForm, un número de tarjeta de crédito se divide en varios cuadros de texto y cada cuadro de texto tiene un enlace separado. Cuando AcroForm se convierte en un formulario adaptable, el formulario adaptable convertido tiene un enlace único para todos los cuadros de texto. Como solución alternativa, antes de convertir un AcroForm a un formulario adaptable, modifique el AcroForm para utilizar un cuadro de texto único para aceptar números de tarjetas de crédito.</td>
        <td><img  src="assets/creditCard_Composite.png"/>                                                            </td>
    </tr>
    <tr>
        <td>El enlace y los datos se pierden en los campos de fecha compuestos. Los campos de fecha compuestos se componen de tres campos diferentes. Por ejemplo, un campo de fecha de nacimiento de un AcroForm se divide en tres campos independientes. El formulario adaptable proporciona un componente de selector de fechas incorporado. Para utilizar el componente selector de fechas del formulario adaptable manteniendo el enlace del AcroForm, antes de convertir un AcroForm a un formulario adaptable, modifique el AcroForm para utilizar el campo de fecha única.</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>Si el tamaño de las casillas de verificación es mayor que el texto que las acompaña, las casillas de verificación no se detectan y se pierde el enlace en AcroForm. Modifique AcroForm para que el tamaño de las casillas de verificación sea menor que el texto que la acompaña.</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>Si los campos de entrada no se alinean con el campo de texto correspondiente, no se detecta el campo de entrada.  </td>
        <td><img  src="assets/non-alingned-fields.png"/></td>
    </tr>
    <tr >
        <td>El servicio convierte todas las casillas de verificación de un AcroForm en grupos de opciones independientes. Se crean grupos de opciones independientes para conservar los enlaces con AcroForm. No combine grupos de opciones en el formulario adaptable. Esto llevará a la pérdida de enlaces. Si combina los grupos de opciones, vuelva a convertir el formulario para recuperar los enlaces perdidos. </td>
        <td></td>
    </tr>
    <tr >
        <td>Los límites de algunas tablas se extienden fuera de la página en el documento de registro generado automáticamente (DoR). </td>
        <td></td>
    </tr>
</table>

## Restricciones     {#limitations}

* Los PDF forms con diseño dinámico complejo, campos con contorno de puntos o campos rellenos no son compatibles.
* Las imágenes y el texto dentro de las imágenes no se identifican. Agregue manualmente imágenes a formularios convertidos.
* Los documentos XDP de ilustraciones no son compatibles.
* No se admiten los PDF forms de más de 15 páginas.
* Los documentos cifrados, protegidos con contraseña y protegidos no se convierten. Elimine el cifrado o las contraseñas antes de ejecutar la conversión.
* No se admiten tablas complejas como tablas sin bordes, tablas anidadas y tablas con valores de marcador de posición. Utilice el editor de formularios adaptables para añadir o modificar tablas complejas después de la conversión. Solo se admiten tablas simples, con campos vacíos, encabezados adecuados y límites claros.
* El servicio convierte únicamente los formularios en español, francés, inglés y alemán a formularios adaptables. Puede traducir formularios adaptables convertidos a otro idioma mediante [AEM flujo de trabajo de traducción](https://helpx.adobe.com/es/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html).
* AEM 6.4 Forms no admite la detección automática del diseño de varias columnas de los formularios de entrada.
* La información codificada con colores en el formulario PDF de origen no se transfiere al formulario adaptable.
* Los colores del formulario PDF de origen no se transfieren a temas de formulario adaptables.
* Los PDF forms de color se tratan como formularios de escala de grises y los campos se detectan en consecuencia.
