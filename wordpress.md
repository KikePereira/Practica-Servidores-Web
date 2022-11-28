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
