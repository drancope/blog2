---
layout: post
title:  "Empezar con Arduino"
date:   2022-01-04 21:59:58 +0200
categories: 4ESO
tags: ["Programación", "Microcontroladores"]
author: drancope
---
Este blog pretende dar una idea general de qué ramas y contenidos aparecen en nuestras asignaturas, y resumir las herramientas que podemos usar, no solo para realizar el trabajo de aprendizaje, sino para aprender acerca de ellas mimas.

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

## Index

- qué es
- cómo se conecta
- descargar programas y extensiones
- lenguaje: generalidades
- sintaxis

## Microcontroladores y Arduino

Un **microprocesador** es un circuito muy complejo, que realiza tareas de *computación* y podríamos decir que es el cerebro principal de un sistema completo, como un *ordenador*. La diferencia entre el *microprocesador* y el *ordenador* es que el primero solamente es el circuito, que generalmente va construido dentro de una pastilla de plástico, y el segundo tiene otros componentes que permiten que el microprocesador se conecte con el mundo exterior. Esto incluye *memorias RAM*, *discos duros*, *ratón*, *teclado*, *Internet*, *pantalla*, y montones de aparatos más.

Un **microcontrolador** es un circuito parecido al microprocesador, pero que está fabricado para conectarse con más facilidad a los dispositivos más sencillos del mundo exterior: *transistores, LEDs, botones, pantallas* simples o pequeños *servo-motores*.

<div style="margin-left: auto; margin-right: auto; width: 80%;">
    <table>
      <tr style="padding: 10px;">
        <td style="width: 50%;">
          <img style=" border-style: solid;height: 110%;" src="/assets/microprocesadores.jpeg">
        </td>
        <td>
          <img style=" border-style: solid;" src="/assets/microcontroladores.jpeg">
        </td>
      </tr>
      <tr>
        <td>
          Microprocesadores: Tienen una alta velocidad y capacidad de tratamiento de datos. Se usan en ordenadores.
        </td>
        <td>
          Microcontroladores: Son más pequeños, y tienen menor consumo eléctrico. Al tener menor capacidad de procesamiento, se usan en gran cantidad de aparatos que necesitan control automático.
        </td>
      </tr>
    </table>
</div>

Con frecuencia, los microcontroladores se montan sobre placas que amplian un poco lo que ellos pueden hacer. Por ejemplo, es común incorporar en la placa un conector **USB** para conectar el microcontrolador al ordenador. También suele añadirse un **LED** para que los usuarios lo programen.

<div style="margin-left: auto; margin-right: auto; width: 80%;">
    <table>
      <tr style="padding: 10px;">
        <td style="width: 50%;">
          <img style=" border-style: solid;height: 110%;" src="/assets/microbit.jpeg">
        </td>
        <td>
          <img style=" border-style: solid;" src="/assets/arduinouno.jpeg">
        </td>
      </tr>
      <tr>
        <td>
        La tarjeta <b>Micro:bit</b> monta un conjunto de 25 diodos y dos botones que pueden programarse. También lleva un micrófono, y un altavoz, un sensor de temperatura, y una brújula.
        </td>
        <td>
          <b>Arduino</b> es algo más sencillo, solo tiene el conector USB y un LED, pero trae unas piezas de plástico para insertar cables de nuevos circuitos, cosa que <b>Micro:bit</b> no tiene.
        </td>
      </tr>
    </table>
</div>

Otros modelos de tarjetas microcontroladoras son las que usan los *chips* **PIC**, las que usan el sistema de programación **mbed** con chips **Arm**.

Existen varios fabricantes de microcontroladores, y algunos de ellos fabrican varios tipos de ellos, con *arquitecturas* distintas. Podemos hablar de ***familias*** de microcontroladores, según el tipo de *arquitectura* con la que se han diseñado. Son ejemplos de ellos las familias *Cortex*, *Z8*, *PIC* o *COP*.

<div class="bloque">
<b>Ejercicio:</b> Muchas de las palabras que aparecen en este texto son nombres de distintas tecnologías o empresas que estamos revisando. Puedes elegir cinco o seis de estas palabras que no estás acostumbrado a manejar, y buscarlas en Internet. Te llevarán a distintas páginas, algunas más fáciles de leer, otras que simplemente venden productos, y otras te ofrecen <em>tutoriales</em> para montar proyectos. Leyendo varias de ellas te construiras un esquema mental de a qué se refiere cada una, de qué tipo de tecnología se trata, y para qué puede usarse. En tus próximas investigaciones, será frecuente tener que buscar muchos componentes o dispositivos para saber qué son.
</div>

### Hardware libre

**Arduino** se diseñó para ser copiado: la empresa que lo creó proporcionó una licencia de uso libre de su diseño. Así han conseguido que este modelo de tarjeta con microcontrolador sea el más usado y conocido del mundo. La mayoría de las tarjetas **Arduino** tienen un *microcontrolador* de la marca **Atmel**, aunque otras más modernas utilizan microcontroladores **Arm Cortex**.

Existen distintas tarjetas bajo la familia **Arduino**. La más corriente es el **Arduino UNO**. Otros modelos son el **mini**, el **Leonardo**, el **nano** o el **Mega**. Cada uno se diferencia de los demás en distintas cosas, como puede ser el modelo de microcontrolador, su memoria o su velocidad, o el tipo de conexión hacia el ordenador (podría incluso no tener ninguna), o la cantidad de terminales para conectar.

Como los fabricantes tienen derecho a copiar y modificar el diseño, para hacer el suyo propio, podemos encontrar modelos ligeramente distintos. Algunos tienen un chip de comunicaciones USB diferente, y otros tienen un microcontrolador distinto, de otro fabricante.

Para hacer funcionar estos modelos, hay que instalar a veces algún *driver* o alguna biblioteca de tarjetas distinta.

Las variedades más comunes, que podemos encontrar a precio muy económico en Intenet, son las que llevan la interfaz USB **ch340**, y la que tiene el chip de la familia **lgt8f**, fabricado por la compañía *Logic Green*.

<div style="margin-left: auto; margin-right: auto; width: 80%;">
    <table>
      <tr style="padding: 10px;">
        <td style="width: 50%;">
          <img style=" border-style: solid;height: 110%;" src="/assets/ch340.jpeg">
        </td>
        <td>
          <img style=" border-style: solid;" src="/assets/lgt8.jpeg">
        </td>
      </tr>
      <tr>
        <td>
        Esta tarjeta inspirada en el Arduino UNO tiene un microcontrolador de tamaño más pequeño que el original, aunque del mismo tipo. A la izquierda vemos señalado también el chip ch340. Para usarla, hay que instalar en el ordenador con el que programamos el driver adecuado:<br>
        <a href="https://www.geekfactory.mx/tutoriales-arduino/driver-ch340-para-arduino-chinos-o-genericos/">driver ch340</a>
        </td>
        <td>
          En esta "copia" del famoso UNO se utiliza el chip lgt8f328. El color rojo no quiere decir nada. Este microcontrolador tiene un conjunto de programas que se añaden a la instalación de Arduino del ordenador. Hay que descargar el paquete y descomprimirlo, y luego copiar las carpetas en nuestra carpeta de instalación:<br>
          <a href="https://drive.google.com/drive/folders/19K9qp-LhdUtl7kuAr4--0e4DROUmyaKc">drivers lgt8 de wagvat</a>
        </td>
      </tr>
    </table>
</div>

También encontramos los dispositivos **ESP8266**. Estas tarjetas tienen incluida la posibilidad de conectarse a una red *wifi* sin necesidad de módulos de expansión.

![Wemos ESP8266](/assets/wemos.png)

## Programas para programar

La [Interfaz de desarrollo Arduino](https://www.arduino.cc/en/software) está disponible para descarga en dos versiones. La versión *estable* es la 1.8, y tiene menos funcionalidades que la versión nueva 2.0. Esta última está en versión de prueba, pero ayuda a gestionar mejor la biblioteca de tarjetas y de programas de extensión.

Una vez que la hayamos descargado e instalado, nos creará una carpeta llamada *Arduino* en nuestra carpeta de usuario del ordenador. Allí podemos instalar las librerías de ampliación que descarguemos, y se guardarán nuestros programas.

![Ide Arduino](/assets/arduinoide.png)

Desde el menú "*herramientas*" podremos seleccionar la tarjeta que vamos a conectar, y el número de conector (*puerto*) en el que la enchufamos. Si tenemos un arduino UNO, basta con elegir esta tarjeta o "*board*", y elegir el puerto adecuado, que en Windows toma los nombres COM1, COM2, etc., y en Linux suele ser ttyUSB0, ttyUSB1, etc.

![Selección de puerto](/assets/puerto_arduino1.png)

Si elegimos el puerto equivocado, no podremos comunicarnos con la tarjeta. Afortunadamente, al lado del nombre correcto de puerto suele aparecer la placa que se ha detectado.

# Primer programa

En el menú *Archivo* tenemos un apartado de **ejemplos**. Probaremos en primer lugar el programa ***blink***, que simplemente hace parpadear el led de la tarjeta. Si no hay problemas de comunicaciones, el botón de la flecha hacia la derecha convertirá el programa desde *código fuente* a *programa objeto* y lo copiará a través del cable usb en la memoria *flash* del microcontrolador. El LED parpadeará.

Cambiando el número dentro de los paréntesis del *delay* (1000 corresponde a un segundo) por un número más bajo, por ejemplo 400, veremos que el ritmo del parpadeo cambia.

Todos estos pasos están descritos con detalles, fotografías, consejos y frecuentemente con videos explicativos en una infinidad de páginas web. Y a partir de aquí, encontraremos los siguientes tutoriales, para continuar avanzando en nuestro aprendizaje.
