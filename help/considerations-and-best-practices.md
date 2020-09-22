---
title: 'Prácticas recomendadas y consideraciones '
description: nulo
seo-description: nulo
page-status-flag: never-activated
uuid: c2821264-39e2-44f8-b234-835c46f33fd5
topic-tags: introduction
discoiquuid: b786e40a-202e-4e17-a2f5-1f77c46538c2
privatebeta: true
index: false
translation-type: tm+mt
source-git-commit: bc7a0a86a211214d6e43e7c95809f6f40fe267f8
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 8%

---


# Prácticas recomendadas y consideraciones {#do-not-publish-best-practices-and-considerations}

<!--
[DO NOT PUBLISH]
-->

El servicio de conversión automatizada de AEM Forms convierte un formulario PDF en un formulario adaptable. El servicio utiliza inteligencia artificial y algoritmos de aprendizaje automático para comprender el diseño y los campos del formulario de origen. Cada servicio de aprendizaje automático aprende continuamente de los datos de origen y produce una salida mejorada con cada repetición. Estos servicios aprenden de la experiencia como humanos.

El servicio de conversión automatizada de Forms se capacita en un gran conjunto de formularios. Identifica fácilmente los campos de un formulario de origen y genera formularios adaptables. Sin embargo, hay algunos campos y estilos en los PDF forms que son fácilmente visibles para el ojo humano pero difíciles de entender para el servicio. El servicio puede asignar tipos de campos o paneles diferentes de los aplicables a algunos campos o estilos. Todos estos patrones de estilo y campo se enumeran a continuación.

El servicio tiene el inicio de identificar y asignar los campos o paneles correctos a estos patrones, ya que sigue aprendiendo de los datos de origen. Por el momento, puede utilizar el editor [Revisar y corregir](review-correct-ui-edited.md) para corregir estos problemas. Antes de inicio de corregir los problemas o leer más, familiarícese con los componentes [de formulario](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)adaptables.

## General {#general}

<table border="1" cellpadding="1" cellspacing="0" style="border-collapse: separate; border-spacing: 0px;" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Patrones y resolución conocidos</td> 
   <td width="70%">Ejemplo</td> 
  </tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio no convierte los PDF forms rellenados en formularios adaptables.</p> <p> </p> <p><strong>Resolución</strong></p> <p>Utilice formularios adaptables vacíos.</p> </td> 
   <td style="text-align: left;"><img src="assets/pre-filled-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio puede no reconocer texto y campos de forma densa.</p> <p> </p> <p><strong>Resolución</strong></p> <p>Aumente la anchura entre el texto y los campos de un formulario denso antes de iniciar la conversión.</p> </td> 
   <td style="text-align: left;"><img src="assets/dense%20form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio no admite formularios digitalizados.</p> <p> </p> <p><strong>Resolución</strong></p> <p>No utilice formularios digitalizados. </p> </td> 
   <td><img src="assets/scanned-form.jpg" /></td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio no extrae imágenes ni texto dentro de las imágenes. </p> <p> </p> <p><strong>Resolución</strong></p> <p>Agregue manualmente imágenes o texto a los formularios convertidos.</p> </td> 
   <td><img src="assets/image-in-adaptive-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>No se convierten las tablas con límites y bordes punteados o no claros.</p> <p><strong>Resolución</strong></p> <p>Utilice tablas con bordes y límites explícitos claros. compatible.</p> </td> 
   <td><img src="assets/border-less-tables.png" /></td> 
  </tr>
 </tbody>
</table>

## Grupo de opciones  {#choice-group}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Patrón</td> 
   <td width="70%">Ejemplo</td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>Las opciones de grupo de opciones con formas distintas de cuadro o círculo no se convierten en los componentes de formulario adaptables correspondientes. </p> <p> </p> <p><strong>Resolución</strong></p> <p>Cambie las formas de opciones de opciones a cuadro o círculo o utilice el editor Revisar y corregir para identificar las formas.</p> </td> 
   <td><img src="assets/shaded-box-patterns.png" /> </td> 
  </tr>
 </tbody>
</table>

## Form fields {#form-fields}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Patrón</td> 
   <td width="70%">Ejemplo</td> 
  </tr>
  <tr>
   <td width="25%"><p><strong>Patrón</strong></p> <p>El servicio no identifica campos sin bordes claros.</p> <p> </p> <p><strong>Resolución</strong></p> <p>Utilice el editor Revisar y corregir para identificar estos campos.</p> <p> </p> <p> </p> </td> 
   <td width="50%"><br /> <img src="assets/fields-without-clear-borders.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio deja algunos campos de formulario con rótulos en la parte inferior o derecha sin identificar.</p> <p> </p> <p><strong>Resolución</strong></p> <p>Utilice el editor Revisar y corregir para identificar dichos campos</p> </td> 
   <td><br /> <img src="assets/forms-with-clear-borders-scale.png" /><br /> </td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio combina o asigna un tipo incorrecto a algunos campos de formulario que se sitúan muy cerca entre sí o que no tienen bordes claros. </p> <p> </p> <p><strong>Resolución</strong></p> <p>Utilice el editor Revisar y corregir para identificar estos campos.</p> </td> 
   <td><img src="assets/forms-with-fields-placed-nearby.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio puede no reconocer los campos con rótulos lejanos o una línea de puntos entre el rótulo y el campo de entrada.</p> <p> </p> <p><strong>Resolución</strong></p> <p>Utilice los campos de formulario con límites claros o utilice el editor Revisar y corregir para corregir estos problemas.</p> </td> 
   <td><img src="assets/form-fields-with-far-away-captions.png" /></td> 
  </tr>
 </tbody>
</table>

## Listas {#lists}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Patrón</td> 
   <td width="70%">Ejemplo</td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>Las listas que contienen campos de formulario se combinan o no se convierten en los componentes de formulario adaptables correspondientes</p> <p><strong>Resolución</strong></p> <p>Utilice los campos de formulario con límites claros o utilice el editor Revisar y corregir para corregir estos problemas.</p> </td> 
   <td><img src="assets/lists-with-fields.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio puede dejar algunas listas anidadas sin identificar</p> <p> </p> <p><strong>Resolución</strong></p> <p>Use el editor Revisar y corregir para corregir estos problemas.</p> </td> 
   <td><img src="assets/nested-lists.png" /> </td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio combina algunas listas que contienen grupos de opciones entre sí</p> <p><strong>Resolución</strong></p> <p>Use el editor Revisar y corregir para corregir estos problemas.</p> </td> 
   <td><img src="assets/lists-containing-choice-groups.png" /> </td> 
  </tr>
 </tbody>
</table>

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fiields without bordes are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->

