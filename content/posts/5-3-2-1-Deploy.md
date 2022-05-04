---
title: "3...2...1...Despliegue!"
date: 2022-05-04T00:32:37-06:00
categories:
  - programming
tags:
  - github
  - github pages
  - github actions
  - deploy
thumbnailImagePosition: left
thumbnailImage: https://i.ytimg.com/vi/2MsN8gpT6jY/maxresdefault.jpg
---

Llego el momento de subir nuestros blogs al internet, y que la gente nos lea, el despegue ha llegado y espero que estés listo!
<!--more-->
Si no has leido mi post anterior, donde les hablaba de como crear tu propio blog con *Hugo*, te dejo el link [aquí](https://felixvelazco.github.io/2022/04/crea-tu-propio-blog-con-hugo/). Con esto dicho, empecemos con el tutorial de hoy!

## Requisitos
- Tener [git](https://git-scm.com/download)
- Tener una cuenta [github](https://github.com/)

## Desplegar nuestro sitio

### Crear nuestro archivo yml

Debes de crear un archivo `.github/workflows/blog.yml`, puedes crear las carpetas y archivos de manera visual, o desde la terminal con los comandos (toma en cuenta que el comando se corre desde la carpeta raiz de tu blog)

```console
> mkdir .github & mkdir .github/workflows & touch .github/workflows/blog.yml
```

Abrimos este archivo y escribimos lo siguiente:

{{< codeblock "blog.yml" "yaml">}}name: Build Personal Blog
on: push

jobs:
  build:

    name: Build and update website
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
      with:
        submodules: true
        fetch-depth: 0
    - name: Setup GoHugo
      uses: peaceiris/actions-hugo@v2
      with:
        hugo-version: '0.92.0'
    - name: Commit Update
      run: |
        echo ":: Eliminando versión previa ::"
        rm -rf docs
    - name: Build drafts
      run: hugo -D
    - name: Commit Update
      run: |
        echo ":: Renombrando nueva version ::"
        mv public/ docs/
        git config --global user.email "launchx@innovaccion.mx"
        git config --global user.name "Launch X Backend Node JS"
        git add .
        git commit -m "GitHub Actions: Build ok"
    - name: Push changes
      uses: ad-m/github-push-action@master
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        branch: ${{ github.ref }}
{{< /codeblock >}}

Y con esto aplicamos un `git add .` y nuestro `git commit -m "Crear archivo .yml`.

{{< alert info>}}
Este archivo nos servirá para automatizar el proceso en nuestro Github actions, así no nos tendremos que preocupar por ciertas cuestiones después. Si quieres saber más sobre los github actions, te dejo
este [link](https://github.com/features/actions) para más información. 
{{< /alert>}}

### Configurar nuestro repositorio en *GitHub*

Sigamos con la creación y configuración de nuestra *GitHub pages*
{{< alert info >}}
Si ya has trabajado con *Github pages* anteriormente puedes saltearte este punto.
{{< /alert >}}
Para ello, debemos de crear un nuevo repositorio, le damos en la opción de crear, y nos aparecerá una ventana como esta.

![Crear nuevo repositorio](/images/5-3-2-1-deploy/git1.JPG)

El nombre de tu repo debe de ser `<username>.github.io` donde sustituyes el *\<username\>* por tu nombre de usuario en github. Quedando algo como esto

{{< alert warning >}}
Este paso es muy importante para la creación de una página en github.
{{< /alert >}}

![Nombre de tu repositorio](/images/5-3-2-1-deploy/git2.JPG)

En este caso a mi me marca rojo debido a que ya existe este repositorio en mi cuenta, pero a ustedes les debe de aparecer en verde. Una vez hecho esto, le dan simplemente en `Crear repositorio`. 
Les mostrará la siguiente ventana.

![Nombre de tu repositorio](/images/5-3-2-1-deploy/git3.JPG)

### Subir nuestro repo a github

Como nosotros ya tenemos nuestro repositorio local en la computadora, vamos a irnos por la segunda opción, copian las líneas que vienen ahí y las pegan en una terminal que esté en la carpeta raíz de tu
blog. Al actualizar la página de github veremos que ya están cargados nuestros archivos.

Nos iremos a la pestaña `settings`, y seleccionamos la opción `pages`, en donde modificaremos la rama a `main` y seleccionamos `/docs`. También en este punto estará la url de nuestro blog, el cual entraremos más tarde.

![Nombre de tu repositorio](/images/5-3-2-1-deploy/git4.JPG)

Nos vamos a la pestaña de `Actions`, y aquí nos encontraremos el estado de nuestro sitio web. Al momento de estar corriendo, estará en color amarillo, de ahí pasará a estar de color verde o rojo, dependiendo si 
todo está bien o no respectivamente. 

![Github actions](/images/5-3-2-1-deploy/git5.JPG)

Si algo sale mal en el proceso, puedes darle click a la acción, y te dirá el error que encontró, pero si todo está bien, ya podrás acceder a tu blog con la url que obtuviste anteriormente.

Finalmente, cada vez que quieras agregar un nuevo post desde tu computadora, hasta github, deberás crear tus commits necesarios con git, y una vez que tengas todo listo, corres el siguiente comando. 

```console
> git push
```

Muy probablemente, te marcará un error, debido a que nuestra `action` en el archivo `blog.yml` ejecutó ciertos comandos que modificaron el repositorio remoto con respecto al local. Para solucionar esto solo 
corre el comando `git pull` y vuelve a correr `git push`, y **listo**.

Con esto termina el post de hoy, espero les sirva la información de hoy y nos vemos pronto.

## Referencias
- [Crear un sitio con github pages](https://docs.github.com/es/pages/getting-started-with-github-pages/creating-a-github-pages-site)
- [Github actions](https://github.com/features/actions)
- [Git](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Acerca-del-Control-de-Versiones)
- [Hugo](https://gohugo.io/)
