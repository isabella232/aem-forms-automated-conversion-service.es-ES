---
title: 'Novedades? Notas de la versión: Servicio de conversión automatizada de formularios'
description: 'Obtenga información sobre las últimas funciones y errores corregidos para el servicio de conversión de formularios automatizados '
translation-type: tm+mt
source-git-commit: e88b9606878cb408c0369b5f20a644db93578f64

---


# Servicio de conversión automatizada de formularios: Notas de la versión

El servicio de conversión automatizada de formularios recibe mejoras de forma continua. Para mantenerse al día con los últimos desarrollos, visite esta página con regularidad. Esta página le proporciona información sobre:

* Últimas versiones
* Nuevas funciones
* Correcciones de errores
* Funcionalidad obsoleta
* Instrucciones especiales
* Planes futuros de cambios

Esta página se actualiza mensualmente, por lo que puede volver a verla regularmente.

## 20 de marzo de 2020 (AFC-2020.03.1)

### Novedades

**Detectar automáticamente secciones lógicas en un formulario**

De forma predeterminada, el servicio crea un panel de nivel superior independiente para cada página de un formulario PDF de entrada. Ahora puede seleccionar la **[!UICONTROL Auto-detect logical sections]** opción para eliminar la noción de crear un panel de nivel superior independiente para cada página PDF y detectar automáticamente las secciones lógicas. Los clubes de servicio relacionaban los campos de un formulario con una sección lógica. Por ejemplo: todos los campos relacionados con la dirección de facturación se agrupan en una sección y todos los campos relacionados con la dirección de envío se agrupan en una sección diferente. El servicio también crea un panel de nivel superior independiente para cada sección lógica detectada automáticamente.

### Qué se ha mejorado

**Mejoras en la detección de listas**

El servicio ahora es más eficaz en la detección de listas con viñetas y numeradas. Ahora puede detectar fácilmente listas de varios niveles.

### Instrucciones especiales

**Instalar el paquete de conector del servicio de conversión de formularios automatizados**

Debe utilizar el paquete de conector 1.1.38 o superior para utilizar las últimas funciones y mejoras de la versión AFC-2020.03.1. Puede descargar el paquete de conector desde Uso compartido de paquetes [AEM](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/fd/AEM-Forms-6.5.4.0-WIN).

Si ya dispone de un entorno de servicio Conversión automatizada de formularios en ejecución, para utilizar las últimas funciones del servicio de conversión, instale el Service Pack más reciente, el paquete adicional de AEM Forms más reciente y el paquete de conector más reciente en el orden mencionado. Para obtener instrucciones detalladas, consulte el artículo [Configurar el servicio](configure-service.md) Conversión automatizada de formularios.
