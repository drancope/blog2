---
layout: post
title:  "Escribir un post"
date:   2021-10-26 12:31:58 +0200
categories: 3ESO
author: drancope
---
En este artículo intentaré dar indicaciones para hacer cada uno de los artículos de un blog Jekyll.

<div class="post-categories">
 Categorías: {% if post %}
   {% assign categories = post.categories %}
 {% else %}
   {% assign categories = page.categories %}
 {% endif %}
 {% for category in categories %}
 <a href="{{site.baseurl}}/categories/#{{category|slugize}}">{{category}}</a>
 {% unless forloop.last %}&nbsp;{% endunless %}
 {% endfor %}
</div>
<br>
## Dónde están los artículos.

En el repositorio hay una carpeta llamada **_posts**. En ella hay un archivo por cada artículo. El nombre del artículo debe tener la fecha y el título del artículo. En formato año-mes-día. Es decir, que un archivo puede llamarse "2021-09-15-Noticias-importantes.markdown". Después, el nombre termina con un punto y la palabra *markdown*.

El documento contiene dos partes: una al inicio, que empieza y termina con tres guiones ---, y otra con el texto. En la primera parte, hay que poner el estilo de página (lo normal es *default*, aunque alguna plantilla de temas admite también *post*), el título, la fecha y el autor. De la siguiente manera:

{%highlight markdown%}
---
layout: post
title:  "Escribir un post"
date:   2021-10-26 12:31:58 +0200
categories: Novedades
author: drancope
---
{%endhighlight%}

La segunda parte es el contenido del artículo. Utiliza lenguaje markdown. Así que podemos usar * para dar énfasis (itálicas) , doble * para negritas, y # para los encabezados. Recomiendo usar a partir del encabezado de segundo nivel (##), ya que el de primer nivel se usa para el título del artículo.

Se puede incluir código html dentro del artículo, aunque puede que estorbe un poco.

Las imágenes, emoticones, listas y enlaces funcionan también con normalidad, siguiendo los manuales del lenguaje markdown.

Lo más complicado es integrar los estilos y filtros dentro de todo este sistema. Por ejemplo, con lenguaje css (o más bien sass) podemos modificar el aspecto general de nuestra web, o bien definir estilos de párrafo especiales que usaremos según queramos dar a un párrafo aspedto distinto. Los filtros utilizan llaves {} o llaves con porcentaje %, dentro de las cuales se incluyen variables o instrucciones especiales. Una de ellas, el resaltador de código, se utiliza en el cuadro de arriba.

<div class="bloque">
La generación de un cuadro como éste requiere crear un código de estilo, que guardamos en un archivo dentro de la carpeta _sass y escribir una llamada a ese archivo dentro de otro que se carga automáticamente en la cabecera de la página web.
</div>
Esto sería todo por hoy.
