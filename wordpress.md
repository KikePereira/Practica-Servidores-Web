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
