---
title: "Please Mr Postman"
date: 2022-04-11T19:26:29-06:00
categories:
  - programming
tags:
  - Postman
  - Endpoints
  - API
thumbnailImagePosition: left
thumbnailImage: https://www.sngular.com/wp-content/uploads/2021/12/postman-logo-vert-2018.jpg
---

Estás creando una API y no sabes donde ver probar todos tus endpoints? O eres fanatico de la canción 
*Please Mister Postman* de *The Beatles*? Entonces estás en el lugar indicado!

<!--more-->
Para quienes ya hallan trabajado con anterioridad con una API, ya estarán familiarizados con el término de `endpoint`, pero 
si es la primera vez que escuchas todo esto, veamos una breve descripción.

La palabra API es un acrónimo del inglés, que se traduce como "Interfaz de programación de aplicaciones". Esto puede sonar muy complicado, 
pero las API tienen una función muy importante en el mundo de la programación, ya que es la parte que comunica entre el frontend y el backend.
Esto lo hace mediante peticiones y respuestas. 

Una analogía sencilla, es imaginarte que una aplicación web es un restaurante, el cliente se encuentra en la sala principal (frontend), y le pide
al mesero (API) un platillo (request), este mesero se comunica con los chefs en la cocina (backend), hacen el platillo que pidió, y el mesero lo 
lleva de vuelta al cliente. 

![Ratatoulli](https://i.gifer.com/J8lc.gif)

Los *endpoints* son las ubicaciones en donde deben de estar las *requests* que les haga el cliente, y estas se observan en los links. 
Tu puedes interactuar con estos *endpoints* de diversas maneras, y aquí es donde surgen los 4 métodos HTML:

1. GET: Obtiene los datos solicitados
2. POST: Crea nuevos datos
3. PUT: Modifica los datos especificados ya existentes
4. DELETE: Borra los datos especificados

Ya una vez que creas tu API, la quieres probar (pero no quieres utilizar *curl* con terminal), es ahí donde entra **Postman**.

![Homer Simpson Letters](https://pa1.narvii.com/6912/d4cfd5996bb99dbe274e1e3a2c1bbf4b5575fcacr1-480-368_hq.gif)

Postman es un programa con interfaz gráfica que nos permitirá realizar peticiones a una API, y facilitar el proceso de la misma, pero 
empecemos a ver su interfaz, como se ve a continuación.

![Interfaz de Postman](/images/6-mr-postman/Captura.JPG)

Para crear un nuevo *request*, le das en el botón de `new` en la parte superior izquierda, y le damos en `HTML Request`

![Interfaz de Postman](/images/6-mr-postman/Captura2.JPG)

Una vez creado, te debe de aparecer algo así:

![Interfaz de Postman](/images/6-mr-postman/Captura3.JPG)

Puedes cambiar el método HTML dándole click en donde dice `GET`, pero por el momento yo lo dejaré así para este ejercicio. 
Para este ejercicio, utilizaremos una API ya existente, para no tener que preocuparnos de crear una. Usaremos la 
[API de Pokemon](https://pokeapi.co/) y el link que copiaremos en Postman es el siguiente: `https://pokeapi.co/api/v2/pokemon`

{{< alert info>}}Si vas a hacer una petición con una API tuya, recuerda que debe de estar corriendo el servidor de la API.{{</alert>}}

Presionamos el botón azul que dice `send` y debemos de recibir una lista con varios pokemon.

![Interfaz de Postman](/images/6-mr-postman/Captura4.JPG)

En este caso, el código de status es `200`, por lo que no hubo ningún error, si no se hubiera encontrado la petición, hubieramos 
encontrado el famoso código 404. Aquí te dejo un [link](https://developer.mozilla.org/es/docs/Web/HTTP/Status) con los códigos. 


![Error 404](https://i0.wp.com/learn.onemonth.com/wp-content/uploads/2017/08/1-10.png?fit=845%2C503&ssl=1)

Puedes llegar incluso a documentar tus API desde postman, por lo que resulta muy conveniente de manejar. Y hasta aquí el post 
de hoy, espero que algo de esto les halla servido. **Hasta la próxima!**





