---
title: 'Solución de problemas del servicio de conversión automatizada de formularios '
seo-title: 'Solución de problemas del servicio de conversión automatizada de formularios (AFCS) '
description: 'Problemas comunes del AFCS y sus soluciones '
seo-description: Problemas comunes del AFCS y sus soluciones
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 56e4696c0372223e0b27f1c313382a2a637b6db1

---


# Solución de problemas del servicio de conversión automatizada de formularios


<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. --> The document  provides basic troubleshooting steps for common errors.

## Errores comunes {#commonerrors}
<!--
|Error|Example|
|--- |--- |
|**Error Message** <br> The access token header is not available. <br><br>**Reason** <br> An administrator has created multiple IMS configurations or IMS configuration is not able to reach AFCS service on Adobe Cloud. <br><br>**Resolution** <br> If there are multiple configurations, delete all the configurations and [create a new configuration](configure-service.md#obtainpubliccertificates). <br> If there is a single configuration, use **[!UICONTROL Health Check]** to [check connectivity](configure-service.md#createintegrationoption).|![The access token header is not available](assets/invalid-ims-configuration.png)|
|**Error Message** <br> Unable to connect to the service.  <br><br>**Reason** <br> Incorrect service URL or no service URL is mentioned in Automated Forms Conversion Service cloud services. <br><br>**Resolution** <br> Correct [Service URL](configure-service.md#configure-the-cloud-service) in Automated Forms Conversion Service Cloud services.|![Unable to connect to the service.](assets/wrong-endpoint-configured.png)|
|**Error Message** <br> The service failed to convert the form.  <br><br>**Reason** <br> Network connectivity issues at your end, the service is down due to scheduled maintenance, or outage on Adobe Cloud. <br><br>**Resolution** <br> Resolve network connectivity issues at your end and check the status of the service on https://status.adobe.com/ for a planned or unplanned outage.|![Unable to connect to the service.](assets/service-failure.png)|
|**Error Message** <br> The number of pages is more than 15.  <br><br>**Reason** <br> The source form is more than 15 pages long.  <br><br>**Resolution** <br> Use Adobe Acrobat to split forms with more than 15 pages. Bring the number of pages in a form to less than 15. |![Unable to connect to the service.](assets/number-of-pages.png)|
|**Error Message** <br> The number of files is more than 15.  <br><br>**Reason** <br>  The folder contains more than 15 forms. <br><br>**Resolution** <br> Bring the number of forms in a folder to less than or equal to 15. Bring the total number of pages in a folder less than 50. Bring the size of the folder to less than 10 MB. Do not keep forms in a sub-folder. Organize source forms into a batch of 8-15 forms. |![Unable to connect to the service.](assets/number-of-pages.png)|
|**Error Message** <br> The source file format is not supported.  <br><br>**Reason** <br> The folder containing source forms have some unsupported files. <br><br>**Resolution** <br> The service supports only .xdp and .pdf files. Remove files with any other extension from the folder and run the conversion. |![Unable to connect to the service.](assets/unsupported-file-formats.png)|
|**Error Message** <br> Scanned forms are not supported.  <br><br>**Reason** <br> The PDF form contains only scanned images of the form and contains no content structure. <br><br>**Resolution** <br> The service does not support converting scanned forms or an image of a form to an adaptive out-of-the-box. However, you use Adobe Acrobat to convert the image of a form to a PDF Form. Then, use the service to convert the PDF Form to an adaptive form. Always use a high-quality image of the form for conversion in Acrobat. It improves the quality of the conversion. |![Unable to connect to the service.](assets/scanned-forms-error.png)|
|**Error Message** <br> Encrypted PDF form is not supported.  <br><br>**Reason** <br> The folder contains encrypted PDF forms. <br><br>**Resolution** <br> The service does not support converting an encrypted PDF form to an adaptive form. Remove the encryption, upload the non-encrypted form, and run the conversion. |![Unable to connect to the service.](assets/secured-pdf-form.png)|
|**Error Message** <br> Unable to parse meta-model JSON schema.  <br><br>**Reason** <br> The JSON schema supplied to the service is not properly formatted, contains invalid characters, or uses invalid syntax to map components.  <br><br>**Resolution** <br> Check the formatting of the JSON file. You can use any online JSON validator to check the formatting and structure of the schema. See, [Extend the default meta-model](extending-the-default-meta-model.md) article for information on meta-model syntax. |![Unable to connect to the service.](assets/invalid-meta-model-schema.png)| -->

<table>
<thead>
<tr>
<th>Error</th>
<th>Ejemplo</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Mensaje</strong> de error <br> El encabezado de token de acceso no está disponible. <br><br><strong>Motivo</strong> <br> : Un administrador ha creado varias configuraciones IMS o la configuración IMS no puede acceder al servicio AFCS en Adobe Cloud. <br><br><strong>Resolución</strong> <br> Si hay varias configuraciones, elimine todas las configuraciones y <a href="configure-service.md#obtainpubliccertificates">cree una nueva configuración</a>. <br> Si hay una sola configuración, utilice <strong>[!Verificación de estado de UICONTROL]</strong> para <a href="configure-service.md#createintegrationoption">comprobar la conectividad</a>.</td>
<td><img alt="El encabezado de token de acceso no está disponible" src="assets/invalid-ims-configuration.png" /></td>
</tr>
<tr>
<td><strong>Mensaje</strong> de error <br> No se puede conectar al servicio.  <br><br><strong>Motivo</strong> <br> : URL de servicio incorrecta o no se menciona ninguna URL de servicio en los servicios de nube del servicio de conversión automatizada de formularios. <br><br><strong>Resolución</strong> <br> Corrección de la URL <a href="configure-service.md#configure-the-cloud-service">del servicio</a> en los servicios de nube de servicios de conversión de formularios automatizados.</td>
<td><img alt="No se puede conectar con el servicio." src="assets/wrong-endpoint-configured.png" /></td>
</tr>
<tr>
<td><strong>Mensaje</strong> de error <br> El servicio no pudo convertir el formulario.  <br><br><strong>Razón</strong> por la que <br> los problemas de conectividad de red se producen al final, el servicio se ha reducido debido a un mantenimiento programado o a una interrupción en Adobe Cloud. <br><br><strong>Resolución</strong> <br> Resuelva los problemas de conectividad de red al final y compruebe el estado del servicio en <a href="https://status.adobe.com/">https://status.adobe.com/</a> para una interrupción planificada o no planificada.</td>
<td><img alt="El servicio no pudo convertir el formulario." src="assets/service-failure.png" /></td>
</tr>
<tr>
<td><strong>Mensaje</strong> de error <br> El número de páginas es mayor que 15.  <br><br><strong>Motivo</strong><br> El formulario de origen tiene más de 15 páginas.  <br><br><strong>Resolución</strong><br> Utilice Adobe Acrobat para dividir formularios con más de 15 páginas. Coloque el número de páginas de un formulario en menos de 15.</td>
<td><img alt="El número de páginas es superior a 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Mensaje</strong> de error <br> El número de archivos es superior a 15.  <br><br><strong>Motivo</strong><br> La carpeta contiene más de 15 formularios. <br><br><strong>Resolución</strong> <br> Coloque el número de formularios en una carpeta en menos o igual a 15. Coloque el número total de páginas en una carpeta menos de 50. Lleve el tamaño de la carpeta a menos de 10 MB. No mantenga los formularios en una subcarpeta. Organice los formularios de origen en un lote de 8 a 15 formularios.</td>
<td><img alt="El número de archivos es superior a 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Mensaje</strong> de error <br> El formato del archivo de origen no es compatible.  <br><br><strong>Motivo</strong><br> La carpeta que contiene los formularios de origen tiene algunos archivos no admitidos. <br><br><strong>Resolución</strong> <br> El servicio solo admite archivos .xdp y .pdf. Elimine los archivos con cualquier otra extensión de la carpeta y ejecute la conversión.</td>
<td><img alt="No se admite el formato de archivo de origen." src="assets/unsupported-file-formats.png" /></td>
</tr>
<tr>
<td><strong>Mensaje</strong> de error <br> Los formularios digitalizados no son compatibles.  <br><br><strong>Motivo</strong><br> El formulario PDF solo contiene imágenes escaneadas del formulario y no contiene ninguna estructura de contenido. <br><br><strong>Resolución</strong> <br> El servicio no admite la conversión de formularios digitalizados o una imagen de un formulario a una solución lista para usar adaptable. Sin embargo, se utiliza Adobe Acrobat para convertir la imagen de un formulario en un formulario PDF. A continuación, utilice el servicio para convertir el formulario PDF en un formulario adaptable. Utilice siempre una imagen de alta calidad del formulario para la conversión en Acrobat. Mejora la calidad de la conversión.</td>
<td><img alt="Los formularios digitalizados no son compatibles." src="assets/scanned-forms-error.png" /></td>
</tr>
<tr>
<td><strong>No se admite el formulario PDF cifrado de mensaje</strong> <br> de error.  <br><br><strong>Motivo</strong><br> La carpeta contiene formularios PDF cifrados. <br><br><strong>Resolución</strong> <br> El servicio no admite la conversión de un formulario PDF codificado a un formulario adaptable. Elimine el cifrado, cargue el formulario no cifrado y ejecute la conversión.</td>
<td><img alt="No se admite el formulario PDF cifrado." src="assets/secured-pdf-form.png" /></td>
</tr>
<tr>
<td><strong>Mensaje</strong> de error <br> No se puede analizar el esquema JSON de meta-modelo.  <br><br><strong>Motivo</strong><br> El esquema JSON proporcionado al servicio no tiene el formato correcto, contiene caracteres no válidos o utiliza una sintaxis no válida para asignar componentes.  <br><br><strong>Resolución</strong> <br> Compruebe el formato del archivo JSON. Puede utilizar cualquier validador JSON en línea para comprobar el formato y la estructura del esquema. Consulte <a href="extending-the-default-meta-model.md">Ampliación del artículo de metamodelo</a> predeterminado para obtener información sobre la sintaxis de metamodelo.</td>
<td><img alt="No se puede analizar el esquema JSON de meta-modelo" src="assets/invalid-meta-model-schema.png" /></td>
</tr>
</tbody>
</table>
