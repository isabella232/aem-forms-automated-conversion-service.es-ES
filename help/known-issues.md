---
title: Problemas conocidos
seo-title: Problemas conocidos
description: problemas conocidos y limitaciones del servicio de conversión de formularios automatizados
seo-description: Antes de empezar a utilizar el servicio de conversión automatizada de formularios de AEM Forms, conozca los problemas conocidos y las limitaciones del servicio
uuid: b1dc661b-ccd3-457f-acbb-4bd25db86e1e
topic-tags: introduction
discoiquuid: 9cd2363c-47a0-46e9-98cd-1fe088b9cd6e
translation-type: tm+mt
source-git-commit: 2fcceb45d9be4297fcd923f5a17c7b593294e855

---

# Problemas y limitaciones conocidos {#known-issues-limitations}

Antes de empezar a utilizar el servicio de conversión automatizada de formularios de AEM Forms, consulte los siguientes problemas y limitaciones conocidos:

## Problemas conocidos {#known-issues}

* La carpeta que contiene los formularios para la conversión no debe tener más de 15 formularios y 50 páginas en total. El tamaño de la carpeta de origen no debe superar los 10 MB. No cree subcarpetas en la carpeta de origen.
* Algunos objetos de formulario son fácilmente visibles para el ojo humano, pero son [difíciles de identificar para el servicio](styles-and-pattern-considerations-and-best-practices.md). Utilice [Revisar y el editor](review-correct-ui-edited.md) correcto para identificar y convertir dichos objetos de formulario.
* Editor de revisión y corrección:

   * No tiene una acción de deshacer. El botón Guardar guarda los cambios de forma permanente.
   * No admite paneles repetibles para formularios basados en XFA.
   * Si modifica una lista de una tabla con el editor Revisar y corregir, el ancho de fila no se ajusta automáticamente y el texto podría extenderse a la siguiente fila de la tabla.
   * La **[!UICONTROL Auto-detect multi-column layout from input forms]** función no funciona con el editor Revisar y corregir ni con los fragmentos de formulario.

* Para formularios basados en XFA:
   * No se admite la extracción de fragmentos de un formulario basado en XFA.
   * No se admiten scripts XFA. Por ejemplo, secuencias de comandos para generar valores automáticamente para un componente desplegable.
   * El modelo meta no funciona para el grupo de opciones
   * No se identifica la opción Grupos de opciones con un solo carácter
   * Cuando el documento de origen es un XFA dinámico (.XDP) y [define el comportamiento de las propiedades XFA en un formulario](https://helpx.adobe.com/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr)adaptable, no se respeta la propiedad presence del documento de origen. Por ejemplo, un campo del documento de origen se marca como oculto y una secuencia de comandos hace que el campo sea visible y, a continuación, el campo permanece visible en el formulario adaptable de salida.

* Cuando utilice la opción **Usar AcroForm de entrada como documento de registro (DoR) para formularios** adaptables generados, tenga en cuenta lo siguiente:

<table>
    <tr>
        <td>El enlace y los datos se pierden para los campos de texto compuestos. Los campos de texto compuestos tienen varios cuadros de texto alineados entre sí. Por ejemplo, en un AcroForm, un número de tarjeta de crédito se divide en varios cuadros de texto y cada cuadro de texto tiene un enlace independiente. Cuando AcroForm se convierte en un formulario adaptable, el formulario adaptable convertido tiene un único enlace para todos los cuadros de texto. Como solución alternativa, antes de convertir un AcroForm en un formulario adaptable, modifique AcroForm para que utilice un único cuadro de texto para aceptar números de tarjeta de crédito.</td>
        <td><img  src="assets/creditCard_Composite.png"/>                                                            </td>
    </tr>
    <tr>
        <td>El enlace y los datos se pierden para los campos de fecha compuestos. Los campos de fecha compuestos se componen de tres campos diferentes. Por ejemplo, una fecha de nacimiento en un AcroForm se divide en tres campos independientes. El formulario adaptable proporciona un componente de selector de fecha incorporado. Para utilizar el componente de selector de fechas del formulario adaptable manteniendo el enlace de AcroForm, antes de convertir un AcroForm a un formulario adaptable, modifique AcroForm para utilizar un campo de fecha única.</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>Si el tamaño de las casillas de verificación es mayor que el texto que las acompaña, no se detectan las casillas de verificación y se pierde el enlace en AcroForm. Modifique AcroForm para que el tamaño de las casillas de verificación sea inferior al texto que las acompaña.</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>Si los campos de entrada no se alinean con el campo de texto correspondiente, no se detectará el campo de entrada.  </td>
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

## Restricciones {#limitations}

* Los formularios PDF con presentación dinámica compleja, los campos con contorno de puntos, los campos rellenos o los campos de color no son compatibles.
* Las imágenes y el texto dentro de las imágenes no se identifican. Agregue manualmente imágenes a los formularios convertidos.
* Los documentos XDP de ilustraciones no son compatibles.
* No se admiten los formularios PDF de más de 15 páginas.
* Los documentos cifrados, protegidos con contraseña y protegidos no se convierten. Elimine el cifrado o las contraseñas antes de ejecutar la conversión.
* No se admiten tablas complejas como tablas sin bordes, tablas anidadas, tablas con filas de color y tablas con valores de marcador de posición. Utilice el editor de formularios adaptables para agregar o modificar tablas complejas después de la conversión. Solo se admiten tablas simples, con campos vacíos, encabezados adecuados y límites claros.
* El servicio convierte solo los formularios en inglés en formularios adaptables. Puede traducir formularios adaptables convertidos a otro idioma mediante el flujo de trabajo [de traducción de](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)AEM.
* AEM 6.4 Forms no admite la detección automática del diseño de varias columnas de los formularios de entrada.

