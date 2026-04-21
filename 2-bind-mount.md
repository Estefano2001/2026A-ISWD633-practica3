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
# COMPLETAR CON EL COMANDO
```
docker run -d --name mi-nginx -p 8080:80 -v C:\Users\asus\nginx\html:/usr/share/nginx/html nginx:alpine 
```

### ¿Qué sucede al ingresar al servidor de nginx?
#### Primero al ir a localhost:8080, me salio un error 403, esto porque la carpeta html esta vacia, entonces decidi incluir un index.html. Esto con el fin de que al ingresar al servidor de nginx no me salga ese error y ahora el resultado es el cuerpo del index.html creado.
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

### ¿Qué pasa con el archivo index.html del contenedor?
#### El archivo index.html original dentro del contenedor queda oculto porque el bind mount sobrescribe la carpeta /usr/share/nginx/html. Solo se muestran los archivos que tengo en la carpeta html del host.
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
#### El servidor nginx muestra el template completo que descarge, porque ahora esos archivos son los que están en la carpeta montada.
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

### Eliminar el contenedor
# COMPLETAR CON EL COMANDO
```
docker rm -f mi-nginx  
```
### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
#### El servidor segue mostrando el contenido de la carpeta html del host, porque los archivos están en la computadora y no se pierden al eliminar el contenedor.
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA


