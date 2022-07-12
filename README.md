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

Ejercicio 9: Correr PasswordAPI en Kubernetes
---------------------------------------------

Escribir el descriptor yaml (deployment) para correr la aplicación PasswordAPI (https://hub.docker.com/r/nicopaez/password-api) en Kubernetes (minikube) con 3 replicas.

Puedes tomar este descriptor de ejemplo como puntos de partida (https://gitlab.com/-/snippets/2088421/raw/master/deployment.yaml).

Una vez tengas escrito el descriptor puedes aplicarlo con "kubectl apply -f".

En principio la aplicación no será accesible desde fuera del cluster, con lo cual para probarla puedes conectarte al pod (kubectl exec -it podname --  bash) y hacer un curl localhost:3000/password.

Una vez completo, compartir el link al repositorio (carpeta ejercicio09) con el correspondiente descriptor y las instrucciones que utilizaste para desplegar y verificar su funcionamiento.

Ejercicio 10: TelegramBot
---------------------------------------------

Desplegar en kubernetes un bot de telegram.

En primer lugar tienes que crear un bot a partir de:

1. Ir a https://web.telegram.org/#/im?p=@BotFather y seguir los pasos
2. Enviar el comando /newbot
3. Seguir los pasos y al final el BotFather responde con un token, tomar nota del token

Luego puedes utilizar esta imagen que ya tiene un bot listo con algunas funcionalidades básicas (nicopaez/telegrambot:0.0.7).
Para correr esa imagen necesitas darle una variable de ambiente TELEGRAM_TOKEN con el correspondiente valor del token que obtuviste previamente.

Primero asegurate de poner a correr el bot localmente con docker run y pasandole como variable de ambiente el TELEGRAM_TOKEN.
En telegram agrega el bot como contacto y chateale "/version". Deberá contestar con la versión.


Una vez que esto corra, entonces escribe el correspondientes descriptor para desplegar el bot en minikube.
Pista: puedes definir la variable de ambiente del token como parte del deployment.yaml.

Finalmente, entrega el link a tu repositorio (ejercicio10) incluyendo:

* un screenshot de un chat con el bot que muestre la versión
* el deployment.yml (no pongas el valor de token en el repo, simplemente deja "A COMPLETAR" )
* las instrucciones detalladas que seguiste

Ejercicio 11: desplegar Pingapp en Kubernetes
---------------------------------------------

Desplegar nicopaez/pingapp:2.1.0 en Kubernetes definiendo:

1. Un configmap1 con las variables de ambiente
```
CONFIG_LOCATION=/mydata/config.json
SECRETS_LOCATION=/mysecrets/secret.json
```

2. Definir un segundo configmap2:
`config.json = { "key1": "value1"}`

3. Definir un secret secret1:
`secret.json = { "mypass":"password!"}`

4. Definir un deployment.yaml que:
* Despliegue 3 replicas de nicopaez/pingapp:2.1.0
* Monte confimap1 como variables de ambiente
* Monte configmap2 y secret1 como volumenes

5. Definir un servicio de tipo NodePort que exponga el deployment

6. Una vez completo el deploy verificar que las variables de ambiente se leen correctamente y que al hacer un request a la ruta /config se ve el contenido de config.json y que la ruta /secrets se ve el contenido de secret.json

Escribe los todos los descriptores en una carpeta ejercicio11en tu repositorio personal y entrega el link correspondiente.

Ejercicio 12: JobVacancy en k8s
---------------------------------------------

Escribir todos los descriptores faltantes necesarios para correr en kubernetes la aplicación jobvacancy considerando:

* El descriptor adjunto
* La aplicación requiere de 2 variasbles: RACK_ENV: "production" y PORT: "3000"
* La aplicación espera una variable DATABASE_URL con url de conexión a la base de datos postgres

IMPORTANTE: hay que desplegar un contenedor postgresql (postgres:10.4) no un cluster de postgresql.

Ubica los descriptores en una carpeta ejercicio12 en tu repositorio personal y entrega el link.

Descriptor adjunto:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: jobvacancy
  labels:
    app: jobvacancy
spec:
  replicas: 1
  selector:
    matchLabels:
      app: jobvacancy
  template:
    metadata:
      labels:
        app: jobvacancy
    spec:
      containers:
      - name: webapp
        image: nicopaez/jobvacancy-ruby:1.0.5
        envFrom:
          - configMapRef:
              name: jobvacancyconfig
          - secretRef:
              name: jobvacancysecret
```

Ejercicio 13: definición de Probes
---------------------------------------------

Definir los correspondiente liveness y readiness probes para la aplicación passwordapi (nicopaez/password-api:1.5.0-java) apuntando al endpoint /actuator/health.

Entregar el correspondiente deployment en la carpeta ejercicio13 de tu repositorio. Entrega el link al mismo.

Ejercicio 14: Ingress
---------------------------------------------

Escribir los descriptores necesarios para desplegar nicopaez/password-api:2.0.1 y nicopaez/pingapp:3.0.0 en Minikube con un Ingress de manera tal que las aplicaciones sean accesibles en "tallerk8s.local/pingapp" y "tallerk8s.local/passwordapi" respectivamente.

Seguir el instructivo: https://kubernetes.io/docs/tasks/access-application-cluster/ingress-minikube/
Para poder probarlo localmente agrega una entrada en el archivo /etc/hosts de tu host "tallerk8s.local" para que apunte a la IP local de tu Minikube.

Ubica los descriptores en una carpeta ejercicio14, agrega dos screenshot que muestren su solución corriendo. Entrega el link a la carpeta.

Recomendación: para las reglas de ruteo del ingress puedes ver https://kubernetes.github.io/ingress-nginx/examples/rewrite/
