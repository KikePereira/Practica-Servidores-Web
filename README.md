# Practica Servidores Web

## Requisitos

### [·Instalación del servidor web apache](https://github.com/KikePereira/Practica-Servidores-Web/blob/main/Instalacion%20Apache.md)

Usaremos dos dominios mediante el archivo hosts: centro.intranet(servirá el contenido mediante wordpress) y departamentos.centro.intranet(Servirá una aplicación en python)

### [·Activar los módulos necesarios para ejecutar php y acceder a mysql](https://github.com/KikePereira/Practica-Servidores-Web/blob/main/PHP%20y%20MySQL.md)

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

## CREACION BASDE DE DATOS EN MYSQL

### Arrancamos MySQL

```bash

  sudo mysql -u root 

```

![image](https://user-images.githubusercontent.com/97993778/204241846-b3811d77-6d10-47a0-adc5-902b2f43f2e9.png)

### Creamos la base de datos

```mysql
  CREATE DATABASE wordpress DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;
  
```
![image](https://user-images.githubusercontent.com/97993778/204242301-0a3bb217-9ed3-48bb-9ef6-52c3f5e6936e.png)

### Creamos el Usuario de la base de datos

```mysql

  CREATE USER 'kike'@'%' IDENTIFIED WITH mysql_native_password BY 'password';
  
```
![image](https://user-images.githubusercontent.com/97993778/204242658-b01f2647-0cdb-4daa-9bd0-24b6e04f9b91.png)

### Le damos permisos al Usuario sobre la base de datos

```mysql

  GRANT ALL ON wordpress.* TO 'kike'@'%';
  
```

![image](https://user-images.githubusercontent.com/97993778/204242935-54ba48ba-fa44-459a-8193-e8b83c7ec53c.png)

### Cerramos MySQL

```mysql

exit

```

![image](https://user-images.githubusercontent.com/97993778/204243249-2fb1cacb-b92c-4141-86b9-beb37c6a6775.png)

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

```bash

<VirtualHost*:80>
  ServerName centro.intranet
  ServerAlias www.centro.intranet
  ServerAdmin webmaster@localhost
  DocumentRoot /var/www/wordpress
  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

![image](https://user-images.githubusercontent.com/97993778/204240492-7aac2157-cc24-4012-bbff-da3db540cb98.png)

### Comprobamos que funciona en el explorador

![image](https://user-images.githubusercontent.com/97993778/204246247-4cbf586f-aaa2-4e51-92d9-971e132a7db7.png)

## Activar el módulo “wsgi” 

### Instalamos el paquete WSGI

```bash

  sudo apt install libapache2-mod-wsgi-py3

```

![image](https://user-images.githubusercontent.com/97993778/204244192-9b7ecfe4-d441-4dc5-8825-e84a3357738c.png)

### Creamos o introducimos nuestro script de Python

```bash

  sudo mkdir /var/www/html/test.py

```

```python

  def application(environ, start_response):
    status = '200 OK'
    output = b'Hello Howtoforge!\n'
    response_headers = [('Content-type', 'text/plain'),
                        ('Content-Length', str(len(output)))]
    start_response(status, response_headers)
    return [output]
    
 ```

![image](https://user-images.githubusercontent.com/97993778/204244433-800422e6-0755-4b98-9712-4d6f273462e3.png)

### Le establecemos los permisos al archivo

```bash

  sudo chown www-data:www-data /var/www/html/test.py
  sudo chmod 775 /var/www/html/test.py

```
![image](https://user-images.githubusercontent.com/97993778/204244814-28f78e37-af57-49d8-bb37-65aa60d1a1d0.png)

### Vinculamos el dominio con el directorio

```bash

  sudo nano /etc/apache2/sites-available/000-default.conf

```

![image](https://user-images.githubusercontent.com/97993778/204245263-1e7e7b62-6c14-4a92-ac17-16a7017c3bac.png)


```bash

<VirtualHost*:80>
  ServerName departamentos.centro.intranet
  ServerAlias www.departamentos.centro.intranet
  ServerAdmin webmaster@localhost
  DocumentRoot /var/www/html
  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
  WSGIcriptAlias /test /var/www/html/test.py
</VirtualHost>

```
![image](https://user-images.githubusercontent.com/97993778/204245305-c159b0e6-3944-4ce0-862d-91efe511bd7a.png)

### Reiniciamos Apache

```bash

  service apache2 restart

```

![image](https://user-images.githubusercontent.com/97993778/204245442-9c214ad4-7570-4f19-a0d5-336c6b21386d.png)

### Comprobamos el funcionamiento en el explorador

![image](https://user-images.githubusercontent.com/97993778/204245577-47a279d4-055b-46a9-a589-7a049a37b151.png)











