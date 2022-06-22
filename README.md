Enunciados
==========

Ejercicio 1 - Contenedor NGINX
------------------------------

1. Crea una página html que tenga tu nombre
2. Ejecuta una imagen nginx (https://hub.docker.com/_/nginx) para que sirva tu página. Para esto tendrás que utilizar el comando docker run y deberás investigar la documentación de la imagen nginx para descubrir cómo especificarle el contenido que el servidor debe servir.

Ten presente que no hay una única forma de resolver este ejercicio.

Pista: puede que tengas que utilizar docker run con la opción -v

Pongo los archivos que resuelven el ejercicio y las correspondientes instrucciones en una carpeta "ejercicio01" de tu repositorio Github y entrega en el classroom el link directo a la misma.


Ejercicio 2 - Publica una imagen
--------------------------------

1. Descarga la imagen nicopaez/pingapp:3.0.0
2. Crear un repositorio en dockerhub
3. Sube la imagen descargada al repositorio creado
4. Crea una carpeta "ejercicio02" en tu repositorio y pon dentro de la misma un archivo README.md con el detalle de instrucción que utilizaste para completar la tarea. 
5. Asegurate que la imagen queda publicada como pública
6. Incluye al final de las instrucciones la sentencia docker pull exacta para descargar tu imagen.

Pista: utilizar comandos tag, login y push

Ejercicio 3 - Jugando con contenedores
--------------------------------------

Investigar cuantas layers tienen las imágenes nicopaez/passwordapi-java:java8-alpine y nicopaez/passwordapi-java:java8-fabric.
¿Tienen estas dos imágenes alguna layer en común?

Crear una carpeta "ejercicio03" en tu repositorio y escribe tus respuesta en un archivo README.md dentro de esa carpeta. Entrega el link a dicho archivo.
Pista: puedes utilizar el comando "docker inspect" o la herramienta dive (https://github.com/wagoodman/dive)

Ejercicio 4
-----------

Adjunto hay un archivo .jar que tiene la aplicación PasswordApi.
Esa aplicación es una aplicación Java que se ejecuta con el comando: java -jar passwordapi.jar. Eso levanta una webapi en el puerto 8080 (ver captura de pantalla).
Lo que se pide es generar una imagen Docker que corra esa aplicación. Más concretamente lo que hay que hacer es:
1. Escribir un dockerfile
2. Generar la imagen a partir del dockerfile ejecutando un docker build
3. Publicar la imagen en Dockerhub

Resolver el ejercicio en un directorio "ejercicio04" del repositorio personal.
Agrega el .jar al repositorio de forma que quien clone el repo pueda reproducir el build.

Menciona en el readme:

1. El link a la imagen publicada en dockerhub
2. En qué te basaste para elegir la imagen base utilizada

Entregar el link a la carpeta del repositorio github.