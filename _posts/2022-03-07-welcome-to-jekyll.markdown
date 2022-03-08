---
layout: post
title:  "Welcome to Jekyll!"
date:   2022-03-07 03:29:04 -0600
categories: jekyll update
---
# Docker-compose.yaml
El siguiente paso es crear el archivo yaml  donde espeficicaremos la version que sera la 3.3 y los servicios Wordpress, mysql, phpmyadmin y hhtps-portal para el acceso https
## Wordpress
![img]({{ site.url }}/Screenshot_20220308_125306.png)
> wordpress:
>    image: wordpress:php8.0
>    environment:
>      - WORDPRESS_DB_HOST=${WORDPRESS_DB_HOST}
>      - WORDPRESS_DB_USER=${WORDPRESS_DB_USER}
>      - WORDPRESS_DB_PASSWORD=${WORDPRESS_DB_PASSWORD}
>      - WORDPRESS_DB_NAME=${WORDPRESS_DB_NAME}
>    restart: always
>    volumes:
>      - wordpress_data:/var/www/html
>    depends_on:
>      - mysql
>    networks:
>      - frontend_network
>      - backend_network

En estas lineas asignamos en enviroment el host de nuestra base de datos de wordpress, el usuario, contraseña y nombre de la base de datos

añadimos la directiva de restart always para que este en constante reinicio
el volumen donde se guardara junto al servicio que depende eneste caso dependera de mysql
y por ultimo toca asignarle las redes que seran una fronted y otra backend

## Mysql

> mysql:
>    image: mysql:8.0 
>    environment:
>      - MYSQL_ROOT_PASSWORD=${MYSQL_ROOT_PASSWORD}
>      - MYSQL_DATABASE=${WORDPRESS_DB_NAME}
>      - MYSQL_USER=${WORDPRESS_DB_USER}
>      - MYSQL_PASSWORD=${WORDPRESS_DB_PASSWORD}
>    volumes:
>      - mysql_data:/var/lib/mysql
>    networks:    
>      - backend_network

en mysql lo mismo que en worpress asignamos la imagen 8.0 y lsa variables de .env, le asignamos el volumen y la red.
