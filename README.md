# docker-compose-lamp

docker compose server LAMP: Linux, Apache, Mysql, PHP, and PhpMyadmin (.htaccess enable)


# instrucciones

Una vez clonado el repositorios tenemos la siguiente estructura de archivos y directorios

```
docker-compose-lamp
│   README.md
│   Docker-compose.yml    # archivo con las instrucciones del docker-compose    
│
└───docker
│   │   Dockerfile56
│   │   Dockerfile56
│   │   Dockerfile56
│   │   file012.txt
│   │
│   └─
│     
└───logs
│   │   56_access.log     
│   │   56_access.log
│   │
│   └───subfolder1
│   
└───folder2
    │   file021.txt
    │   file022.txt
```

todos los archivos y carpetas de las carpeta *www* tiene que pertenecer a usuario *www-data*
    sudo chown -R www-data www/

arrancar los contenedores
    docker-compose up

arrancar y parar en segundo plano
    docker-compose start
    docker-compose stop


    docker-compose start
    docker-compose stop



### entrar en bash de un contenedor mysql
    docker exec -it dbmy /bin/bash

### entrar en bash de un contenedor apache-php
   docker exec -it p56 /bin/bash

# Instrucciones basicas para el manejo de contenedores

Listar procesos en contenedores corriendo
    docker ps

Listar procesos en contenedores creados
    docker ps -

## Borrar contendor

borrar todos los contendores 
    docker stop $(docker ps -a -q)

# Eliminar todos los contenedores
docker rm $(docker ps -a -q)

# Eliminar todas las imágenes
docker rmi $(docker images -q)

docker image prune -a

listar interfaces de red
    docker network ls

docker network $(docker network ls -q)



# Backup
    docker exec CONTAINER /usr/bin/mysqldump -u root --password=root DATABASE > backup.sql

# Restore
    cat backup.sql | docker exec -i CONTAINER /usr/bin/mysql -u root --password=root DATABASE

# create data base
    docker exec -i CONTAINER /usr/bin/mysql -u root --password=root 'CREATE DATABASE mydatabase CHARACTER SET utf8 COLLATE utf8_general_ci;'

