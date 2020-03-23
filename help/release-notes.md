---
title: 'Novedades? Notas de la versión: Servicio de conversión automatizada de formularios'
description: 'Obtenga información sobre las últimas funciones y errores corregidos para el servicio de conversión de formularios automatizados '
translation-type: tm+mt
source-git-commit: e01334d9a22ab95749e9b9b459da8886ae1ccd78

---


# Servicio de conversión automatizada de formularios: Notas de la versión

El servicio de conversión automatizada de formularios recibe mejoras de forma continua. Para mantenerse al día con los últimos desarrollos, visite esta página con regularidad. Esta página le proporciona información sobre:

* Últimas versiones
* Nuevas funciones
* Correcciones de errores
* Funcionalidad obsoleta
* Instrucciones especiales
* Planes futuros de cambios

## 20 de marzo de 2020 (AFC-2020.03.1)

### Novedades

**Detectar automáticamente secciones lógicas en un formulario**

De forma predeterminada, el servicio crea un panel de nivel superior independiente para cada página de un formulario PDF. Ahora puede utilizar la **[!UICONTROL Auto-detect logical sections]** opción para colocar paneles de nivel de página (paneles basados en números de página) y crear solo paneles lógicos.  También agrupa los campos que no pertenecen a ninguna sección con una sección lógica anterior y los campos de una sección lógica extendidos en dos páginas adyacentes en una sola sección lógica. Por ejemplo: si algunos campos de una sección lógica se encuentran al final de la página uno y algunos están al comienzo de la página dos, todos esos campos se agrupan en una sola sección lógica.

### Qué se ha mejorado

**Mejoras en la detección de listas**

El servicio ahora es más eficaz en la detección de listas con viñetas y numeradas. Ahora puede detectar fácilmente listas de varios niveles.

### Instrucciones especiales

**Instalar el paquete de conector del servicio de conversión de formularios automatizados**

Debe utilizar el paquete de conector 1.1.38 o superior para utilizar las últimas funciones y mejoras de la versión AFC-2020.03.1. Puede descargar el paquete de conector desde Uso compartido de paquetes [AEM](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1).

Si ya dispone de un entorno de servicio Conversión automatizada de formularios en ejecución, para utilizar las últimas funciones del servicio de conversión, instale el Service Pack más reciente, el paquete adicional de AEM Forms más reciente y el paquete de conector más reciente en el orden mencionado. Para obtener instrucciones detalladas, consulte el artículo [Configurar el servicio](configure-service.md) Conversión automatizada de formularios.
