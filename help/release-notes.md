---
title: 'Novedades Notas de la versión: Servicio de conversión automatizada de formularios'
description: 'Obtenga información sobre las últimas funciones y los errores corregidos para el Servicio de conversión automatizada de formularios '
translation-type: tm+mt
source-git-commit: 176dfbf12d1147d0348957e2cc8ce9390529fe72
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 93%

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


## 01 de febrero de 2021 (AFC-2021.01.2)

Mejoras en la organización del contenido del formulario en paneles y la generación de títulos para paneles al convertir un formulario de origen en un formulario adaptable.

## 16 de julio de 2020 (AFC-2020.07.2)

### Novedades

Ya es posible convertir formularios PDF en color a formularios adaptables.

### Mejoras

Mejoras de la conversión automatizada de los campos de texto, formulario y grupo de selección a los correspondientes componentes de formulario adaptable.


## 20 de marzo de 2020 (AFC-2020.03.1)

### Acceso temprano

**Detección automática de secciones lógicas en un formulario**

De forma predeterminada, el servicio crea un panel independiente de nivel superior para cada página de un formulario PDF. Ahora puede usar la opción **[!UICONTROL Auto-detect logical sections]** para soltar paneles de nivel de página (basados en el número de página) y crear solo paneles lógicos. También agrupa los campos que no pertenecen a ninguna sección con la sección lógica anterior y los campos de una sección lógica se distribuyen en dos páginas adyacentes en una sola sección lógica. Por ejemplo, si algunos campos de una sección lógica están al final de la página uno y otros al comienzo de la página dos, todos esos campos se agrupan en una sola sección lógica.

### Mejoras {#improvements}

**Mejoras en la detección de listas**

El servicio ahora es más eficiente en la detección de listas numeradas y con viñetas.

### Instrucciones especiales

**Instalación del paquete del conector del servicio de conversión automatizada de formularios**

Se necesita el paquete del conector 1.1.38 o una versión superior para utilizar las últimas funciones y mejoras de la versión AFC-2020.03.1. Puede descargar el paquete del conector de [Uso compartido de paquetes AEM](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1).

Si ya tiene un entorno de servicio de conversión automatizada de formularios en funcionamiento, para usar las últimas funciones del servicio de conversión, instalar el último paquete de servicios, el último paquete de complemento de AEM Forms y el último paquete del conector en el orden mencionado. Para obtener instrucciones detalladas al respeto, consulte el artículo [Configurar el servicio de conversión automatizada de formularios](configure-service.md).