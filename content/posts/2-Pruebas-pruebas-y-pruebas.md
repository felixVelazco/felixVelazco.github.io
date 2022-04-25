---
title: "Pruebas, pruebas y más pruebas"
date: 2022-04-25
categories:
  - programming
tags:
  - unit testing
  - TDD
  - programming
  - essentials
  - jest
thumbnailImagePosition: left
thumbnailImage: https://programaenlinea.net/wp-content/uploads/2019/04/testing-1.jpg
---

Hola de nuevo! Alguna vez se han preguntado de qué manera se puede corroborar que tu código en verdad funcione como debería 😎?... No realmente?😅 
Pues aún así, este será tu día de suerte! 

<!--more-->

En el post de hoy veremos la importancia de crear pruebas unitarias cuando se trabaja con software.

Al momento de programar software en escuelas, muchas veces se olvidan de una de las partes más importantes en el mundo maravilloso del desarrollo de software, 
que son las pruebas del mismo, el cual nos da la garantía y ese "sello" de calidad en nuestros proyectos de que funcionan.

Para el tema de hoy, nos enfocaremos específicamente en algo llamado pruebas unitarias.

## Pero qué son las pruebas unitarias?

Las pruebas unitarias, básicamente nos ayudan a probar pequeñas partes del código, y con esto lograr saber si ciertas secciones funcionan como deberían.

La clave de estas pruebas unitarias, es la fragmentación del código en piezas simples, como si fueran figuras de legos, donde cada bloquecito debe de funcionar correctamente
para que todo el sistema esté en armonía, y para eso se prueba cada uno, para facilitar las cosas y ayudando a largo plazo a la escalabilidad de nuestros proyectos.

![Estructura de lego](https://c.tenor.com/eVXHLyK4c-kAAAAC/building-lego.gif)


Una vez sabiendo lo que son las pruebas unitarias, empecemos con la metodología TDD (de sus siglas en inglés, *Test-Driven Development*), básicamente consiste en crear 
el código principal en base a pruebas unitarias (o como a algunos les gusta llamarles, programación orientada a errores 😅), y se puede llevar a cabo en 3
sencillos pasos:

1. Crear una prueba la cual deberá fallar.
2. Después se debe de crear el código **mínimo** para que pase esa prueba.
3. Finalmente se mejora el código sabiendo que ya hay una prueba que lo respalda. 

![Ciclo TDD](https://marsner.com/wp-content/uploads/test-driven-development-TDD.png)


Y solo toma en cuenta, nunca confíes en una prueba que no has visto fallar, por lo que una vez que tengas en la prueba que todo está correcto, intenta mover 
las especificaciones para provocar que falle a propósito, y ver que no pasaste la prueba de pura "chiripa" 😂

Con esto termina una explicación breve (espero) de pruebas unitarias, a lo mejor en la siguiente vez puedo poner un ejemplo práctico utilizando *Javascript* y 
*Jest JS* para una prueba básica.