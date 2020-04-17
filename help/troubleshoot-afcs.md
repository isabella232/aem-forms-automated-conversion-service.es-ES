---
title: 'Solución de problemas del servicio de conversión automatizada de formularios '
seo-title: 'Solución de problemas del servicio de conversión automatizada de formularios (AFCS) '
description: 'Problemas comunes del AFCS y sus soluciones '
seo-description: Problemas comunes del AFCS y sus soluciones
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 535267e20fb8e583e1c01f4160be378ffd31a4a4

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
