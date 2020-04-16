---
title: 'Solución de problemas del servicio de conversión automatizada de formularios '
seo-title: 'Solución de problemas del servicio de conversión automatizada de formularios (AFCS) '
description: 'Problemas comunes del AFCS y sus soluciones '
seo-description: Problemas comunes del AFCS y sus soluciones
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: ccf30bc990c1a7cdb261332403668af6f35aeb9e

---


# Solución de problemas del servicio de conversión automatizada de formularios


El artículo proporciona información sobre los problemas de instalación, configuración y administración que pueden surgir en un entorno de producción del Servicio de conversión automatizada de formularios. El documento también proporciona pasos básicos para la resolución de problemas y una explicación de los mensajes de error comunes.

## Errores comunes {#commonerrors}

| Error | Ejemplo |
|--- |--- |
| **Mensaje** de error <br> El encabezado de token de acceso no está disponible. <br><br>**Motivo **<br>: Un administrador ha creado varias configuraciones IMS o la configuración IMS no puede acceder al servicio AFCS en Adobe Cloud.<br><br>**Resolución** <br> Si hay varias configuraciones, elimine todas las configuraciones y [cree una nueva configuración](configure-service.md#obtainpubliccertificates). <br> Si hay una sola configuración, use **[!UICONTROL Health Check]** para [comprobar la conectividad](configure-service.md#createintegrationoption). | ![El encabezado de token de acceso no está disponible](assets/invalid-ims-configuration.png) |
| **Mensaje** de error <br> No se puede conectar al servicio.  <br><br>**Motivo **<br>: URL de servicio incorrecta o no se menciona ninguna URL de servicio en los servicios de nube del servicio de conversión automatizada de formularios.<br><br>**Resolución** <br> Corrección de la URL [del servicio](configure-service.md#configure-the-cloud-service) en los servicios de nube de servicios de conversión de formularios automatizados. | ![No se puede conectar con el servicio.](assets/wrong-endpoint-configured.png) |
| **Mensaje** de error <br> El servicio no pudo convertir el formulario.  <br><br>**Motivo **por el que<br>los problemas de conectividad de red se producen al final o el servicio está inactivo debido al mantenimiento o interrupción programados en Adobe Cloud.<br><br>**Resolución** <br> Resuelva los problemas de conectividad de red al final y compruebe el estado del servicio en https://status.adobe.com/# para obtener información sobre interrupciones planificadas o no planificadas. | ![No se puede conectar con el servicio.](assets/service-failure.png) |
