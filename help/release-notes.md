---
title: 'Novedades Notas de la versión: Servicio de conversión automatizada de formularios'
description: 'Obtenga información sobre las últimas funciones y los errores corregidos para el Servicio de conversión automatizada de formularios '
translation-type: ht
source-git-commit: 5031050795a558795c151e9f3c26a16736566adf
workflow-type: ht
source-wordcount: '305'
ht-degree: 100%

---


# Notas de la versión

El Servicio de conversión automatizada de formularios es objeto de mejoras continuas. Para estar al día de los desarrollos más recientes, visite esta página regularmente. Esta página le proporciona información sobre:

* Acceso temprano
* Últimas versiones
* Nuevas funciones
* Mejoras
* Corrección de errores
* Funcionalidad obsoleta
* Instrucciones especiales
* Planes de futuros cambios

## 20 de marzo de 2020 (AFC-2020.03.1)

### Acceso temprano

**Detección automática de secciones lógicas en un formulario**

De forma predeterminada, el servicio crea un panel independiente de nivel superior para cada página de un formulario PDF. Ahora puede usar la opción **[!UICONTROL Auto-detect logical sections]** para soltar paneles de nivel de página (basados en el número de página) y crear solo paneles lógicos. También agrupa los campos que no pertenecen a ninguna sección con la sección lógica anterior y los campos de una sección lógica se distribuyen en dos páginas adyacentes en una sola sección lógica. Por ejemplo, si algunos campos de una sección lógica están al final de la página uno y otros al comienzo de la página dos, todos esos campos se agrupan en una sola sección lógica.

### Mejoras

**Mejoras en la detección de listas**

El servicio ahora es más eficiente en la detección de listas numeradas y con viñetas.

### Instrucciones especiales

**Instalación del paquete del conector del Servicio de conversión automatizada de formularios**

Se necesita el paquete del conector 1.1.38 o una versión superior para utilizar las últimas funciones y mejoras de la versión AFC-2020.03.1. Puede descargar el paquete del conector de [Uso compartido de paquetes AEM](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1).

Si ya tiene un entorno de servicio de conversión automatizada de formularios en funcionamiento, para usar las últimas funciones del servicio de conversión, instalar el último paquete de servicios, el último paquete de complemento de AEM Forms y el último paquete del conector en el orden mencionado. Para obtener instrucciones detalladas al respeto, consulte el artículo [Configurar el servicio de conversión automatizada de formularios](configure-service.md).