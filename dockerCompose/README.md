# Qué es Docker Compose
    -Contenedores 
    -Servicios
        -Base de datos
            -Relacionales 
            -No relacionales
## SERVER LEMP
    -Linux CentOS versión 7
    -Nginx (apache server, solo que se usará nginx)
    -MySQL ó MariaDB v. 10 (base de datos)
    -PHP ^8.2 (lenguaje de programación, php-fpm)
    -PHPMyAdmin (administrador de base de datos) (--tarea)
    -NODE JS ^22 (--tarea extra administrador de node)
    -COMPOSER 2.8.6 ^
    -Laravel ^11 (instalación global)
    
# INSTRUCCIONES PARA CREAR UNA IMAGEN DE DOCKER COMPOSE

La idea es crear todas las instrucciones necesarias para levantar una imagen de docker compose, este debe tener centOS 7 como servidor web con nginx y php-fpm, y un contenedor de mysql o mariaDB. **TAREA** USER para mysql debe llamarse development y el password a su criterio.

Y se puede iniciar con isntrucciones simples pero funcionales, tambien en importante aclarar que dicha imagen debe correr en **windows 11 como huesped**, por lo tanto es necesario crear un **bash** para colocarlo como un script en el administrador de tarea de windows 11.

# Docker Compose con CentOS 7 + Nginx + PHP-FPM + MySQL

Este proyecto configura un entorno de desarrollo en producción con:

- Servidor web basado en CentOS 7 con Nginx y PHP-FPM
- Base de datos MySQL 5.7
- MariaDB
- 
## Estructura del Proyecto
```
dockerCompose/
|
|-- docker-compose.yml
|-- webserver/
|   |-- Dockerfile
|   |-- config/
|       |--- nginx.conf
|       |--- default.conf
|   |-- start.sh
|-- www/
|   |-- index.php
|-- logs/nginx/
|-- logs/mysql/
|-- logs/mariadb/
|-- start-docker.bat      # Scritp para ejecutar desde windows
|-- README.md

```
## Requisitos 
- windows 11 como huesped
- WSL 2 con Ubuntu, Debian, Arch Linux (u otra distro de linux)
  - ```link https://learn.microsoft.com/es-es/windows/wsl/install ``
  - `` link https://learn.microsoft.com/en-us/windows/wsl/install ``

## Instrucciones para el funcionamiento
1. Instalar WSL 2 en windows 11
    --debes abrir la terminal de windows con la poweshell en modo admininistrador. 
    ```bash
    wsl --install
    ```
2. Instalar Docker dentro de WSL (en linux), revise que no tenga isntalado docker desktop
    ```bash
    sudo apt-get update
    sudo apt-get install doceker.io docker-compose
    sudo usermod -aG docker $USER
    newgrp docker
    ```
    
3. Verificar la instalacion
    ```bash 
    docker --version
    docker-compose --version
    ```
### Instrunccinoes de uso
1. Clonar el proyecto
2. levantar el contenedor con el comando
```bash 
docker-compose build 
docker-compose up -d
```
3. Acceder a la pagina web
   --Acceder al navegador en http://localhost/index.php
   --nginx es necesario utilizar proxy reverse **tarea
   --enabled virtualhost (edit en php config)

4. Base de datos
   --schema tenerlo ya levantado
   --puerto mysql o mariaDB 3306, 3322 **tarea

## Automatizacion de el bash o script en widows
1. Crear un archivo llamado start-docker.bat
   ```bash
   @echo off
   wsl -d Ubuntu -e bash -c "cd /mnt/c/TU_USUARIO/PATH/dockerCompose && docker-compose up -d"
   ```
2. Verificaciones
   ```php
   <php? phpinfo() ?>
   ```
   ``` link http://tusencuestas.test/info.php```

## Notas
- **tarea** indica que es necesario realizar una tarea para completar el proyecto
- **tarea** indica que es necesario realizar una tarea para completar el proyecto
- **INFOR** Este stack puede usarse para desarrollo o producción, con las herramientas ??
- **NOTA** Se recomienda hacer backups de los volumenes regularmente.
  - Backup FULL
    - A donde lo enviamos?
  - Backup Incremental
    - A donde lo enviamos?
  - Backup Diferencial
    - A donde lo enviamos?
  - Backup de logs

