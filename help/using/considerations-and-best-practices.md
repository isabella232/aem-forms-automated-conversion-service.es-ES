---
title: Prácticas recomendadas y consideraciones
description: NO PUBLICAR
seo-description: DO NOT PUBLISH
page-status-flag: never-activated
uuid: c2821264-39e2-44f8-b234-835c46f33fd5
topic-tags: introduction
discoiquuid: b786e40a-202e-4e17-a2f5-1f77c46538c2
privatebeta: true
index: false
source-git-commit: 298d6c0641d7b416edb5b2bcd5fec0232f01f4c7
workflow-type: ht
source-wordcount: '538'
ht-degree: 100%

---


# Prácticas recomendadas y consideraciones {#do-not-publish-best-practices-and-considerations}

<!--
[DO NOT PUBLISH]
-->

El servicio de conversión automatizada de AEM Forms tiene la capacidad de transformar un formulario PDF en uno que sea adaptable. Este usa inteligencia artificial y algoritmos de aprendizaje automático para comprender los diseños y campos del formulario de origen. Todos los servicios de aprendizaje automático se alimentan continuamente de los datos de origen y producen mejores resultados con cada operación. Al igual que las personas, estos servicios recopilan información de las experiencias.

El servicio de conversión automatizada de formularios se entrena con un amplio conjunto de formularios. Identifica fácilmente los campos de un formulario de origen y los transforma en adaptables. Sin embargo, hay algunos campos y estilos en los formularios PDF que son fácilmente visibles para las personas, pero difíciles de identificar para el servicio. El servicio puede asignar tipos de campos o paneles diferentes a los aplicables a algunos campos o estilos. A continuación, se enumeran todos estos patrones de estilos y campos.

Al comienzo, el servicio identifica y asigna los campos o paneles correctos a estos patrones, a medida que sigue aprendiendo de los datos de origen. Por el momento, puede usar el editor [Revisar y corregir](review-correct-ui-edited.md) para solucionar estos problemas. Antes de comenzar a corregir los problemas o seguir leyendo, familiarícese con los [componentes del formulario adaptable](https://helpx.adobe.com/es/experience-manager/6-5/forms/using/introduction-forms-authoring.html).

## General {#general}

<table border="1" cellpadding="1" cellspacing="0" style="border-collapse: separate; border-spacing: 0px;" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Patrones conocidos y resoluciones</td> 
   <td width="70%">Ejemplos</td> 
  </tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio no convierte los formularios PDF rellenados a formularios adaptables.</p> <p> </p> <p><strong>Resolución</strong></p> <p>Utilice formularios adaptables vacíos.</p> </td> 
   <td style="text-align: left;"><img src="assets/pre-filled-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio puede no reconocer el texto y los campos de un formulario con mucho contenido.</p> <p> </p> <p><strong>Resolución</strong></p> <p>Aumente la anchura entre el texto y los campos del formulario antes de iniciar la conversión.</p> </td> 
   <td style="text-align: left;"><img src="assets/dense%20form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio no admite formularios escaneados.</p> <p> </p> <p><strong>Resolución</strong></p> <p>No los utilice. </p> </td> 
   <td><img src="assets/scanned-form.jpg" /></td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio no extrae imágenes ni texto dentro de las imágenes. </p> <p> </p> <p><strong>Resolución</strong></p> <p>Agregue manualmente las imágenes o el texto a los formularios convertidos.</p> </td> 
   <td><img src="assets/image-in-adaptive-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>Las tablas con límites y bordes con puntos o que no estén bien delimitados no se pueden convertir.</p> <p><strong>Resolución</strong></p> <p>Utilice tablas con límites y bordes claros, explícitos y admitidos.</p> </td> 
   <td><img src="assets/border-less-tables.png" /></td> 
  </tr>
 </tbody>
</table>

## Grupo de elección  {#choice-group}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Patrón</td> 
   <td width="70%">Ejemplo</td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>Las opciones del grupo de elección con formas distintas de recuadros o círculos no se convierten en los componentes correspondientes al formulario adaptable. </p> <p> </p> <p><strong>Resolución</strong></p> <p>Cambie las formas de las opciones de elección a recuadros o círculos o utilice el editor Revisar y corregir para identificarlas.</p> </td> 
   <td><img src="assets/shaded-box-patterns.png" /> </td> 
  </tr>
 </tbody>
</table>

## Campos del formulario {#form-fields}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Patrón</td> 
   <td width="70%">Ejemplo</td> 
  </tr>
  <tr>
   <td width="25%"><p><strong>Patrón</strong></p> <p>El servicio no identifica los campos que no tengan bordes bien delimitados.</p> <p> </p> <p><strong>Resolución</strong></p> <p>Utilice el editor Revisar y corregir para identificarlos.</p> <p> </p> <p> </p> </td> 
   <td width="50%"><br /> <img src="assets/fields-without-clear-borders.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio no identifica algunos campos de formulario con subtítulos en la parte inferior o a la derecha.</p> <p> </p> <p><strong>Resolución</strong></p> <p>Utilice el editor Revisar y corregir para identificarlos.</p> </td> 
   <td><br /> <img src="assets/forms-with-clear-borders-scale.png" /><br /> </td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio combina o asigna un tipo incorrecto a algunos campos de formulario que están situados muy cerca unos de otros o que no tienen bordes bien definidos. </p> <p> </p> <p><strong>Resolución</strong></p> <p>Utilice el editor Revisar y corregir para identificarlos.</p> </td> 
   <td><img src="assets/forms-with-fields-placed-nearby.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio puede no reconocer los campos con subtítulos muy alejados o con una línea de puntos entre el subtítulo y el campo de entrada.</p> <p> </p> <p><strong>Resolución</strong></p> <p>Utilice campos de formulario con límites bien definidos o use el editor Revisar y corregir para solucionar estos problemas.</p> </td> 
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
   <td><p><strong>Patrón</strong></p> <p>Las listas que contienen campos de formulario se combinan o no se convierten en los componentes de formulario adaptable correspondientes.</p> <p><strong>Resolución</strong></p> <p>Utilice campos de formulario con límites bien definidos o use el editor Revisar y corregir para solucionar estos problemas.</p> </td> 
   <td><img src="assets/lists-with-fields.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio puede dejar sin identificar algunas listas anidadas.</p> <p> </p> <p><strong>Resolución</strong></p> <p>Utilice el editor Revisar y corregir para solucionar estos problemas.</p> </td> 
   <td><img src="assets/nested-lists.png" /> </td> 
  </tr>
  <tr>
   <td><p><strong>Patrón</strong></p> <p>El servicio combina algunas listas que contienen grupos de elección entre sí.</p> <p><strong>Resolución</strong></p> <p>Utilice el editor Revisar y corregir para solucionar estos problemas.</p> </td> 
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

