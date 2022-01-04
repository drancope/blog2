---
layout: post
title:  "Abordar la construcción de una estación meteorológica"
date:   2021-12-27 12:02:08 +0200
categories: 2ESO
tags: ["Estación Meteorológica", "Proyectos"]
author: drancope
---
Una estación meteorológica es un proyecto idóneo para hacer en el instituto: tiene un microcontrolador, que puede ser muy sencillo y barato.

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

## Cómo abordar este proyecto

Podemos pensar en un dispositivo que de manera independiente es capaz de tomar datos del ambiente exterior y mostrarlos en una pantalla, o bien que sea capaz de conectarse a Internet y guardar datos en algún servicio de alojamiento de datos. También podríamos diseñarlo para que fuera interactivo con los usuarios, a través de una página web, con lo cual entraríamos en el mundo del *Internet de las cosas*, e incluso podríamos crear algún tipo de análisis a partir de los datos guardados, y explorar el *machine learning*, y la *inteligencia artificial*.

El microcontrolador puede ser un arduino nano RP4020, o un dispositivo ESP8266, que pueden conectarse a la red para transmitir datos. El segundo es más barato y ligeramente más pequeño. Tiene, también, menos terminales de entrada/salida.

## Sensores

En todos los sistemas automáticos hay un microcontrolador, sensores y actuadores. Para la estación meteorológica, tenemos que determinar qué datos son los que queremos tomar. Lo más importante será la temperatura, pero también es útil tomar la presión atmosférica y la humedad. Podríamos incluir un sensor de luminosidad ambiental, para intentar utilizar estos datos en correlación con los otros.

### Temperatura y humedad

Para medir la temperatura y la humedad encontramos un doble sensor, el DHT11.

![sensor de temperatura y humedad](Imagenes/dht11.jpg)

Se conecta a una entrada digital, y ofrece los datos ya codificados. Basta con incluir la biblioteca de funciones disponible.

### presión

El sensor de presión atmosférica será el BMP180.

![sensor de presión](Imagenes/bmp180.jpeg)

Este sensor, como el BMP185, tienen también una biblioteca de funciones que ofrece las rutinas necesarias para tomar los datos de presión, desde 300 hasta 1100 hPa. Se alimenta con 3.3 Voltios.

## Actuadores

La salida de datos puede hacerse mediante terminal serie, o incorporando una pantalla LCD, o transmitiendo los datos a un servidor externo.

Intentaremos probar los tres métodos, sucesivamente, para estudiar cómo se programa cada uno de ellos.
