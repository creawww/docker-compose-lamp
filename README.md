# docker-compose-lamp

docker compose server LAMP: Linux, Apache, Mysql, PHP, and PhpMyadmin (.htaccess enable)


# instrucciones

Una vez clonado el repositorios tenemos la siguiente estructura de archivos y directorios

```
docker-compose-lamp
│   README.md
│   Docker-compose.yml             # archivo con las instrucciones del docker-compose    
│
└───docker
│   │   Dockerfile56
│   │   Dockerfile71
│   │   php.ini
│   │   virtualhost-php56.conf
│   └─
│     
└───logs
│   │   56_access.log     
│   │   56_access.log
│   │
│   └─
│
└───phpmyadmin
│   │
│   └───sessions                   # persistencia para las sesiones de phpmyadmin  
│ 
└───www                            # persistencia para la aplicacion web 
    │   index.php
    │   
```

todos los archivos y carpetas de las carpeta *www* tiene que pertenecer a usuario *www-data*

    sudo chown -R www-data www/

arrancar los contenedores

    docker-compose up

arrancar y parar en segundo plano

    docker-compose start
    docker-compose stop



### entrar en bash de un contenedor mysql
    docker exec -it dbmy /bin/bash

### entrar en bash de un contenedor apache-php
   docker exec -it p56 /bin/bash

# Instrucciones basicas para el manejo de contenedores

Listar procesos en contenedores corriendo

    docker ps <id/name>

Listar procesos en contenedores creados
    
    docker ps -a


## Parar contendor

    docker stop <id/name>

Parar todos los contendores
 
    docker stop $(docker ps -a -q)

## Borrar contendor

    docker rm <id/name>

borrar todos los contenedores

    docker rm $(docker ps -a -q)

## imagenes docker

### Listar imagenes almacenadas

	docker images

## Borrar imagen

    docker rmi <id/name>

Borrar todas las imágenes

    docker rmi $(docker images -q)

    o

	docker image prune -a

## listar interfaces de red

    docker network ls

## borrar interfaces de red

	docker network rm <id/name>

Borrar toda las interfaces de red

	docker network rm $(docker network ls -q)

# base de datos

## Backup

    docker exec CONTAINER /usr/bin/mysqldump -u root --password=root DATABASE > backup.sql

## Restore

    cat backup.sql | docker exec -i CONTAINER /usr/bin/mysql -u root --password=root DATABASE

## create data base

    docker exec -i CONTAINER /usr/bin/mysql -u root --password=root 'CREATE DATABASE mydatabase CHARACTER SET utf8 COLLATE utf8_general_ci;'

