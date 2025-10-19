# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
docker run -d  --name mi-nginx  -p 80:80 -v F:\Alessss\6 semestre/nginx/html nginx:alpine

### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar al servidor de Nginx, el contenedor recibe la petición HTTP, Nginx busca el archivo solicitado dentro de /usr/share/nginx/html (que apunta a tu carpeta local), y devuelve el contenido al navegador como una página web.
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

### ¿Qué pasa con el archivo index.html del contenedor?
Queda oculto y se usa el que tenemos en nuestro computador
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar al servidor de Nginx, este muestra el contenido descomprimido en la carpeta html, funcionando como un sitio web estático completo
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

### Eliminar el contenedor
docker rm -f mi-nginx
# COMPLETAR CON EL COMANDO

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
Nginx vuelve a servir los mismos archivos del directorio local.
Es decir, aunque el contenedor anterior fue eliminado, el contenido del sitio web no se pierde, porque los archivos están almacenados fuera del contenedor.
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA


