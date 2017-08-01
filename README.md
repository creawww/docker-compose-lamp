# docker-compose-lamp

Docker compose server LAMP: Linux, Apache, Mysql, PHP, and PhpMyadmin (.htaccess enable)

Entorno de desarrollo de aplicaciones en php y mysql, con persistencia de la base de datos, y acceso a los log de apache, esta habilitado el uso de .htaccess y dispone de un phpmyadmin para gestinar las base de datos en entorno grafico.

# instrucciones

Una vez clonado el repositorios tenemos la siguiente estructura de archivos y directorios

```
docker-compose-lamp
│   README.md
│   Docker-compose.yml             # archivo con las instrucciones del docker-compose    
│
└───docker
│   │   Dockerfile56               # Dockerfile de instalacion de apache, php y librerias 
│   │   php.ini                    # Paramametros personalizados de php ini
│   │   virtualhost-php56.conf     # Paramametros personalizados virtualhost de apache
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
    │   index.php                  # index ejemplo y test con el phpinfo
    │   
```

Todos los archivos y carpetas de las carpeta **www** tiene que pertenecer a usuario **www-data**

    sudo chown -R www-data www/

La configuracion de la base de datos el host **DB_HOST='db:3306'**

Arrancar los contenedores (la primera vex se construyen build)

    docker-compose up

Arrancar y parar en segundo plano

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

Borrar todos los contenedores

    docker rm $(docker ps -a -q)


## Imagenes docker

### Listar imagenes almacenadas

	docker images

## Borrar imagen

    docker rmi <id/name>

Borrar todas las imágenes

    docker rmi $(docker images -q)

    o

	docker image prune -a


## interfaces de red docker

### listar interfaces de red

    docker network ls

### borrar interfaces de red

	docker network rm <id/name>

Borrar toda las interfaces de red

	docker network rm $(docker network ls -q)

