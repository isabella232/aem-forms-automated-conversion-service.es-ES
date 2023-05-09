---
title: Configuración del servicio de conversión automatizada de formularios
description: Prepare la instancia de AEM para utilizar el servicio de conversión automatizada de formularios
role: User, Admin
exl-id: 8f21560f-157f-41cb-ba6f-12a4d6e18555
source-git-commit: 47261710e6616c27c210ac53bffcc2387a06ea7a
workflow-type: ht
source-wordcount: '2684'
ht-degree: 100%

---

# Configuración del servicio de conversión automatizada de formularios {#about-this-help}

Esta ayuda describe cómo un administrador de AEM puede configurar el servicio de conversión automatizada de formularios para automatizar la conversión de sus formularios PDF a formularios adaptables. Esta ayuda es para los administradores de TI y AEM de su organización. La información proporcionada se basa en la suposición de que cualquiera que lea esta Ayuda está familiarizado con las siguientes tecnologías:

* Instalación, configuración y administración de paquetes de Adobe Experience Manager y AEM.

* Uso de los sistemas operativos Linux® y Windows® de Microsoft®,

* Configuración de los servidores de correo SMTP.

<!--- >[!VIDEO](https://video.tv.adobe.com/v/29267/) 

**Watch the video or read the article to configure Automated Forms Conversion service** -->

## Incorporación{#onboarding}

El servicio está disponible de forma gratuita para los clientes a plazo de AEM Forms 6.4 y AEM Forms 6.5 locales y los clientes empresariales de Managed Services de Adobe. Póngase en contacto con el equipo de ventas de Adobe o con su representante de Adobe para solicitar acceso al servicio. El servicio también está disponible de forma gratuita y está prehabilitado para los clientes de AEM Forms as a Cloud Service.

Adobe posibilita el acceso a su organización y otorga los pertinentes privilegios a las personas de su organización designadas como administradores. Estos administradores pueden otorgar acceso a los desarrolladores de AEM Forms (usuarios) de su organización para conectarse al servicio.

## Requisitos previos {#prerequisites}

Para utilizar el servicio de conversión automatizada de formularios, es necesario lo siguiente:

* Que el servicio de conversión automatizada de formularios esté habilitado para su organización.
* Que tenga una cuenta de Adobe ID con privilegios de administrador para el servicio de conversión.
* Que tenga una instancia de autor de AEM Forms as a Cloud Service que se esté ejecutando AEM 6.4, AEM 6.5 o con el Service Pack de AEM más reciente o con las actualizaciones más recientes.
* Un usuario de AEM (en la instancia de AEM) que sea miembro del grupo de usuarios de formularios.

## Configuración del entorno {#setuptheservice}

Antes de utilizar el servicio, prepare la instancia de autor de AEM para conectarse al servicio que se ejecuta en Adobe Cloud. Realice los siguientes pasos en la secuencia indicada para preparar la instancia para el servicio:

1. [Descargue e instale AEM 6.4, AEM 6.5 o AEM Forms as a Cloud Service incorporado](#aemquickstart)
1. [Descargue e instale el Service Pack de AEM más reciente](#servicepack)
1. [Descargue e instale el último paquete de complementos de AEM Forms](#downloadaemformsaddon)
1. (opcional) [Descargue e instale el paquete de conectores más reciente](#installConnectorPackage)
1. [Creación de temas y plantillas personalizadas](#referencepackage)

### Descarga e instalación de AEM 6.4 o AEM 6.5 o AEM Forms as a Cloud Service incorporado {#aemquickstart}


El servicio de conversión automatizada de formularios se ejecuta en la instancia de autor de AEM. Se necesita AEM 6.4, AEM 6.5 o AEM Forms as a Cloud Service para configurar la instancia de autor de AEM.

* Si no tiene AEM 6.4 o AEM 6.5 en funcionamiento, descárguelo desde las siguientes ubicaciones. Después de descargar AEM, para obtener instrucciones para configurar una instancia de autor de AEM, consulte [implementación y mantenimiento](https://helpx.adobe.com/es/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall):

   * Si ya es cliente de AEM, descargue AEM 6.4 o AEM 6.5 desde el [sitio web de licencias de Adobe](http://licensing.adobe.com).

   * Si es socio de Adobe, utilice el [Programa de formación para socios de Adobe](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) para solicitar AEM 6.4 o AEM 6.5.

* Si utiliza AEM Forms as a Cloud Service, consulte Incorporarse a [AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-forms-cloud-service.html?lang=es#setup-environment) y la [configuración de un entorno de desarrollo local](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-local-development-environment.html?lang=es#setup-environment).

### (Solo para AEM 6.4 y 6.5) Descarga e instalación del último Service Pack de AEM {#servicepack}

Descargue e instale el Service Pack de AEM más reciente. Para obtener instrucciones detalladas, consulte las [Notas de la versión de Service Pack de AEM 6.4](https://helpx.adobe.com/es/experience-manager/6-4/release-notes/sp-release-notes.html) o las [Notas de la versión de Service Pack de AEM 6.5](https://helpx.adobe.com/es/experience-manager/6-5/release-notes/sp-release-notes.html).

### (Solo para AEM 6.4 y 6.5) Descarga e instalación del paquete de complementos de AEM Forms  {#downloadaemformsaddon}

La instancia de AEM contiene funciones básicas para los formularios. El servicio de conversión requiere todas las funciones de AEM Forms. Descargue e instale el paquete de complementos de AEM Forms para disponer de todas las funcionalidades de AEM Forms. El paquete es necesario para configurar y ejecutar el servicio de conversión. Para obtener instrucciones detalladas, consulte [Instalación y configuración de las funcionalidades de captura de datos.](https://helpx.adobe.com/es/experience-manager/6-5/forms/using/installing-configuring-aem-forms-osgi.html)

>[!NOTE]
> Asegúrese de realizar las configuraciones obligatorias posteriores a la instalación después de instalar el paquete de complementos.

<!-- ### (Optional) Download and install connector package  {#installConnectorPackage}

The connector package provides early access to the [Auto-detect logical sections](convert-existing-forms-to-adaptive-forms.md#run-the-conversion) features and improvements delivered in release AFC-2020.03.1. Do not install the package if you do not require feature and improvements delivered in AFC-2020.03.1.  You can [download the connector package from AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1). -->


### Creación de temas y plantillas personalizadas {#referencepackage}

Si comienza con AEM 6.4 o AEM 6.5 en [modo de producción](https://helpx.adobe.com/es/experience-manager/6-5/sites/administering/using/security-checklist.html) (modo nosamplecontent run), los paquetes de referencia no están instalados. Los paquetes de referencia contienen muestras de temáticas y plantillas. El servicio de conversión automatizada de formularios necesita al menos una temática y una plantilla para convertir un formulario PDF en un formulario adaptable. Cree una temática y una plantilla personalizadas propias y marque [configuración del servicio](#configure-the-cloud-service) para utilizar plantillas y temáticas personalizadas antes de usar el servicio.

También puede descargar e instalar el paquete de [Activos de referencia de AEM Forms](https://experience.adobe.com/#/downloads/content/software-distribution/es-es/aemcloud.html) en la instancia de autor. Crea algunas temáticas y plantillas de referencia.

## Configuración del servicio {#configure-the-service}

Antes de comenzar con la configuración del servicio y conectar la instancia local con el servicio que se ejecuta en Adobe Cloud, obtenga información sobre los perfiles y los privilegios necesarios para conectarse al servicio. El servicio utiliza dos tipos de perfiles, administradores y desarrolladores:

* **Administradores**: son responsables de administrar el software y los servicios de Adobe para su organización. Conceden acceso a los desarrolladores de su organización para que se conecten al servicio de conversión automatizada de formularios que se ejecuta en Adobe Cloud. Cuando se aprovisiona un administrador para una organización, este recibe un correo electrónico con el título **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']**. Si es administrador, compruebe si hay un correo electrónico en su buzón con el título mencionado anteriormente y proceda a [conceder acceso a los desarrolladores de su organización](#adduseranddevs).

![Correo electrónico de concesión de acceso del administrador](assets/admin-console-adobe-io-access-grantedx75.png)

* **Desarrolladores**: conectan una instancia de autor de AEM Forms local con el servicio de conversión automatizada de formularios que se ejecuta en Adobe Cloud. Cuando un administrador concede derechos a un desarrollador para que se conecte al servicio de conversión automatizada de formularios, se envía un mensaje de correo electrónico al desarrollador con el título “Ahora tiene acceso como desarrollador para administrar las integraciones de API de Adobe para su organización”. Si es un desarrollador, compruebe si tiene un correo electrónico en su buzón con el título mencionado anteriormente y proceda a [Conectar la instancia de AEM local al servicio de conversión automatizada de formularios en Adobe Cloud.](#connectafcadobeio)

![Correo electrónico de concesión de acceso para desarrolladores](assets/email-developer-accessx94.png)

### (Solo para administradores de AEM 6.4 y 6.5) Concesión de acceso a los desarrolladores de su organización {#adduseranddevs}

Una vez que Adobe habilita el acceso para su organización y proporciona los privilegios necesarios al administrador, este puede iniciar sesión en Admin Console (instrucciones detalladas a continuación), crear un perfil y agregar desarrolladores. Los desarrolladores pueden conectar una instancia local de AEM Forms al servicio de conversión automatizada de formularios en Adobe Cloud.

Los desarrolladores son miembros de su organización que están designados para ejecutar el servicio de conversión. Solo aquellos desarrolladores que se agregan al perfil del servicio de conversión automatizada de formularios de Adobe tienen derecho a utilizarlo. Realice los pasos siguientes para crear un perfil y agregarle desarrolladores. Se requiere un perfil como mínimo para conceder el acceso necesario a los desarrolladores de su organización.

1. Inicie sesión en [Admin Console](https://adminconsole.adobe.com/). Use el **Adobe ID** del administrador suministrado para utilizar el servicio de conversión automatizada de formularios para iniciar sesión. No utilice ningún otro ID o Federated ID para iniciar sesión.
1. Haga clic en la opción **[!UICONTROL Automated Forms Conversion]**.
1. Haga clic **[!UICONTROL New Profile]** en la pestaña **[!UICONTROL Products]**.
1. Especifique **[!UICONTROL Name]**, **[!UICONTROL Display Name]** y **[!UICONTROL Description]** para el perfil. Haga clic en **[!UICONTROL Done]**. Se crea el perfil.

   ![Especifique los detalles del nuevo perfil.](assets/create-new-profile-details.png)

1. Agregue un desarrollador al perfil. Para agregar a los desarrolladores, haga lo siguiente:
   1. En [Admin Console](https://adminconsole.adobe.com/enterprise), vaya a la pestaña Información general.
   1. Haga clic en **[!UICONTROL Assign Developers]** en la tarjeta de producto requerida.
   1. Escriba la dirección de correo electrónico de los desarrolladores y, opcionalmente, los nombres y apellidos.
   1. Seleccione los perfiles del producto. Pulse **[!UICONTROL Save]**.

Repita los pasos anteriores para todos los usuarios. Para obtener más información sobre cómo agregar desarrolladores, vea [Administrar desarrolladores](https://helpx.adobe.com/es/enterprise/using/support-for-experience-cloud.html).

Una vez que un administrador agrega desarrolladores al perfil de Adobe I/O, se les notifica a los desarrolladores por correo electrónico. Después de recibir el correo electrónico, los desarrolladores pueden continuar con una [conexión de una instancia local de AEM Forms con el servicio de conversión automatizada de formularios en Adobe Cloud](#connectafcadobeio).

### (Solo para desarrolladores) Conexión de la instancia local de AEM Forms al servicio de conversión automatizada de formularios en Adobe Cloud {#connectafcadobeio}

Una vez que un administrador le proporcione acceso para desarrolladores, puede conectar la instancia local de AEM Forms al servicio de conversión automatizada de formularios que se ejecuta en Adobe Cloud. Realice los siguientes pasos en la secuencia indicada para conectar la instancia de AEM Forms al servicio:

* [Configuración de notificaciones por correo electrónico](configure-service.md#configureemailnotification)
* [Adición de usuarios a grupos de usuarios de los formularios](#adduserstousergroup)
* [Obtener certificados públicos](#obtainpubliccertificates)
* [Configuración de las API de servicio en Adobe Developer Console](#createintegration)
* [Configuración de Cloud Service](configure-service.md#configure-the-cloud-service)

#### Configuración de las notificaciones por correo electrónico {#configureemailnotification}

El servicio de conversión automatizada de formularios utiliza el servicio de correo Day CQ para enviar notificaciones por correo electrónico. Estas notificaciones por correo electrónico contienen información sobre las conversiones correctas o fallidas. Si no desea recibir notificaciones, omita estos pasos. Realice los siguientes pasos para configurar el servicio de correo Day CQ.

* Para AEM 6.4 Forms o AEM 6.5 Forms:

   1. Vaya al administrador de configuración de AEM en `http://localhost:4502/system/console/configMgr`
   1. Abra la configuración de Day CQ Mail Service. Especifique un valor para los campos **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]** y **[!UICONTROL From address]**. Haga clic en **[!UICONTROL Save]**.

      Puede ponerse en contacto con el proveedor de servicios de correo electrónico o el administrador de TI para obtener información sobre el nombre del host y el puerto del servidor SMTP. Puede utilizar cualquier dirección de correo electrónico válida en el campo de formulario. Por ejemplo, notification@example.com o donotreply@example.com.

   1. Abra la configuración **[!UICONTROL Day CQ Link Externalizer]**. En el campo **[!UICONTROL Domains]**, especifique el nombre del host o la dirección IP real y el número de puerto para las instancias locales, autor y publicación. Haga clic en **[!UICONTROL Save]**.

* Para AEM Forms as a Cloud Service, [registre una incidencia de soporte técnico para habilitar el servicio de correo electrónico](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=es#sending-email).

#### Adición de usuarios a grupos de usuarios de los formularios {#adduserstousergroup}

Especifique una dirección de correo electrónico en el perfil de AEM del usuario designado para ejecutar el servicio. Asegúrese de que el usuario sea miembro del grupo de [usuarios de formularios](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/forms-groups-privileges-tasks.html?lang=es). Se envían correos electrónicos a la dirección del usuario que ejecuta la conversión. Para especificar una dirección de correo electrónico para el usuario y agregar el usuario al grupo de usuarios de formularios, haga lo siguiente:

1. Inicie sesión en AEM en la instancia de autor de AEM Forms como administrador. Use sus credenciales de AEM locales para iniciar sesión. No use el Adobe ID para iniciar sesión. Toque **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Seleccione un usuario designado para ejecutar el servicio de conversión y pulse **[!UICONTROL Properties]**. Se abrirá la página Editar configuración de usuario.
1. Especifique una dirección de correo electrónico en el campo **[!UICONTROL Email]** y toque **[!UICONTROL Save]**. Se envían correos electrónicos a la dirección especificada si la conversión se realiza correctamente o si no.
1. Pulse la pestaña **Grupos**. En la pestaña seleccionar grupo, escriba y seleccione el grupo **usuarios de formularios**. Pulse **Guardar y cerrar**. El usuario es ahora miembro del grupo de usuarios de formularios.

#### (Solo para AEM 6.4 y 6.5) Obtener certificados públicos {#obtainpubliccertificates}

Un certificado público le permite autenticar su perfil en Adobe I/O.

1. Inicie sesión en la instancia de autor de AEM Forms. Navegue hasta **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Pulse **[!UICONTROL Create]**. Se abre la página **[!UICONTROL Adobe IMS Technical Account Configuration]**.

   ![La página Configuración de cuenta técnica de Adobe IMS](assets/adobe-ims-technical-account-configuration.png)

1. Seleccione **[!UICONTROL Automated Forms Conversion Service]** en Cloud Solution.

1. Seleccione la casilla de verificación **[!UICONTROL Create new certificate]** y especifique un alias. El alias sirve como nombre del cuadro de diálogo. Pulse **[!UICONTROL Create certificate]**. Aparece un cuadro de diálogo. Haga clic en **[!UICONTROL OK]**. Se crea un certificado.

1. Pulse **[!UICONTROL Download Public Key]** y guarde el archivo de certificado *AEM-Adobe-IMS.crt* en el equipo. El archivo de certificado se utiliza para la [Configuración de las API de servicio en Adobe Developer Console](#createintegration). Pulse **[!UICONTROL Next]**.

1. Especifique lo siguiente.

   * Título: especifique un título.
   * Servidor de autorización: [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)\

   Deje los demás campos en blanco por ahora (se proporcionarán más adelante). Mantenga la página abierta.

   <!--
   Comment Type: draft

   <li> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

#### (Solo para AEM 6.4 y 6.5) Configuración de las API de servicio en Adobe Developer Console {#createintegration}

Para utilizar el servicio de conversión automatizada de formularios, cree un proyecto y agregue la API del servicio de configuración automatizada de formularios al proyecto en la consola de Adobe Developer. La integración genera la clave de la API, el secreto del cliente y la carga útil (JWT).

1. Inicie sesión en [https://console.adobe.io/](https://console.adobe.io/). Utilice su cuenta de desarrollador de Adobe ID que el administrador haya aprovisionado para iniciar sesión en la consola de Adobe I/O.
1. Seleccione su organización en la esquina superior derecha. Si no conoce su organización, póngase en contacto con su administrador.
1. Toque **[!UICONTROL Create new project]**. Aparece una pantalla para comenzar con el nuevo proyecto. Toque **[!UICONTROL Add API]**. Aparece una pantalla con una lista de todas las API habilitadas para su cuenta.
1. Seleccione **[!UICONTROL Automated Forms Conversion service]** y pulse **[!UICONTROL Next]**. Aparece una pantalla para configurar la API.
1. Seleccione la opción [!UICONTROL Upload your public key], cargue el archivo AEM-Adobe-IMS.crt descargado en la sección [Obtener certificados públicos](#obtainpubliccertificates) y pulse **[!UICONTROL Next]**. Aparece la opción de la credencial Crear una nueva cuenta de servicio (JWT). Pulse **[!UICONTROL Next]**.
1. Seleccione un perfil de producto y pulse **[!UICONTROL Save configured API]**. Seleccione el perfil creado al [conceder acceso a los desarrolladores de su organización](#adduseranddevs). Si no conoce el perfil que desea seleccionar, póngase en contacto con su administrador.
1. Pulse **[!UICONTROL Service Account (JWT)]** para ver la clave de la API, el secreto del cliente y otra información necesaria para conectar la instancia de AEM local al servicio de conversión de automatizada de formularios. La información de la página se utiliza para crear la configuración de IMS en el equipo local.

1. Abra la página Configuración de IMS en la instancia local. Si mantuvo la página abierta al final de la sección, podrá [Obtener un certificado público](#obtainpubliccertificates).

   ![Especifique el título, la clave de API, el secreto del cliente y la carga útil ](assets/ims-configuration-details.png)

1. En la página técnica de Adobe IMS, especifique la clave de API y el secreto del cliente. Utilice los valores especificados en la Cuenta de servicio (JWT) de la página de Adobe Developer console.

   >[!NOTE]
   >
   >
   >Para la carga útil, utilice el código proporcionado en la pestaña Generar JWT de la página de la cuenta del servicio (JWT) de Adobe Developer Console.

1. Pulse **[!UICONTROL Save]**. Se crea la configuración IMS.

   >[!CAUTION]
   >
   >Cree solo una configuración IMS. No cree más de una.

1. Seleccione la configuración de IMS y pulse **[!UICONTROL Check Health]**. Aparecerá un cuadro de diálogo. Pulse **[!UICONTROL Check]**. Cuando la conexión se realiza correctamente, aparece el mensaje *Token recuperado correctamente*.

   ![Cuando la conexión se realiza correctamente, aparece el mensaje Token recuperado correctamente.](assets/health-check.png)

   <br/> <br/>

#### Configuración de Cloud Service {#configure-the-cloud-service}

Cree una configuración de Cloud Service para conectar la instancia de AEM al servicio de conversión. También le permite especificar una plantilla, un tema y fragmentos de formulario para una conversión. Puede crear varias configuraciones de servicios para la nube por separado para cada conjunto de formularios. Por ejemplo, puede tener una configuración independiente para los formularios del departamento de ventas y otra para los de asistencia al cliente. Siga estos pasos para crear la configuración del servicio en la nube:

1. En la instancia de AEM Forms, pulse **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]**> **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**.
1. Pulse la carpeta **[!UICONTROL Global]** y pulse **[!UICONTROL Create]**. Aparece la página para crear la configuración de la conversión automatizada de formularios. La configuración se crea en la carpeta Global. También puede crear la configuración en una carpeta diferente que ya exista o crear una para las configuraciones.

1. En la página **[!UICONTROL Create Automated Forms Conversion Configuration]**, especifique el valor de los campos siguientes y pulse **[!UICONTROL Next]**.

   | Campo | Descripción |
   |--- |--- |
   | Título | Título único para la configuración. El título se muestra en la IU utilizada para iniciar la conversión. |
   | Nombre | Nombre único para la configuración. La configuración se guarda en el repositorio CRX con el nombre especificado. El nombre puede ser idéntico al título. |
   | Ubicación de la miniatura | Ubicación de la miniatura para la configuración. |
   | URL del servicio | URL del servicio de conversión automatizada de los formularios en Adobe Cloud. Utilice la URL `https://aemformsconversion.adobe.io/`. |
   | Plantilla | Plantilla predeterminada que se aplica a los formularios convertidos. Puede especificar una plantilla diferente antes de iniciar la conversión. Una plantilla contiene estructura básica y contenido inicial para un formulario adaptable. Puede elegir una plantilla de las proporcionadas de forma predeterminada. También puede crear una plantilla personalizada. |
   | Tema | Tema predeterminado que se aplica a los formularios convertidos. Siempre puede especificar un tema diferente antes de iniciar la conversión.  Puede hacer clic en el icono para elegir un tema que se proporcione de forma predeterminada. También puede crear un tema personalizado. |
   | Fragmentos existentes | Ubicación de los fragmentos existentes, si los hay. |
   | Metamodelo personalizado | Ruta del archivo .schema.json del metamodelo personalizado. Puede crear metamodelos independientes para los idiomas inglés, francés, alemán, español, italiano y portugués. |

1. En la pestaña **[!UICONTROL Advanced]** de la página **[!UICONTROL Create Automated Forms Conversion Configuration]**, especifique el valor para el siguiente campo:

   <table>
   <thead>
   <tr>
   <th>Campo</th>
   <th>Descripción</th>
   </tr>
   </thead>
   <tbody>
   <tr>
   <td >Generar documento de registro</td>
   <td>Seleccione la opción para generar automáticamente el documento de registro para los formularios convertidos. La opción solo está disponible para formularios basados en XFA (formularios XDP y PDF). Cuando se activa la opción, después de enviar un formulario, se puede permitir a los clientes mantener un registro, impreso o en formato de documento, de la información que han rellenado en el formulario, para su referencia futura. Este registro se denomina documento de registro.</td>
   </tr>
   <tr>
   <td>Activar Analytics</td>
   <td>(Solo para AEM 6.4 y 6.5) Seleccione la opción para habilitar Adobe Analytics en todos los formularios convertidos. Antes de utilizar la opción, compruebe que Adobe Analytics esté habilitado para su instancia de AEM Forms.</td>
   </tr>
   </tbody>
   </table>

   * Cuando el origen es un formulario basado en XFA con la extensión .XDP, el DOR de salida conserva el diseño XFA. De lo contrario, el servicio de conversión utiliza una plantilla predeterminada para generar DOR para otros formularios basados en XFA.
   * Cuando se envía un formulario XFA, los datos enviados se guardan como un elemento XML o un atributo. Por ejemplo, `<Amount currency="USD"> 10.00 </Amount>`. La moneda se guarda como un atributo y la cantidad de divisa (10.00), como un elemento. Los datos de envío de un formulario adaptable no tienen atributos, solo tienen elementos. Por lo tanto, cuando un formulario basado en XFA se convierte en formulario adaptable, los datos de envío de formulario adaptable contienen un elemento para cada atributo. Por ejemplo,

   ```css
      {
         "Type": "Principal",
   
         "Amount": "10.00",
   
         "currency": "USD"
      }
   ```

1. Pulse **[!UICONTROL Create]**. Se crea la configuración de la nube. La instancia de AEM Forms está lista para empezar a convertir formularios heredados a formularios adaptables.
