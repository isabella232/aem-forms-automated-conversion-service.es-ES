---
title: 'Solución de problemas del servicio de conversión automatizada de formularios '
seo-title: 'Solución de problemas del servicio de conversión automatizada de formularios (AFCS) '
description: 'Problemas comunes del AFCS y sus soluciones '
seo-description: Problemas comunes del AFCS y sus soluciones
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 4b9f3f4fe3b3901cb99c9374ff40e8f49855237f

---


# Solución de problemas del servicio de conversión automatizada de formularios


El artículo proporciona información sobre los problemas de instalación, configuración y administración que pueden surgir en un entorno de producción del Servicio de conversión automatizada de formularios. El documento también proporciona pasos básicos para la resolución de problemas y una explicación de los mensajes de error comunes.

## Errores comunes {#commonerrors}

| Error | Ejemplo |
|--- |--- |
| **Mensaje** de error <br> El encabezado de token de acceso no está disponible. <br><br>**Motivo **<br>: Un administrador ha creado varias configuraciones IMS o la configuración IMS no puede acceder al servicio AFCS en Adobe Cloud.<br><br>**Resolución** <br> Si hay varias configuraciones, elimine todas las configuraciones y [cree una nueva configuración](configure-service.md#obtainpubliccertificates). <br> Si hay una sola configuración, use **[!UICONTROL Health Check]** para [comprobar la conectividad](configure-service.md#createintegrationoption). | ![El encabezado de token de acceso no está disponible](assets/invalid-ims-configuration.png) |
| **Mensaje** de error <br> No se puede conectar al servicio.  <br><br>**Motivo **<br>: URL de servicio incorrecta o no se menciona ninguna URL de servicio en los servicios de nube del servicio de conversión automatizada de formularios.<br><br>**Resolución** <br> Corrección de la URL [del servicio](configure-service.md#configure-the-cloud-service) en los servicios de nube de servicios de conversión de formularios automatizados. | ![No se puede conectar con el servicio.](assets/wrong-endpoint-configured.png) |
| **Mensaje** de error <br> El servicio no pudo convertir el formulario.  <br><br>**Motivo **por el que<br>los problemas de conectividad de red se producen al final o el servicio está inactivo debido al mantenimiento o interrupción programados en Adobe Cloud.<br><br>**Resolución** <br> Resuelva los problemas de conectividad de red al final y compruebe el estado del servicio en https://status.adobe.com/ para ver si hay interrupciones planificadas o no planificadas. | ![No se puede conectar con el servicio.](assets/service-failure.png) |
| **Mensaje** de error <br> El número de páginas es superior a 15.  <br><br>**Motivo **<br>La carpeta que contiene los formularios XDP y PDF de origen tiene más de 15 archivos.<br><br>**Resolución** <br> Coloque el número de formularios en una carpeta en menos o igual a 15. Coloque el número total de páginas en una carpeta menos de 50. Lleve el tamaño de la carpeta a menos de 10 MB. No mantenga los formularios en una subcarpeta. Organizar documentos de origen en un lote de 8 a 15 documentos. | ![No se puede conectar con el servicio.](assets/number-of-pages.png) |
| **Mensaje** de error <br> El formato del archivo de origen no es compatible.  <br><br>**Motivo **<br>La carpeta que contiene los formularios de origen tiene algunos archivos no admitidos.<br><br>**Resolución** <br> El servicio solo admite archivos .xdp y .pdf. Elimine los archivos con cualquier otra extensión de la carpeta y ejecute la conversión. | ![No se puede conectar con el servicio.](assets/unsupported-file-formats.png) |
| **Mensaje** de error <br> Los formularios digitalizados no son compatibles.  <br><br>**Motivo **<br>El formulario PDF solo contiene una imagen digitalizada del formulario y no contiene ninguna estructura de contenido.<br><br>**Resolución** <br> El servicio no admite la conversión de formularios digitalizados o una imagen de un formulario a una solución lista para usar adaptable. Sin embargo, se utiliza Adobe Acrobat para convertir la imagen de un formulario en un formulario PDF. A continuación, utilice el servicio para convertir el formulario PDF en un formulario adaptable. Utilice siempre una imagen de alta calidad del formulario para la conversión en Acrobat. Mejora la calidad de la conversión. | ![No se puede conectar con el servicio.](assets/scanned-forms-error.png) |