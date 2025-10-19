## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
No contiene nada.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
```
docker run -d --name cont-mysql --network net-wp -e MYSQL_ROOT_PASSWORD=leoxd -e MYSQL_DATABASE=db_wordpress -e MYSQL_USER=wp_user -e MYSQL_PASSWORD=leo1 -v "F:\Alessss\6 semestre\ej3\db":/var/lib/mysql mysql:8

```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
Archivos de mysql

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es /var/www/html

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
```
docker run -d --name cont-wordpress --network net-wp -v "F:\Alessss\6 semestre\ej3\www":/var/www/html/ -p 9500:80 -e WORDPRESS_DB_HOST=cont-mysql -e WORDPRESS_DB_USER=wp_user -e WORDPRESS_DB_PASSWORD=leo1 -e WORDPRESS_DB_NAME=db_wordpress wordpress
```

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

Se logró recuperar el contenido con el comando anterior

