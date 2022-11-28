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





