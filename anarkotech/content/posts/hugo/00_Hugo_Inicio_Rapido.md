+++
title = "00 Hugo Inicio Rápido"
date = "2021-09-10T19:30:46+02:00"
author = "Anarkotech"
authorTwitter = "" #do not include @
cover = ""
tags = ["Hugo"]
keywords = ["", ""]
description = "Manual de Inicio Rápido con Hugo"
showFullContent = false
+++

Esta guía pretende explicar de manera sencillas los primeros pasos que hay que realizar para poder hacer un sitio web con **HUGO**.

Estamos trabajando con un PC con Sistema Operativo **Arch Linux** y con la consola de comandos. Para el uso de otros Sistemas Operativos algunos de los puntos descritos en este manual pueden no ser válidos.

## 1. INSTALAR HUGO

Para instalar **HUGO** en Arch Linux debemos poner el siguiente comando en la consola:

```bash
sudo pacman -S hugo
```

Para verificar que versión tenemos y ver si se ha instalado correctamente  ponemos desde la terinal:

```bash
hugo version
```

## 2. CREACIÓN DE UN NUEVO SITIO WEB

Hugo permite crear toda la estructura de archivos y directorios de tu web en el directorio en el que nos encontremos, usando un solo comando:

```bash
hugo new site [Nombre_de_la_web]
```
Esto crea un directorio con el nombre de la web y dentro de el toda la estructura de directorios y archivos necesarios para la web.

## 2.1 ESTRUCTURA DE DIRECTORIOS

	archetypes/		-->	definir datos sobre el contenido
	content/		-->	aquí se guarda el contenido de la web
	data/			-->	para los datos de la web
	layouts/		-->
	static/			-->	archivos estáticos generados para subir al servidor
	themes/			-->	temas de la web
	config.toml		-->	archivo de configuración de la web

## 3. AGREGAR UN TEMA A LA WEB

En nuestro caso vamos a trabajar con el tema **Terminal**. Pero podemos elegir cualquiera de los temas que hay en la web:

	https://themes.gohugo.io/

Nuestro tema **Terminal** tiene el siguiente enlace:

	https://themes.gohugo.io/themes/hugo-theme-terminal/

Para la instalación del tema tenemos dos opciones:

- Clonarlo directamente desde git a nuestro directorio de Hugo, debemos estar en el directorio raíz de nuestra web:

```bash
git clone https://github.com/panr/hugo-theme-terminal.git themes/terminal
```
- También podemos incluirlo como un submódulo de git para permitir actualizaciones cundo estén disponibles:
```bash
git submodule add https://github.com/panr/hugo-theme-terminal.git themes/terminal
```

Con esto creamos un directorio **terminal** dentro del directorio `./themes/` de la raíz de nuestra web . Este directorio contiene todas las carpetas y archivos necesarios para que funcione nuestro tema. 

## 4. CONFIGURACIÓN DEL TEMA "TERMINAL"

Para configurar el tema **terminal** solo debemos copiar el siguiente código en el archivo **config.toml** del directorio raiz de nuestra web y cambiar cualquier parámetro que queramos.

```bash
baseurl = "/"
languageCode = "en-us"
theme = "terminal"
paginate = 5

[params]
  # dir name of your main content (default is `content/posts`).
  # the list of set content will show up on your index page (baseurl).
  contentTypeName = "posts"

  # ["orange", "blue", "red", "green", "pink"]
  themeColor = "orange"

  # if you set this to 0, only submenu trigger will be visible
  showMenuItems = 2

  # show selector to switch language
  showLanguageSelector = false

  # set theme to full screen width
  fullWidthTheme = false

  # center theme with default width
  centerTheme = false

  # set a custom favicon (default is a `themeColor` square)
  # favicon = "favicon.ico"

  # set post to show the last updated
  # If you use git, you can set `enableGitInfo` to `true` and then post will automatically get the last updated
  showLastUpdated = false
  # Provide a string as a prefix for the last update date. By default, it looks like this: 2020-xx-xx [Updated: 2020-xx-xx] :: Author
  # updatedDatePrefix = "Updated"

  # set all headings to their default size (depending on browser settings)
  # it's set to `true` by default
  # oneHeadingSize = false

[params.twitter]
  # set Twitter handles for Twitter cards
  # see https://developer.twitter.com/en/docs/tweets/optimize-with-cards/guides/getting-started#card-and-content-attribution
  # do not include @
  creator = ""
  site = ""

[languages]
  [languages.en]
    languageName = "English"
    title = "Terminal"
    subtitle = "A simple, retro theme for Hugo"
    owner = ""
    keywords = ""
    copyright = ""
    menuMore = "Show more"
    readMore = "Read more"
    readOtherPosts = "Read other posts"
    newerPosts = "Newer posts"
    olderPosts = "Older posts"
    missingContentMessage = "Page not found..."
    missingBackButtonLabel = "Back to home page"

    [languages.en.params.logo]
      logoText = "Terminal"
      logoHomeLink = "/"

    [languages.en.menu]
      [[languages.en.menu.main]]
        identifier = "about"
        name = "About"
        url = "/about"
      [[languages.en.menu.main]]
        identifier = "showcase"
        name = "Showcase"
        url = "/showcase"
```

## 5. AÑADIR CONTENIDO A LA WEB

Para Hugo cualquier archivo markdown ".md" creado en la raíz del directorio **content** sería una página del sitio o una página global.

Si colocamos el siguiente código, estando ubicados en el directorio raiz:

	hugo new Nombre_Archivo.md


Estamos creando una página global dentro del directorio **content/**.

Cada archivo que coloquemos a su vez dentro de **content/** y dentro de una carpeta, será una página dentro de una colección:

	hugo new coleccion/archivo.md


Podemos crear manualmente ficheros de contenido añadiéndolos dentro de la carpeta **content/** tal que así:
	
	content/<categoría>/<fichero>.<formato>

Después podemos rellenar manualmente los metadatos del archivo.

Si lo que queremos es crear un nuevo post para nuestro blog, el nuevo archivo **.md** debe estar dentro de la carpeta posts. A su vez puede estar en una subcarpeta que nos permita organizar el post dentro de una categoría:
 
```bash
hugo new posts/Mi_Post.md
```
## 6. METADATOS DE UN ARCHIVO .md CON EL TEMPLATE "TERMINAL"

Estos son los metadatos que se crean con el comando **hugo new posts/Mi_post.md** usando el template **terminal**:

	title = "Es el título del post"
	date = "2021-09-10T19:30:46+02:00"			#La fecha de creación
	author = "El Autor del post"
	authorTwitter = "Cuenta de twitter" 			#no incluir la  @
	cover = "" 						#agregar un marco al post
	tags = ["Hugo"] 					#Etiquetas para el post
	keywords = ["", ""]
	description = "Descripción del contenido del post"
	showFullContent = false


## 7. INICIAR EL SERVIDOR DE HUGO

```bash
hugo server -t terminal
```

Al iniciar, el servidor te indica la dirección que hay que poner en el navegador para previsuaizar la web en la línea:

	Web Server is available at //localhost:1313/

Debemos poner **localhost:1313** en nuestro navegador para ver la web.

## 8. CONSTRUIR LA WEB

Para poder subir nuestra web al servidor, debemos construir las páginas en formato estático partiendo de nuestro sitio en formato markdown, para ello en el directorio raíz, usamos el comando:

```bash
hugo -D
```

Esto nos genera todo el contenido estático necesario para subir al servidor dentro de la carpeta `./public/` por defecto. Podemos poner `-d/ --destination` para cambiarlo o seleccionarlos en `publishdir` en el config file.
