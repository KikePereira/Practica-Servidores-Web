## AUTENTICACION

### Creamos el archivo y añadimos un nuevo Usuario con contraseña 
(Tras el comando nos pedira la contraseña)

```bash

  sudo htpasswd -c /etc/apache2/.htpasswd kike

```

![image](https://user-images.githubusercontent.com/97993778/204350451-ef89f512-7d4c-4ed2-adb3-aa7fac657e5a.png)

### Accedemos al archivo de configuracion

```bash

  sudo nano /etc/apache2/sites-enabled/000-default.conf

```
Añadimos el siguiente script
```bash

  <Directory /var/www/html>
        AuthType Basic
        AuthName "Secure area - Authentication required"
        AuthUserFile /etc/apache2/.htpasswd
        Require valid-user
  </Directory>
  
```
![image](https://user-images.githubusercontent.com/97993778/204351802-a26fa99b-ee87-47e2-9359-427fc2c1dacf.png)

### Comprobamos que nos pide Autenticacion al iniciar la aplicacion python

![image](https://user-images.githubusercontent.com/97993778/204351739-4aca5b9c-faa8-4609-89c5-2998e97716be.png)

