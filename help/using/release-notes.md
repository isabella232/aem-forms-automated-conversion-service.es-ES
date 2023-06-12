---
title: 'Novedades Notas de la versión: Servicio de conversión automatizada de formularios'
description: Obtenga información sobre las últimas funciones y los errores corregidos para el Servicio de conversión automatizada de formularios
exl-id: fccafbc9-28c1-4736-922c-24d675b25213
source-git-commit: 298d6c0641d7b416edb5b2bcd5fec0232f01f4c7
workflow-type: tm+mt
source-wordcount: '451'
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

## 24 de febrero de 2022 (AFC-2022.02.0) {#feb-2022}

* Se agregó la capacidad a [convertir las secciones en fragmentos de forma automática](convert-existing-forms-to-adaptive-forms.md) para mejorar la velocidad de procesamiento de los formularios convertidos y facilitar la carga de formularios adaptables grandes en el editor.

## 29 de agosto de 2021 (AFC-2021.08.0) {#aug-2021}

* Se agregó la capacidad de convertir formularios PDF adaptables en italiano y portugués.

## 29 de julio de 2021 (AFC-2021.07.2) {#july-2021}

* Se ha agregado la capacidad de convertir un formulario de PDF en francés, alemán y español a un formulario adaptable.

## 24 de junio de 2021 (AFC-2021.06.2) {#june-2021}

### Mejoras {#june-2021-improvements}

Se ha mejorado la precisión para detectar secciones lógicas en los formularios de origen de forma automática y convertirlas en los paneles de formularios adaptables correspondientes.

## 3 de marzo de 2021 (AFC-2021.02.2) {#mar-2021}

### Mejoras {#march-2021-improvements}

Mejoras en la organización del contenido del formulario en campos y grupos de opciones al convertir un formulario de origen en un formulario adaptable.

## 2 de febrero de 2021 (AFC-2021.01.2) {#feb-2021}

### Mejoras {#feb-2021-improvements}

Mejoras en la organización del contenido del formulario en paneles y generación de títulos para paneles, al mismo tiempo que se convierte un formulario de origen en uno adaptable.

## 16 de julio de 2020 (AFC-2020.07.2) {#jul-2020}

### Novedades {#whats-new-jul-2020-}

Ya es posible convertir formularios PDF en color a formularios adaptables.

### Mejoras {#jul-2020-improvements}

Mejoras de la conversión automatizada de los campos de texto, formulario y grupo de selección a los correspondientes componentes de formulario adaptable.

## 20 de marzo de 2020 (AFC-2020.03.1) {#mar-2020}

### Acceso temprano {#early-access}

**Detección automática de secciones lógicas en un formulario**

De forma predeterminada, el servicio crea un panel independiente de nivel superior para cada página de un formulario PDF. Ahora puede usar la opción **[!UICONTROL Auto-detect logical sections]** para soltar paneles de nivel de página (basados en el número de página) y crear solo paneles lógicos. También agrupa los campos que no pertenecen a ninguna sección con la sección lógica anterior y los campos de una sección lógica se distribuyen en dos páginas adyacentes en una sola sección lógica. Por ejemplo, si algunos campos de una sección lógica están al final de la página uno y otros al comienzo de la página dos, todos esos campos se agrupan en una sola sección lógica.

### Mejoras {#mar-2020-improvements}

**Mejoras en la detección de listas**

El servicio ahora es más eficiente en la detección de listas numeradas y con viñetas.

### Instrucciones especiales {#special-instructions}

**Instalación del paquete del conector del servicio de conversión automatizada de formularios**

Se necesita el paquete del conector 1.1.38 o posterior para utilizar las últimas funciones y mejoras de la versión AFC-2020.03.1.

Si ya tiene un entorno de servicio de conversión automatizada de formularios en funcionamiento, para usar las últimas funciones del servicio de conversión, instalar el último paquete de servicios, el último paquete de complemento de AEM Forms y el último paquete del conector en el orden mencionado. Para obtener instrucciones detalladas al respeto, consulte el artículo [Configurar el servicio de conversión automatizada de formularios](configure-service.md).
