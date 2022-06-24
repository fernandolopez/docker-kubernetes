Enunciados
==========

Ejercicio 1: Contenedor NGINX
-----------------------------

1. Crea una página html que tenga tu nombre
2. Ejecuta una imagen nginx (https://hub.docker.com/_/nginx) para que sirva tu página. Para esto tendrás que utilizar el comando docker run y deberás investigar la documentación de la imagen nginx para descubrir cómo especificarle el contenido que el servidor debe servir.

Ten presente que no hay una única forma de resolver este ejercicio.

Pista: puede que tengas que utilizar docker run con la opción -v

Pongo los archivos que resuelven el ejercicio y las correspondientes instrucciones en una carpeta "ejercicio01" de tu repositorio Github y entrega en el classroom el link directo a la misma.


Ejercicio 2: Publica una imagen
-------------------------------

1. Descarga la imagen nicopaez/pingapp:3.0.0
2. Crear un repositorio en dockerhub
3. Sube la imagen descargada al repositorio creado
4. Crea una carpeta "ejercicio02" en tu repositorio y pon dentro de la misma un archivo README.md con el detalle de instrucción que utilizaste para completar la tarea. 
5. Asegurate que la imagen queda publicada como pública
6. Incluye al final de las instrucciones la sentencia docker pull exacta para descargar tu imagen.

Pista: utilizar comandos tag, login y push

Ejercicio 3: Jugando con contenedores
-------------------------------------

Investigar cuantas layers tienen las imágenes nicopaez/passwordapi-java:java8-alpine y nicopaez/passwordapi-java:java8-fabric.
¿Tienen estas dos imágenes alguna layer en común?

Crear una carpeta "ejercicio03" en tu repositorio y escribe tus respuesta en un archivo README.md dentro de esa carpeta. Entrega el link a dicho archivo.
Pista: puedes utilizar el comando "docker inspect" o la herramienta dive (https://github.com/wagoodman/dive)

Ejercicio 4: Creación de imagen PasswordApi
-------------------------------------------

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

Entregar el link a la carpeta del repositorio github.com

Ejercicio 5: Explorando Dockerfile commands
-------------------------------------------

Investigar que hacen y para que se usan los siguientes comandos dentro de un Dockerfile:

* HEALTHCHECK
* ONBUILD
* VOLUME

Escribir la respuesta en el repositorio personal en ejercicio05/README.md, entregar el link director al archivo.

Ejercicio 6: Imagen basada en RedHat
------------------------------------

Crear un contenedor para la aplicación PasswordApi (del ejercicio 4) que esté basada en la imagen redhat-openjdk-18/openjdk18-openshift
disponible en la registry de Red Hat (https://catalog.redhat.com/software/containers/redhat-openjdk-18/openjdk18-openshift/58ada5701fbe981673cd6b10).


1. Escribe el dockerfile
2. Genera la imagen (docker build)
3. Publica la imagen en tu cuenta de Dockerhub


Pon el dockerfile en un repositorio Github en una carpeta ejercicio06. Agregar también en esa carpeta un archivo readme con el link a la imagen generada en dockerhub.
Entrega el link a la carpeta en el repositorio Github.

Ejercicio 7: JobVacancy
-----------------------

Para este ejercicio necesitas docker-compose, si estas usando Docker Desktop ya lo tienes instalados, sino deberás instalarlo aparte.Crea un archivo llamado "docker-compose-jobvacancy.yml" y pon dentro el contenido de este link: https://gitlab.com/-/snippets/2088421/raw/master/docker-compose-jobvacancy.yml.

A continuación ejecuta este comando en una terminal: docker-compose -f docker-compose-jobvacancy.yml up.

Espera unos minutos hasta que dejen de aparecer mensaje en la terminal. Luego navega localhost:3000 para verificar que la aplicación levantó correctamente.

Finalmente contesta:

* ¿Cuántos contenedores se están ejecutando? (pueden verlo en el archivo docker-compose-jobvacancy.yml y también ejecutando docker ps)
* ¿Cuales son las imágenes en las que están basados los mencionados contenedores?
* ¿Puedes leer el docker-compose-jobvacancy.yml y describir lo que hace cada una de sus lineas?
* Dado que cada contenedor corre en forma aislada ¿Cómo es posible que esos contenedores se vean entre sí?

Escribe tus respuestas ejercicio07/README.md en tu repositorio github y entrega el link directo al archivo.

Ejercicio 8: Creación de cluster balanceado
-------------------------------------------

Utilizando docker compose generar una configuración para correr dos instancias de passwordapi balanceadas por Nginx.
La aplicación tiene un endpoint /health que indica la ip/host de la instancia que atendió el pedido, se puede usar esto para verificar el correcto balanceo.

Poner la solución en un carpeta ejercicio08, incluyendo:

* la configuración de compose
* el README.md con la forma correrlo y cualquier explicación que consideres relevante. 

Entregar el link directo a la carpeta en el repositorio.