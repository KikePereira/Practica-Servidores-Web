## SEGUNDO SERVIDOR

## Instalacion

### Instalamos Nginx

```bash

sudo apt install nginx

```
![image](https://user-images.githubusercontent.com/97993778/204383248-08d0d422-35e6-44a0-9a3e-091077c5b2ba.png)

### Instalamos los paquetes de PHP

```bash

sudo apt install -y php-fpm php-mysql php-json php-mbstring php-xml

```
![image](https://user-images.githubusercontent.com/97993778/204383616-9901f4ae-e74e-4c2f-aeb0-fef15abc90a6.png)

### Descargamos y extraemos phpMyAdmin

```bash

sudo wget https://files.phpmyadmin.net/phpMyAdmin/5.2.0/phpMyAdmin-5.2.0-all-languages.tar.gz
sudo tar -zxvf phpMyAdmin-5.2.0-all-languages.tar.gz

```

### Lo movemos hasta la carpeta contenedora

```bash

sudo mv phpMyAdmin-5.2.0-all-languages /var/www/phpmyadmin

```
### Movemos la plantilla de configuracion cambiandole el nombre

```bash

sudo mv /var/www/phpmyadmin/config.sample.inc.php /var/www/phpmyadmin/config.inc.php

```

## Configuracion

### Generamos el blowfish_secret

```bash

sudo pwgen -s 32 1

```
![image](https://user-images.githubusercontent.com/97993778/204384557-a0476ebc-1886-4aa3-8d98-cd7fe31cc4e5.png)

### Editamos el archivo de configuracion 

```bash

  sudo nano /var/www/phpmyadmin/config.inc.php

```
E insertamos/modificamos

```bash

$cfg['blowfish_secret'] = 'jO9yXAug2HX9GaZDCycrmWeqqtWHUS7T';

$cfg['Servers'][$i]['controlhost'] = 'localhost';
$cfg['Servers'][$i]['controlport'] = '';
$cfg['Servers'][$i]['controluser'] = 'pmauser';
$cfg['Servers'][$i]['controlpass'] = 'mypmapass';


```

![image](https://user-images.githubusercontent.com/97993778/204385420-fb937fd7-d951-4eea-8d13-fa0d905aa167.png)

### Relacionamos MySQL con phpMyAdmin

```bash

sudo mysql < /var/www/phpmyadmin/sql/create_tables.sql -u root -p

```
### Creamos la configuracion de servidor para phpMyAdmin en Nginx


```bash

sudo nano /etc/nginx/sites-available/phpmyadmin.conf

```
E insertamos/modificamos

```bash

server {
   listen 8080;
   server_name servidor2.centro.intranet;
   root /var/www/phpmyadmin;
   location / {
      index index.php;
   }
## Images and static content is treated different
   location ~* ^.+.(jpg|jpeg|gif|css|png|js|ico|xml)$ {
      access_log off;
      expires 30d;
   }
   location ~ /.ht {
      deny all;
   }
   location ~ /(libraries|setup/frames|setup/libs) {
      deny all;
      return 404;
   }
   location ~ .php$ {
      include /etc/nginx/fastcgi_params;
      fastcgi_pass unix:/run/php/php8.1-fpm.sock;
      fastcgi_index index.php;
      fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
   }
}

```

### Creamos una carpeta temporal para phpMyAdmin y cambiamos los permisos

```bash

sudo mkdir /var/www/phpmyadmin/tmp
sudo chmod 777 /var/www/phpmyadmin/tmp

```

### Establecemos la propiedad del directorio phpMyAdmin

```bash

sudo chown -R www-data:www-data /var/www/phpmyadmin

```

### Agregamos el dominio

```bash

sudo nano /etc/hosts

```
E insertamos

```bash

127.0.0.1 servidor2.centro.intranet

```
![image](https://user-images.githubusercontent.com/97993778/204387348-c607ffda-ad0e-4025-bca8-2996893351d1.png)


### Reiniciamos Ngnix y PHP

```bash

sudo systemctl restart nginx php8.1-fpm

```

### Comprobramos en el explorador que funciona

url(http://servidor2.centro.intranet:8080)

![image](https://user-images.githubusercontent.com/97993778/204387052-4b412996-e991-4837-8f10-b0132bf13df0.png)















