## INSTALACION AWSTATS

### Instalamos el paquete awstast

```bash

  sudo apt-get install awstats
  
```
![image](https://user-images.githubusercontent.com/97993778/204353246-826f054d-fde8-492b-a59c-b66a9cee4e05.png)

### Habilitar modulo CGI de Apache
(Luego reiniciamos Apache)

```bash

  sudo a2enmod cgi
  
```
![image](https://user-images.githubusercontent.com/97993778/204353590-7e1012e0-5704-4417-a12f-5852bac93e00.png)

## CONFIGURACION AWSTATS

### Creamos el archivo de configuracion para el dominio que queremos ver estadisticas

```bash

  sudo cp /etc/awstats/awstats.conf /etc/awstats/awstats.centro.intranet.conf

```

![image](https://user-images.githubusercontent.com/97993778/204357394-2aaf904b-7408-4c0c-8661-9ea1e49f244e.png)

### Modificamos el archivo de configuracion


```bash

  sudo nano /etc/awstats/awstats.centro.intranet.conf

```

Establecemos el nombre de dominio del sitio web

```bash

  SiteDomain='centro.intranet'
  HotAliases='centro.intranet localhost 127.0.0.1'
  
 ```

![image](https://user-images.githubusercontent.com/97993778/204357939-03796bbb-0246-406f-bc5d-7b692c839119.png)

![image](https://user-images.githubusercontent.com/97993778/204358222-ad9e3ab0-68d2-4ee9-b84d-6292d676d7f1.png)

Ponemos en 1 este parametro de configuracion para que nos permita actulizar la estadisticas mediante un boton desde el navegador web

```bash

 AllowToUpdateStatsFromBrowser=1
  
 ```
 
 ![image](https://user-images.githubusercontent.com/97993778/204358602-39d8053d-2d9b-4d7d-837b-3119334c3831.png)

Guardamos y cerramos el archivo de configuracion.

### Generamos las estadisticas inciales

```bash

  sudo /usr/lib/cgi-bin/awstats.pl -config=centro.intranet -update
  
 ```
![image](https://user-images.githubusercontent.com/97993778/204359082-1407007d-f030-43e9-a083-5ed0c0e3771d.png)

### Comprobamos que funciona con el siguiente enlace

```url

  http://centro.intranet/cgi-bin/awstats.pl?config=centro.intranet

```

![image](https://user-images.githubusercontent.com/97993778/204357076-5dd873f2-1d98-4a2a-9600-0354af260375.png)





