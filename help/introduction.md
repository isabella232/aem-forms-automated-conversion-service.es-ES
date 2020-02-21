---
title: Introducción
description: 'Acelerar la conversión de formularios impresos a formularios adaptables '
translation-type: tm+mt
source-git-commit: ef5789dabccc65dcf988b9424b435aa036017691

---


# Introducción {#introduction-to-automated-forms-conversion-service}

El servicio Conversión automatizada de formularios ayuda a acelerar la digitalización y modernización de la experiencia de captura de datos mediante la conversión automatizada de formularios PDF a formularios adaptables. El servicio, con la tecnología Adobe Sensei, convierte automáticamente los formularios PDF en formularios adaptables basados en HTML5, adaptables y fáciles de usar en el dispositivo. A la vez que aprovecha las inversiones existentes en formularios PDF y XFA, el servicio también aplica validaciones, estilo y presentación adecuados a los campos de formulario adaptables durante la conversión. El servicio ayuda a:

* Ahorre el esfuerzo manual necesario para convertir formularios impresos en formularios adaptables
* Aplica patrones y validaciones apropiadas durante la conversión
* Generar documento de registro durante la conversión
* Agrupar los campos que se suelen incluir en fragmentos de formulario reutilizables
* Habilita Adobe Analytics durante la conversión

![Es simple. Usted sólo nos provee los formularios de origen y nos deja todo a nosotros. Le proporcionaremos hermosas formas adaptables. Por supuesto, usted pensará con el resultado a su satisfacción. ](assets/pdf-to-adaptive-form-gitx50.gif)

## Incorporación {#onboarding}

El servicio está disponible de forma gratuita para los clientes a plazo local de AEM 6.5 Forms y para los clientes empresariales de servicios gestionados de Adobe. Puede ponerse en contacto con el equipo de ventas de Adobe o con su representante de Adobe para solicitar acceso al servicio.

Adobe habilita el acceso para su organización y proporciona los privilegios requeridos a la persona designada como administrador en su organización. El administrador puede otorgar acceso a los desarrolladores (usuarios) de AEM Forms de su organización para conectarse al servicio. Consulte [Configuración del servicio](configure-service.md) de conversión automatizada de formularios para obtener más información.

## Formularios e idiomas PDF admitidos {#supported-languages-and-pdf-forms}

El servicio admite formularios PDF no interactivos, formularios creados con Adobe Acrobat, conocidos como AcroForms, y formularios basados en XFA creados con AEM Forms o Adobe LiveCycle.

El servicio solo puede convertir formularios en inglés en formularios adaptables. Puede traducir los formularios adaptables generados a otro idioma mediante el flujo de trabajo [de traducción de](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)AEM.

## Flujo de trabajo de conversión {#conversion-workflow}

El servicio Conversión automatizada de formularios se ejecuta en Adobe Cloud. Puede conectar la instancia de AEM al servicio, cargar formularios en la instancia de AEM e iniciar la conversión. El proceso de conversión completo es el siguiente:

![Flujo de trabajo](assets/conversion-workflow.png)

### 1.Configuración del entorno {#set-up-the-environment}

El servicio Conversión automatizada de formularios se ejecuta en Adobe Cloud. [Configure la cuenta de Adobe I/O de su organización y conecte la instancia](configure-service.md) local de AEM al servicio de conversión que se ejecuta en Adobe Cloud.

### 2. Convertir formularios PDF en formularios adaptables {#use-the-conversion-service}

Una vez configurado el entorno de AEM Forms, para convertir los formularios PDF a formularios adaptables, [cargue los formularios](convert-existing-forms-to-adaptive-forms.md) PDF en la instancia de AEM e [inicie la conversión](convert-existing-forms-to-adaptive-forms.md#run-the-conversion). Antes de cargar los formularios, tenga en cuenta lo siguiente:

* No cargue los formularios protegidos. El servicio no convierte formularios cifrados y protegidos con contraseña.
* No cargue formularios escaneados, coloreados, que no estén en inglés ni rellenados. Estos formularios no son compatibles.
* No cargue formularios PDF con espacios en el nombre del archivo.
* No cargue carteras [PDF](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html). El servicio no convierte una cartera PDF en formularios adaptables.
* Realice los cambios sugeridos en los formularios PDF que se describen en el artículo [Prácticas recomendadas y consideraciones](styles-and-pattern-considerations-and-best-practices.md) .
* Lea el artículo Problemas [](known-issues.md) conocidos para evitar escollos.

### 3. Revisar formularios convertidos {#review-converted-forms}

Los formularios del mundo real pueden tener requisitos complejos de captura de datos en términos de diseño de campo, nominación o sugerencias implícitas que pueden no ser captadas con precisión por la lógica de detección basada en AI/ML. Una vez completada la conversión automatizada, puede utilizar el editor [](review-correct-ui-edited.md) Revisar y corregir para revisar el formulario convertido y realizar las actualizaciones necesarias y generar una salida mejorada más cercana a la experiencia deseada. Después de realizar los cambios necesarios, vuelva a enviar el formulario para la conversión.

El tiempo empleado para la conversión automatizada depende de una variedad de factores, como el tamaño del formulario de entrada, la complejidad del formulario, el préstamo en la cola de procesamiento del servicio. Se notifica al usuario el progreso regularmente mediante el indicador de estado en la carpeta o archivo. Cuando se completa la conversión, también se envía una notificación por correo electrónico a la dirección de correo electrónico configurada.
