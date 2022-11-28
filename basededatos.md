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
