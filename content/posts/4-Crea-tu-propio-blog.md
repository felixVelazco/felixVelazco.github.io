---
title: "Crea tu propio blog con Hugo!"
date: 2022-04-29T00:01:13-06:00
categories:
  - programming
tags:
  - github
  - github pages
  - programming
  - tranquilpeak
thumbnailImagePosition: left
thumbnailImage: https://www.uxlift.org/assets/images/iu.png
---
No les puedo hablar sobre temas de programación en mi blog sin mencionarles antes el como es que cree mi blog, y justo es lo que veremos el día de hoy, y lo haremos posible con nuestro amigo **HUGO**.
<!--more-->
Empecemos con lo primero, ¿Quién es *Hugo*, y por qué lo necesitamos para crear un blog? Bueno, se los presento:

![Hackerman meme](https://i.ytimg.com/vi/KEkrWRHCDQU/maxresdefault.jpg)

Ya dejándonos de broma, [**HUGO**](https://gohugo.io/?ref=uxlift.org) es un *framework* para crear sitios web estáticos, el cual nos permite crear sitios de manera muy sencilla y con bastantes opciones de temas de personalización. Y si ningún tema te convence, puedes crear el tuyo propio (aunque esto requerirá de mayor trabajo).

Y hoy seré su guia para instalar, desarrollar y probar sus blogs. Así que empecemos!

## Requisitos
- Tener instalado [chocolatey](https://chocolatey.org/install)
- Tener [git](https://git-scm.com/download)
- Tener ciertos conocimientos básicos de programación (opcional)

## Instalación
Una vez que tengas instalado chocolatey, debes de correr este comando en tu terminal
```console
> choco install hugo -confirm
```
O si necesitas de la versión extendida "Sass/SCSS":
```console
> choco install hugo-extended -confirm
```
Con esto, corremos simplemente corremos el siguiente código, y nos debe de dar la versión que tienes instalado.

```console
> hugo version
hugo v0.96.0-2fd4a7d3d6845e75f8b8ae3a2a7bd91438967bbb+extended windows/amd64 BuildDate=2022-03-26T09:15:58Z VendorInfo=gohugoio
```

## Creando mi primer blog
Una vez que ya tienes instalado *Hugo*, lo primero es crear nuestro proyecto, esto lo haremos con ayuda de nuestra terminal. Buscamos el directorio donde queremos que se localice el blog, 
y corremos el siguiente comando:

```console
> hugo new site mi_primer_blog

Congratulations! Your new Hugo site is created in C:\directory\mi_primer_blog.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>\<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
```

Entramos a nuestro nuevo proyecto con el comando `cd mi_primer_blog`, y con `ls` veremos todos los archivos que hay en la carpeta. Si accedemos a cada una de las carpetas, veremos que casi todas se encuentran vacias.

Aquí es un buen momento para iniciar nuestro repositorio en *git*, esto se hace con el comando 

```console
> git init
```

De aquí en adelante, cada vez que hagamos un cambio sustancial, podemos correr los siguientes comandos

```console
> git add nombreArchivoModificado
> git commit -m "Agregar descripcion de la modificacion"
```

Otro comando importante sería `git status`, el cual te ayudará a ver cuales son los archivos que se han modificado.

Si bien, esto es de manera general, de momento esto sería lo más importante para continuar con el blog y tenerlo actualizado, si están interesados en saber más comandos de git, puedo hacer un post más adelante. 

### Obtener nuestro tema

El siguiente paso es, acceder al siguiente [link](https://themes.gohugo.io/) en donde encontraremos todos los temas que podemos instalar para nuestro blog. Yo en este caso, utilizaré [tranquilpeak](https://themes.gohugo.io/themes/hugo-tranquilpeak-theme/).

Nos movemos a la carpeta `themes`, y clonamos el repositorio de github

```console 
> git clone https://github.com/kakawait/hugo-tranquilpeak-theme.git
```

Ahora bien, este tema viene consigo con un ejemplo ya a la mano, y para facilitarnos la vida, 
utilizaremos esto para agilizar el proceso, así que copiamos los archivos en la carpeta `themes/nombre-del-tema/exampleSite`, y los pegamos en la raiz del proyecto, esto se puede hacer de manera manual, o con el siguiente comando:

{{< alert warning >}} Debes de estar en la carpeta raiz al ejecutarlo.{{< /alert >}}

```console
> cp -a themes/hugo-tranquilpeak-theme/exampleSite/. ./
```

### Configurando nuestro *config.toml*

En el archivo *config.toml* es donde encontraremos todas las configuraciones que debemos de ajustar la primera vez que hacemos nuestro blog, aquí irán tus datos personales y contacto, el link de tu página web y el nombre, las palabras claves que se utilizan dentro del blog, entre muchas cosas más.

{{< alert info >}}
Este archivo puede variar en sus requisitos dependiendo del tema que estés usando, por lo que te recomiendo que siempre intentes ver un ejemplo de este con el tema que quieras usar. Aquí dejo el link de la documentación para [tranquilpeak](https://github.com/kakawait/hugo-tranquilpeak-theme/blob/master/docs/user.md). 
{{< /alert >}}

### Creando nuestro primer post

De la misma manera, cada tema tiene sus funciones adicionales para crear cada post, por lo que puedes acceder a ver en tu carpeta `content/posts` y ver los códigos de ejemplo que tienes, pero la manera general de crear uno es con la siguiente línea de comando.

```console
> hugo new posts/nombre_de_tu_post.md
```

Este comando lo que hace, es tomar crear un nuevo `archivo.md`, tomando el arquetipo `posts`. Un arquetipo es como una plantilla para crear tus posts de manera más rápida. El arquetipo por default te crea un archivo con el siguiente formato

{{< codeblock "nombre-de-tu-post.md" "md">}}
---
title: "nombre-de-tu-post"
date: 2022-04-29T16:10:37-06:00
draft: true
---
{{< /codeblock >}}

De la misma manera, podemos nosotros crear nuestros propios arquetipos, y utilizarlo para facilitar la creación de nuevos posts. Imáginemos que creamos el arquetipo `biografia` en la carpeta `archetypes`, y queremos crear un post con este formato, usamos el comando:

```console
> hugo new biografia/nombre_de_tu_post.md
```

Si es el primer post que haces, este te creará una carpeta `biografia` dentro de la carpeta `content`. Si en dado caso quieres guardar esos blogs en otra carpeta (por ejemplo, en `posts`), solo tienes que hacer los siguiente:

```console
> hugo new -k biografia posts/nombre_de_tu_post.md
```

{{< alert info >}}Si no existe el arquetipo con el que le intentas crear tu post, automáticamente te creará el archivo con el arquetipo `default`. {{< /alert >}}

{{< codeblock "nombre-post.md" "md">}}
---
title: "Nuevo post"
date: 2022-04-29T16:10:37-06:00
categories:
- Tecnología
tags:
- Ejemplo
- Tranquilpeak
thumbnailImagePosition: left
thumbnailImage: https://img.freepik.com/vector-gratis/colorida-bienvenida-dibujada-mano-pagina-inicio_23-2148274061.jpg?w=2000_
---

Todo lo que muestres antes del `<!-- more-->`, se mostrará como una 
*preview* del contenido 
<!--more-->

# Blog

Aquí va todo el contenido del mismo, puedes insertar imágenes, código, alertas,
entre otras cosas, verifica el ejemplo o la documentación oficial para 
ver más detalles.
{{< /codeblock>}}

Con esto hecho, es hora de ver como se ve nuestro blog

### Servidor local
Para poder visualizar nuestro blog de manera local (es decir, solo en tu computadora), corremos el comando de:

```console
> hugo server
```
Este iniciará un servidor en el link `http://localhost:1313/`
{{< alert info >}} 
El puerto `1313` es el puerto por default para Hugo, aunque si intentas abrir más blogs al mismo tiempo, entonces este puede cambiar, por lo que se aconseja siempre revisar el puerto que le indica la terminal al correr el comando anterior.
{{< /alert >}} 

Entramos al link, y nos encontramos con la página principal, y su interfaz, veremos todos los posts de ejemplos y entre ellos el que acabamos de crear.
Después de esto ya puedes borrar esos posts y empezar a crear los tuyos. 

![Hugo Blog](/images/3-mi-primer-blog-con-hugo/hugo-blog.gif)

Y con esto terminamos por el día de hoy, espero que esta información les sirva, y motive a crear sus propios blogs. De momento esto aún está de manera local, y ya en el siguiente post les mostraré como pueden subir su blog con [Github pages](https://pages.github.com/). 



