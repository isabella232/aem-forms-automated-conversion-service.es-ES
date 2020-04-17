---
title: 'Solución de problemas del servicio de conversión automatizada de formularios '
seo-title: 'Solución de problemas del servicio de conversión automatizada de formularios (AFCS) '
description: 'Problemas comunes del AFCS y sus soluciones '
seo-description: Problemas comunes del AFCS y sus soluciones
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: e905833e5b58c05aac612e3a8139eb7fb60ef4bf

---


# Solución de problemas del servicio de conversión automatizada de formularios


<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. --> The document  provides basic troubleshooting steps for common errors.

## Errores comunes {#commonerrors}

| Error | Ejemplo |
|--- |--- |
| **Mensaje** de error <br> El encabezado de token de acceso no está disponible. <br><br>**Motivo **<br>: Un administrador ha creado varias configuraciones IMS o la configuración IMS no puede acceder al servicio AFCS en Adobe Cloud.<br><br>**Resolución** <br> Si hay varias configuraciones, elimine todas las configuraciones y [cree una nueva configuración](configure-service.md#obtainpubliccertificates). <br> Si hay una sola configuración, use **[!UICONTROL Health Check]** para [comprobar la conectividad](configure-service.md#createintegrationoption). | ![El encabezado de token de acceso no está disponible](assets/invalid-ims-configuration.png) |
| **Mensaje** de error <br> No se puede conectar al servicio.  <br><br>**Motivo **<br>: URL de servicio incorrecta o no se menciona ninguna URL de servicio en los servicios de nube del servicio de conversión automatizada de formularios.<br><br>**Resolución** <br> Corrección de la URL [del servicio](configure-service.md#configure-the-cloud-service) en los servicios de nube de servicios de conversión de formularios automatizados. | ![No se puede conectar con el servicio.](assets/wrong-endpoint-configured.png) |
| **Mensaje** de error <br> El servicio no pudo convertir el formulario.  <br><br>**Razón **por la que<br>los problemas de conectividad de red se producen al final, el servicio se ha reducido debido a un mantenimiento programado o a una interrupción en Adobe Cloud.<br><br>**Resolución** <br> Resuelva los problemas de conectividad de red al final y verifique el estado del servicio en https://status.adobe.com/ para una interrupción planificada o no planificada. | ![No se puede conectar con el servicio.](assets/service-failure.png) |
| **Mensaje** de error <br> El número de páginas es mayor que 15.  <br><br>**Motivo **<br>El formulario de origen tiene más de 15 páginas.<br><br>**Resolución**<br> Utilice Adobe Acrobat para dividir formularios con más de 15 páginas. Coloque el número de páginas de un formulario en menos de 15. | ![No se puede conectar con el servicio.](assets/number-of-pages.png) |
| **Mensaje** de error <br> El número de archivos es superior a 15.  <br><br>**Motivo **<br>La carpeta contiene más de 15 formularios.<br><br>**Resolución** <br> Coloque el número de formularios en una carpeta en menos o igual a 15. Coloque el número total de páginas en una carpeta menos de 50. Lleve el tamaño de la carpeta a menos de 10 MB. No mantenga los formularios en una subcarpeta. Organice los formularios de origen en un lote de 8 a 15 formularios. | ![No se puede conectar con el servicio.](assets/number-of-pages.png) |
| **Mensaje** de error <br> El formato del archivo de origen no es compatible.  <br><br>**Motivo **<br>La carpeta que contiene los formularios de origen tiene algunos archivos no admitidos.<br><br>**Resolución** <br> El servicio solo admite archivos .xdp y .pdf. Elimine los archivos con cualquier otra extensión de la carpeta y ejecute la conversión. | ![No se puede conectar con el servicio.](assets/unsupported-file-formats.png) |
| **Mensaje** de error <br> Los formularios digitalizados no son compatibles.  <br><br>**Motivo **<br>El formulario PDF solo contiene imágenes escaneadas del formulario y no contiene ninguna estructura de contenido.<br><br>**Resolución** <br> El servicio no admite la conversión de formularios digitalizados o una imagen de un formulario a una solución lista para usar adaptable. Sin embargo, se utiliza Adobe Acrobat para convertir la imagen de un formulario en un formulario PDF. A continuación, utilice el servicio para convertir el formulario PDF en un formulario adaptable. Utilice siempre una imagen de alta calidad del formulario para la conversión en Acrobat. Mejora la calidad de la conversión. | ![No se puede conectar con el servicio.](assets/scanned-forms-error.png) |
| **No se admite el formulario PDF cifrado de mensaje** <br> de error.  <br><br>**Motivo **<br>La carpeta contiene formularios PDF cifrados.<br><br>**Resolución** <br> El servicio no admite la conversión de un formulario PDF codificado a un formulario adaptable. Elimine el cifrado, cargue el formulario no cifrado y ejecute la conversión. | ![No se puede conectar con el servicio.](assets/secured-pdf-form.png) |
| **Mensaje** de error <br> No se puede analizar el esquema JSON de meta-modelo.  <br><br>**Motivo **<br>El esquema JSON proporcionado al servicio no tiene el formato correcto, contiene caracteres no válidos o utiliza una sintaxis no válida para asignar componentes.<br><br>**Resolución** <br> Compruebe el formato del archivo JSON. Puede utilizar cualquier validador JSON en línea para comprobar el formato y la estructura del esquema. Consulte [Ampliación del artículo de metamodelo](extending-the-default-meta-model.md) predeterminado para obtener información sobre la sintaxis de metamodelo. | ![No se puede conectar con el servicio.](assets/invalid-meta-model-schema.png) |

<!--

<table>
<thead>
<tr>
<th>Error</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Error Message</strong> <p> The access token header is not available. </p><br><strong>Reason</strong> <br> An administrator has created multiple IMS configurations or IMS configuration is not able to reach AFCS service on Adobe Cloud. <br><br><strong>Resolution</strong> <br> If there are multiple configurations, delete all the configurations and <a href="configure-service.md#obtainpubliccertificates">create a new configuration</a>. <br> If there is a single configuration, use <strong> Health Check </strong> to <a href="configure-service.md#createintegrationoption">check connectivity</a>.</td>
<td><img alt="The access token header is not available" src="assets/invalid-ims-configuration.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Unable to connect to the service.  <br><br><strong>Reason</strong> <br> Incorrect service URL or no service URL is mentioned in Automated Forms Conversion Service cloud services. <br><br><strong>Resolution</strong> <br> Correct <a href="configure-service.md#configure-the-cloud-service">Service URL</a> in Automated Forms Conversion Service Cloud services.</td>
<td><img alt="Unable to connect to the service." src="assets/wrong-endpoint-configured.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The service failed to convert the form.  <br><br><strong>Reason</strong> <br> Network connectivity issues at your end, the service is down due to scheduled maintenance, or outage on Adobe Cloud. <br><br><strong>Resolution</strong> <br> Resolve network connectivity issues at your end and check the status of the service on <a href="https://status.adobe.com/">https://status.adobe.com/</a> for a planned or unplanned outage.</td>
<td><img alt="The service failed to convert the form." src="assets/service-failure.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The number of pages is more than 15.  <br><br><strong>Reason</strong> <br> The source form is more than 15 pages long.  <br><br><strong>Resolution</strong> <br> Use Adobe Acrobat to split forms with more than 15 pages. Bring the number of pages in a form to less than 15.</td>
<td><img alt="The number of pages is more than 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The number of files is more than 15.  <br><br><strong>Reason</strong> <br>  The folder contains more than 15 forms. <br><br><strong>Resolution</strong> <br> Bring the number of forms in a folder to less than or equal to 15. Bring the total number of pages in a folder less than 50. Bring the size of the folder to less than 10 MB. Do not keep forms in a sub-folder. Organize source forms into a batch of 8-15 forms.</td>
<td><img alt="The number of files is more than 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The source file format is not supported.  <br><br><strong>Reason</strong> <br> The folder containing source forms have some unsupported files. <br><br><strong>Resolution</strong> <br> The service supports only .xdp and .pdf files. Remove files with any other extension from the folder and run the conversion.</td>
<td><img alt="The source file format is not supported." src="assets/unsupported-file-formats.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Scanned forms are not supported.  <br><br><strong>Reason</strong> <br> The PDF form contains only scanned images of the form and contains no content structure. <br><br><strong>Resolution</strong> <br> The service does not support converting scanned forms or an image of a form to an adaptive out-of-the-box. However, you use Adobe Acrobat to convert the image of a form to a PDF Form. Then, use the service to convert the PDF Form to an adaptive form. Always use a high-quality image of the form for conversion in Acrobat. It improves the quality of the conversion.</td>
<td><img alt="Scanned forms are not supported." src="assets/scanned-forms-error.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Encrypted PDF form is not supported.  <br><br><strong>Reason</strong> <br> The folder contains encrypted PDF forms. <br><br><strong>Resolution</strong> <br> The service does not support converting an encrypted PDF form to an adaptive form. Remove the encryption, upload the non-encrypted form, and run the conversion.</td>
<td><img alt="Encrypted PDF form is not supported." src="assets/secured-pdf-form.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Unable to parse meta-model JSON schema.  <br><br><strong>Reason</strong> <br> The JSON schema supplied to the service is not properly formatted, contains invalid characters, or uses invalid syntax to map components.  <br><br><strong>Resolution</strong> <br> Check the formatting of the JSON file. You can use any online JSON validator to check the formatting and structure of the schema. See, <a href="extending-the-default-meta-model.md">Extend the default meta-model</a> article for information on meta-model syntax.</td>
<td><img alt="Unable to parse meta-model JSON schema" src="assets/invalid-meta-model-schema.png" /></td>
</tr>
</tbody>
</table>
-->