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

## Instalamos el paquete de Apache

```bash

  sudo apt install apache2
  
```

![image](https://user-images.githubusercontent.com/97993778/204224141-79ab35e8-cd34-4576-947e-6cbd8fa6be79.png)


