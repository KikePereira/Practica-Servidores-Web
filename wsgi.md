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
