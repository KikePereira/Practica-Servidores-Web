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
