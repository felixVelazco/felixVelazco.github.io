---
title: "Git o Github? esa es la cuestión"
date: 2022-04-24
categories:
  - programming
tags:
  - git
  - github
  - differences
thumbnailImagePosition: left
thumbnailImage: https://cdn-icons-png.flaticon.com/512/25/25231.png
---


Cuantas veces hemos escuchado hablar sobre *Github* y *Git* son la misma cosa? 
Y pues, si bien, están relacionadas entre si, no son lo mismo, y hoy veremos esas diferencias, **Let's GO!**
<!--more-->


# Control de versiones
Empecemos por el principio, un control de versiones es una maravillosa herramienta que nos permite tener un registro de todas las modificaciones en un proyecto,
y si en algún paso la regamos y todo el sistema se colapsa, podemos regresar a un estado anterior en donde todo funcionaba de maravilla. Son el equivalente 
a la saga de películas *"Volver al futuro"*, donde Marty McFly viaja al pasado, modifica algo y su vida cambia, pues es más o menos lo mismo. 

![Back to the future](https://giffiles.alphacoders.com/144/144132.gif)

Y no podemos mencionar control de versiones sin mencionar al único e inigualable *git*. Git se encarga de gestionar todas las versiones de tus repositorios (lugar donde
se almacena tus proyectos) de manera local, por lo que no se necesita de una conexión a internet para su funcionamiento. 

![Git logo](https://user-images.githubusercontent.com/79220309/165035210-eea1645a-82af-4953-aedf-c2f8ed2eee27.png)

# Alojamiento de repositorios

Ahora imaginemos que nosotros queremos tener en un lugar guardado nuestros proyectos, y tenerlos de manera local no siempre es lo más ideal, ya que si la compu se te 
descompone, tu proyecto se puede quedar en el olvido. O también si necesitas trabajar en diferentes computadoras por *x* o *y* o trabajar en equipo en un solo 
repositorio. Ahí es donde surge nuestro amigo Github.

Esta plataforma está basada en Git (de ahí su nombre Github) el cual es un servicio en la nube que permite tener tus repositorios en línea, en la cual tu decides 
si son privados o cualquier persona puede acceder a ellos, y además, permite que varias personas contribuyan en algún repositorio, creando una bonita 
comunidad de programadores que pueden contribuir en diversos proyectos. 

![Github logo](https://user-images.githubusercontent.com/79220309/165035355-12fd9e55-e918-42b3-8d05-11dec39a0c6b.png)

De hecho, mi primer acercamiento con Github, simplemente fue clonar un repositorio para utilizar unas librerias de robótica (Si mal no me equivoco era el repo de 
*player/stage* para una clase, pero nunca imaginé la utilidad y complejidad real hasta años después que ya tuve que trabajar en verdad con los repos, y no solo
copiar la famosa linea de `git clone ...` 

# Diferencias principales
|  | **Git** | **Github** |
|-- |--|--|
| **Función principal** | Control de versiones | Gestor de repositorios online |
| **Interfaz** | Comandos desde terminal | Interfaz gráfica agradable |
| **Trabajo en equipo** | No (se necesita github o gitlab) | Si |


# Conclusiones

Esto solo fue una explicación breve de lo que nos permiten estas herramientas y sus diferencias. En otro post me gustaría ir un poco más profundo en como usarlas
sus comandos básicos, y otras cosas más, pero por el día de hoy es todo! Nos vemos en el siguiente post!
