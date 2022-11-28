# Practica Servidores Web

## Requisitos

### ·Instalación del servidor web apache. 

Usaremos dos dominios mediante el archivo hosts: centro.intranet(servirá el contenido mediante wordpress) y departamentos.centro.intranet(Servirá una aplicación en python)

### ·Activar los módulos necesarios para ejecutar php y acceder a mysql

### ·Instala y configura wordpress

### ·Activar el módulo “wsgi” para permitir la ejecución de aplicaciones Python

### ·Crea y despliega una pequeña aplicación python para comprobar que funciona correctamente.

### ·Adicionalmente protegeremos el acceso a la aplicación python mediante autenticación

### ·Instala y configura awstat.

### ·Instala un segundo servidor de tu elección (nginx, lighttpd) bajo el dominio “servidor2.centro.intranet”. 

Debes configurarlo para que sirva en el puerto 8080 y haz los cambios necesarios para ejecutar php. Instala phpmyadmin.

## INSTALACION SERVIDOR WEB APACHE

### Actualizamos el indice de paquetes locales
```bash

  sudo apt update
  
```

![image](https://user-images.githubusercontent.com/97993778/204223325-79071d0a-82d5-4cb5-9da4-65c4eb7e9b92.png)

### Instalamos el paquete de Apache

```bash

  sudo apt install apache2
  
```

![image](https://user-images.githubusercontent.com/97993778/204224141-79ab35e8-cd34-4576-947e-6cbd8fa6be79.png)

### Comprobamos la instalacion


```bash

  sudo service apache2 status
  
```

![image](https://user-images.githubusercontent.com/97993778/204227414-54679f99-e68d-4ffc-97ec-84147f475ddb.png)

## ESTABLECEMOS LOS DOMINIOS

### Accedemos al archivo de configuracion de dominios

```bash

  sudo nano /etc/hosts
  
```
![image](https://user-images.githubusercontent.com/97993778/204232153-d1e741f1-7afb-430a-b790-043e51b7e2e0.png)

### Dominio para Worpress

```bash

  127.0.0.1 centro.intranet
  
```
![image](https://user-images.githubusercontent.com/97993778/204232381-8803156d-b372-436b-ae3e-2df5098670f3.png)

### Dominio para aplicacion Python

```bash

  127.0.0.1 departamentos.centro.intranet
  
```
![image](https://user-images.githubusercontent.com/97993778/204232703-1e81e2b7-6e24-4171-9405-352f54deaa2b.png)

## INSTALAR/ACTIVAR MODULOS PHP Y MYSQL

## MODULO PHP

### Instalamos el paquete de PHP

```bash

  sudo apt install php libapache2-mod-php php-mysql
  
```

![image](https://user-images.githubusercontent.com/97993778/204229907-f0269ea0-fb49-4bf5-bb83-b3556a4069ee.png)

### Comprobamos la versión de PHP instalada

```bash

  php -v
  
```

![image](https://user-images.githubusercontent.com/97993778/204230314-e2a6566e-5da4-4b0c-8cce-39e48dcec18e.png)

## MODULO MYSQL

### Instalamos el paquete MySQL-Server

```bash

  sudo apt install mysql-server
  
```

![image](https://user-images.githubusercontent.com/97993778/204230600-feabc004-cbd0-4bf1-8993-557560ed52f4.png)

### Comprobamos la instalacion arrancando MySQL

```bash

  sudo mysql
  
```
![image](https://user-images.githubusercontent.com/97993778/204230845-adc440ee-7d2e-4bc3-90d9-7c4f4c2b0f07.png)

### Cerramos MySQL

```mysql

  exit
  
```
![image](https://user-images.githubusercontent.com/97993778/204231203-206746cf-ae39-4eba-b50d-b2d5580f9c98.png)

## WORDPRESS

### Instalamos el paquete curl

```bash

  sudo apt install curl
  
```
![image](https://user-images.githubusercontent.com/97993778/204235914-750a828b-3631-4f37-8ad9-c29e77390acd.png)

### Descargamos WordPress


```bash

  curl -O https://wordpress.org/latest.tar.gz
  
```

![image](https://user-images.githubusercontent.com/97993778/204236269-4b15e401-349a-499c-b501-d407f2c18a41.png)

### Descomprimimos el archivo descargado

```bash

  tar xzvf latest.tar.gz
  
```

![image](https://user-images.githubusercontent.com/97993778/204236530-f42276be-53d7-4ff4-bfc9-98dd67cd79aa.png)

### Copiamos el archivo de configuracion de Worpress cambiandole el nombre

```bash

  cp /tmp/wordpress/wp-config-sample.php /tmp/wordpress/wp-config.php
  
```

![image](https://user-images.githubusercontent.com/97993778/204237965-1bd33f9f-2132-44db-8bf8-bd46bce8a3a4.png)

### Movemos al directorio raiz

```bash

  sudo cp -a /tmp/wordpress/. /var/www/wordpress
  
```

![image](https://user-images.githubusercontent.com/97993778/204238246-8d664b7f-5dee-4304-bda6-42ad1faf66c6.png)

## CONFIGURACION WORDPRESS

### Establecemos los permisos

```bash

  sudo chown -R www-data:www-data /var/www/wordpress
  
```

![image](https://user-images.githubusercontent.com/97993778/204238929-801616cc-5ffa-45a1-8977-a2ba54a471a1.png)

### Copiamos los valores del generador de claves

```bash

  curl -s https://api.wordpress.org/secret-key/1.1/salt/
  
```

![image](https://user-images.githubusercontent.com/97993778/204239189-b36704a9-85a5-4492-87a3-6387ba91e9d4.png)


### Pegamos las claves en el archivo de configuracion de Wordpress y establecemos los datos de la base de datos

```bash

  sudo nano /var/www/wordpress/wp-config.php
  
```

![image](https://user-images.githubusercontent.com/97993778/204239859-28e868cc-c3a1-4117-a143-4440252ca517.png)

![image](https://user-images.githubusercontent.com/97993778/204239928-0f31916c-59c7-4376-b658-cc5fa4bf2146.png)

### Asignamos el dominio al directorio de instalación de Worpress

```bash

  sudo nano /etc/apache2/sites-available/000-default.conf
  
```

![image](https://user-images.githubusercontent.com/97993778/204240159-83a10680-1d97-40f1-8b17-a563a6ba7e9d.png)








