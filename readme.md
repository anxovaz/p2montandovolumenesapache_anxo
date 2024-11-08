# Práctica 2 - Anxo Vázquez Lorenzo

## 1. Comproba que tes a imaxe httpd

Para comprobar que está instalada a imaxe de httpd executo o comando "docker image ls" o cal mostra todas as imaxes dispoñibles.

docker image ls

## 2. Crea un contenedor de nome 'asir_httpd'

Executo o contenedor de httpd en segundo plano (&) co parámetro "--name" para indicarlle un nome.

docker run --name asir_httpd httpd &

## 3. Mapea o porto 80 do contenedor có 8080 da túa máquina

Primeiro monto o volume coa ruta do index.html.

docker run --mount type=bind,source="$(pwd)"/htdocs,target=/usr/local/apache2/htdocs httpd

Código html:
```shell
<html>
<head>
<meta charset="utf-8">
</head>
<body>
<h1>Anxo Vázquez Lorenzo - Práctica 2</h1>
</body>
</html>
```


Despois asigno o porto e indico a ruta da carpeta que contén o html (htdocs) e a ruta da carpeta htdocs do apache do contedor "asir_httpd".

docker run -it -p 8080:80 -v "$(pwd)"/htdocs:/usr/local/apache2/htdocs httpd

## 4. Monta unha páxina html aloxada no apache2 dende o teu navegador

Para acceder á páxina aloxada, uso a ruta "localhost:8080" nun navegador web.

(firefox) localhost:8080

## 5. Crea o contedor 'asir_web1' que use este mesmo directorio para 'htdocs' e o porto 8000

Primeiro creo o contedor coa imaxe de httpd co parámetro "--name" para indicarlle o nome de "asir_web1".

docker run --name asir_web1 httpd &

A continuación asigno o porto 8000 do equipo host e meto a ruta da carpeta que contén o html.

docker run -it -p 8000:80 -v "$(pwd)"/htdocs:/usr/local/apache2/htdocs httpd

Para comprobalo, uso o navegador web e introduzo a dirección "localhost:8000".

(firefox) localhost:8000

## 6. Crea outro contedor 'asir_web2' có mesmo directorio e outro porto, como o 8090

Realizo o mesmo que no paso 5, pero cambiando o porto do host asignado.

docker run --name asir_web2 httpd & docker run -it -p 8090:80 -v "$(pwd)"/htdocs:/usr/local/apache2/htdocs httpd

(firefox) localhost:8090