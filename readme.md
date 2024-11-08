#Práctica 2 - Anxo Vázquez Lorenzo

##1. Comproba que tes a imaxe httpd

###Para comprobar que está instalada a imaxe de httpd executo o comando "docker image ls" o cal mostra todas as imaxes dispoñibles.

###docker image ls



##2. Crea un contenedor de nome 'asir_httpd'

###Executo o contenedor de httpd en segundo plano (&) co parámetro "--name" para indicarlle un nome.

###docker run --name asir_httpd httpd &


##3. Mapea o porto 80 do contenedor có 8080 da túa maquina 

###Primeiro monto o volumen coa ruta do index.html

###docker run --mount type=bind,source="$(pwd)"/htdocs,target=/user/local7apache2/htdocs httpd

###Código html:

###<html>
###<head>
###<meta charset="utf-8">
###</head>
###<body>
###<h1>Anxo Vázquez Lorenzo - Práctica 2</h1>
###</html>

###Despois asigno o porto e indico a ruta da carpeta que contén o html (htdocs) e a ruta da carpeta htdocs do apache do contenedor "asir_httpd"

###docker run -it  -p 8080:80 -v "$(pwd)"/htdocs:/usr/local/apache2/htdocs httpd


##4. Monta unha páxina html aloxada no apache2 dende o teu navegador

###Para acceder a páxina aloxada uso a ruta "localhost:8080" nun navegador web.

###(firefox)localhost:8080


##5. Crea o contenedor 'asir_web1' que use este mesmo directorio para 'htdocs' e o porto 8000

###Primeiro creo o contenedor coa imaxe de httpd co parámetro "--name" para indicarlle o nome de "asir_web1"

###docker run --name asir_web1 httpd &

###A continuación asignolle o porto 8000 do equipo host e meto a ruta da carpeta que conten o html.

###docker run -it  -p 8000:80 -v "$(pwd)"/htdocs:/usr/local/apache2/htdocs httpd

###Para comprobalo uso o navegador web e introduzo a dirección "localhost:8000

###(firefox)localhost:8000


##6. Crea outro contenedor 'asir_web2' có mesmo directorio e outro porto, cómo o 8090

###Realizo o mesmo que no paso 5, pero cambiando o porto do host asignado

###docker run --name asir_web2 httpd &
###docker run -it  -p 8090:80 -v "$(pwd)"/htdocs:/usr/local/apache2/htdocs httpd
###(firefox)localhost:8090
