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

Entramos a nuestro nuevo proyecto con el comando `cd mi_primer_blog`, y con `ls` veremos todos los archivos que hay en la carpeta. Si accedemos a cada una de las carpetas, veremos que casi
todas se encuentran vacias.

### Obtener nuestro tema

El siguiente paso es, acceder al siguiente [link](https://themes.gohugo.io/) en donde encontraremos todos los temas que podemos instalar para nuestro blog. Yo en este caso, utilizaré 
el mismo que el de este blog, que es (tranquilpeak)[https://themes.gohugo.io/themes/hugo-tranquilpeak-theme/].

Nos movemos a la carpeta `themes`, y clonamos el repositorio de github

```console 
> git clone https://github.com/kakawait/hugo-tranquilpeak-theme.git
```

Ahora bien, este tema viene consigo con un ejemplo ya a la mano, y para facilitarnos la vida, 
utilizaremos esto para agilizar el proceso, así que copiamos los archivos en la carpeta `exampleSite`, y los pegamos en la raiz del proyecto, esto se puede hacer de manera manual, o con el siguiente comando:

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