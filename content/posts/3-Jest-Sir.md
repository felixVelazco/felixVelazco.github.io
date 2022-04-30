---
title: "Jest Sir!"
date: 2022-04-28T02:18:48-06:00
categories:
  - programming
tags:
  - jest
  - javascript
  - unit testing
  - test
  - TDD
thumbnailImagePosition: left
thumbnailImage: https://jestjs.io/es-ES/img/opengraph.png
---

Hola a todos los que lean esto! En el blog anterior les hable de manera general sobre la definición y la utilidad de las muestras unitarias en la creación de 
software, ahora toca ver la versión práctica del código, así que vamos a darle!

<!--more-->

![Yes sir meme](https://c.tenor.com/oVl_61sA4eMAAAAC/yes-sir.gif)

## Requisitos
- Javascript
- npm
- Node JS
- Jest

## Requerimientos de la aplicación
Para este ejercicio, debemos de crear una clase `Mascota`, la cual al instanciar un objeto, tendrá los atributos `name`, `age`, `race`, `canSwim`, `favoriteFoods`.

## Pasos
#### Crear la carpeta de tu proyecto 
Para este proyecto crearé una carpeta llamada `Mascota` donde estará la raiz de nuestro proyecto

#### Crear nuestro `package.json`
En la raiz de nuestro proyecto, abriremos una terminal, donde ejecutaremos el siguiente comando:

```console
> npm init
```

Te aparecerán después varias preguntas que puedes responder u omitir simplemente presionando <kbd>Enter</kbd> en cada una, y listo!

Si abrimos nuestro archivo package.json, veremos algo como esto:

{{< codeblock "package.json" "json">}}
{
  "name": "mascota",
  "version": "1.0.0",
  "description": "\"Clase para crear una mascota\"",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "felix velazco",
  "license": "ISC"
}
{{< /codeblock>}}

#### Agregar *Jest* a nuestro *package.json*
Para eso ejecutaremos el comando:

```console
> npm install --save-dev jest
```
Este comando lo que hace es descargar la carpeta `node_modules` en nuestro proyecto, y especifica que el `node_module` jest será utilizado como 
devDependencies (es decir, son dependencias que sirven solo cuando el proyecto está en desarrollo, pero no para el producto final, como lo son las 
pruebas unitarias)

Y si nos metemos nuevamente a nuestro archivo `package.json` vemos que este a sido modificado, agregando nuestras `devDependencies`.

{{< codeblock "package.json" "json">}}
{
  "name": "mascota",
  "version": "1.0.0",
  "description": "\"Clase para crear una mascota\"",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "felix velazco",
  "license": "ISC",
  "devDependencies": {
    "jest": "^27.5.1"
  }
}
{{< /codeblock >}}

Ya por último, modificamos la línea de `"test": "echo \"Error: no test specified\" && exit 1"` por `"test": "node ./node_modules/jest/bin/jest"`

{{< alert info>}} 
Esta sintaxis solo aplica para windows, para sistemas Linux/Unix usar `"test": "node ./node_modules/.bin/jest"`
{{ /alert}}

Y así nuestro `package.json` quedó listo

#### Creación de nuestras carpetas y archivos
Pasamos a crear dos carpetas llamadas `app` y `test`. En la primer carpeta crearemos un archivo llamado `mascota.js`, mientras que en
la segunda un archivo `mascota.test.js`. Debe de quedar una distribución similar a la siguiente:

![Directorio con todos los archivos](https://user-images.githubusercontent.com/79220309/164637006-56f750f7-d55d-4482-b2ab-d78a3a93de68.png)

#### Aplicar el TDD
En el post anterior había mencionado que el TDD es una técnica que ayuda a crear código en base a pruebas, y que consta de 3 pasos.

##### 1. Hacer una prueba que falle

Abrimos el archivo `mascota.test.js` y creamos el siguiente código

{{< codeblock "mascota.test.js" "js">}}
//Con esto importamos la clase mascota
const Mascota = require("./../app/mascota");

//Crea una suite donde estarán todas tus pruebas
describe('Unit test suite para Clase Mascota',() =>{
//Aqui se pone la primera prueba, que consiste en crear un objeto de la clase mascota
  test('1) Crear un objeto', () => {
    //Se crea el objeto con los atributos que queramos
    const perro = new Mascota('doggy', 2, 'shiba', ['croquetas', 'sobres', 'platano']);

    //en expect ponemos la variable que queremos analizar
    //toBe nos dice que a lo que tiene que ser igual (existen mas funciones ademas de toBe)
    expect(perro.name).toBe("doggy");
    
    //toBeGreaterThan nos dice si un numero es mayor que 2
    expect(perro.age).toBeGreaterThan(2);
    
    expect(perro.race).toBe("shiba");
    
    //not nos dice que la condicion que le sigue no debe de ser verdad
    //toBeUndefined nos dice si la variable es indefinida
    expect(perro.canSwim).not.toBeUndefined();
    
    //toContain sirve para saber si un elemento existe en un array
    expect(perro.favoriteFood).toContain("croquetas");
  })
})
{{< /codeblock>}}
Guardamos cambios, nos vamos a nuestra consola y corremos la prueba

```console
> npm test mascota.test.js

- mascota@1.0.0 test
- node ./node_modules/jest/bin/jest "test/mascota.test.js"

 FAIL  test/mascota.test.js
  Unit test suite para Clase Mascota
    × 1) Crear un objeto (1 ms)

  ● Unit test suite para Clase Mascota › 1) Crear un objeto

    TypeError: Mascota is not a constructor

       7 |   test('1) Crear un objeto', () => {
       8 |     //Se crea el objeto con los atributos que queramos
    >  9 |     const perro = new Mascota('doggy', 2, 'shiba', false, ['croquetas', 'sobres', 'platano']);
         |                   ^
      10 |
      11 |     //en expect ponemos la variable que queremos analizar
      12 |     //toBe nos dice que a lo que tiene que ser igual (existen mas funciones ademas de toBe)

      at Object.<anonymous> (test/mascota.test.js:9:19)

Test Suites: 1 failed, 1 total
Tests:       1 failed, 1 total
Snapshots:   0 total
Time:        0.696 s, estimated 1 s
Ran all test suites matching /test\\mascota.test.js/i.
```
La prueba tronó debido a que mascota no es un constructor, debido a que aún no tenemos nada de código hecho. Ahora debemos crear el código mínimo para que lo pase.

##### 2. Hacer que el test pase

Abrimos el archivo `mascota.js` y escribimos lo siguiente.

{{< codeblock "mascota.js" "js">}}
//Creamos la clase Mascota
class Mascota{
  //Creamos un constructor para instanciar el objeto
  constructor(name, age, race, favoriteFood){

  }
}
//Exportamos nuestro modulo mascota para usarlo en otros archivos
module.exports = Mascota;
{{< /codeblock >}}
Corremos de nuevo nuestra prueba:

```terminal
felix@bar:mascota/test$ npm test mascota.test.js
  Unit test suite para Clase Mascota
    × 1) Crear un objeto (7 ms)

  ● Unit test suite para Clase Mascota › 1) Crear un objeto

    expect(received).toBe(expected) // Object.is equality

    Expected: "doggy"
    Received: undefined

      11 |     //en expect ponemos la variable que queremos analizar
      12 |     //toBe nos dice que a lo que tiene que ser igual (existen mas funciones ademas de toBe)
    > 13 |     expect(perro.name).toBe("doggy");
         |                        ^
      14 |     //toBeGreaterThan nos dice si un numero es mayor que 2
      15 |     expect(perro.age).toBeGreaterThan(2);
      16 |     expect(perro.race).toBe("");

      at Object.<anonymous> (test/mascota.test.js:13:24)

Test Suites: 1 failed, 1 total
Tests:       1 failed, 1 total
Snapshots:   0 total
Time:        0.784 s, estimated 1 s
Ran all test suites matching /test\\mascota.test.js/i.
```

Obtenemos un error nuevo, el cual nos dice que esperaba recibir el valor `"doggy"`, pero recibió `undefined`, ya que solo creamos la clase y el constructor vacío. Añadimos unas pocas líneas de 
código

{{< codeblock "mascota.js" "js">}}
//Creamos la clase Mascota
class Mascota{
  //Creamos un constructor para instanciar el objeto
  constructor(name, age, race, favoriteFood){
    //Con el this.foo podemos guardar los parametos a nuestro objeto
    this.name = name;
    this.age = age;
    this.race = race;
    this.canSwim = true;
    this.favoriteFood = favoriteFood;
  }
}

//Exportamos nuestro modulo mascota para usarlo en otros archivos
module.exports = Mascota;
{{< /codeblock >}}

Corremos una vez más nuestra prueba: 

```terminal
felix@bar:mascota/test$ npm test test/mascota.test.js 

> mascota@1.0.0 test
> node ./node_modules/jest/bin/jest "test/mascota.test.js"

 PASS  test/mascota.test.js
  Unit test suite para Clase Mascota
    √ 1) Crear un objeto (5 ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        0.693 s, estimated 1 s
Ran all test suites matching /test\\mascota.test.js/i.
```
Listo! Nuestro programa y prueba están listos! Ahora hay que hacerla tronar la prueba 
moviendo los valores después del `.toBe()` o equivalentes, pero eso se los dejo a ustedes.

##### 3. Mejorar el código
Este paso, para códigos más complejos, nos ayuda a mejorar el código ya hecho, y como ya hay una prueba que te sirve de guia, por lo que si haces las cosas mal, te equivocas al pasar una variable, o cualquier cosa, al correr tus pruebas te va a decir en que te equivocaste. 

Por el día de hoy es todo, espero y esto les llegue a servir, las pruebas al principio pueden parecer innecesarias o redundantes, pero su importancia es muy grande si quieres llegar a ser proyectos más profesionales y con sello de calidad.


# Bibliografía relevante
- [Documentación de Jest JS](https://jestjs.io/docs/using-matchers)


