---
title: 'Novedades? Notas de la versión: Servicio de conversión automatizada de formularios'
description: 'Obtenga información sobre las últimas funciones y errores corregidos para el servicio de conversión de formularios automatizados '
translation-type: tm+mt
source-git-commit: dc17dfcb331df6144b8a7ce3c9c9d840b1182a95

---


# Servicio de conversión automatizada de formularios: Notas de la versión

El servicio de conversión automatizada de formularios recibe mejoras de forma continua. Para mantenerse al día con los últimos desarrollos, visite esta página con regularidad. Esta página le proporciona información sobre:

* Acceso anticipado
* Últimas versiones
* Nuevas funciones
* mejoras
* Correcciones de errores
* Funcionalidad obsoleta
* Instrucciones especiales
* Planes futuros de cambios

## 20 de marzo de 2020 (AFC-2020.03.1)

### Acceso anticipado

**Detectar automáticamente secciones lógicas en un formulario**

La versión AFC-2020.03.1 proporciona acceso anticipado a la **[!UICONTROL Auto-detect logical sections]** función.

De forma predeterminada, el servicio crea un panel de nivel superior independiente para cada página de un formulario PDF. Ahora puede utilizar la **[!UICONTROL Auto-detect logical sections]** opción para colocar paneles de nivel de página (paneles basados en números de página) y crear solo paneles lógicos.  También agrupa los campos que no pertenecen a ninguna sección con una sección lógica anterior y los campos de una sección lógica extendidos en dos páginas adyacentes en una sola sección lógica. Por ejemplo: si algunos campos de una sección lógica se encuentran al final de la página uno y algunos están al comienzo de la página dos, todos esos campos se agrupan en una sola sección lógica.

Debe utilizar la función el paquete de conector 1.1.38 o superior para utilizar la **[!UICONTROL Auto-detect logical sections]** . Puede descargar el paquete de conector desde Uso compartido de paquetes [AEM](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1).

### Qué se ha mejorado

**Mejoras en la detección de listas**

El servicio es ahora más eficiente en la detección de listas con viñetas y numeradas.