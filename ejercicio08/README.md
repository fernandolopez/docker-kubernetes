No encontré el endpoint /health (me tira 404), pero pude verificar que hace el
balanceo usando en endpoint /valid sin enviarle datos para que tire error y
verificando qué contenedor tiraba el error en la terminal.

`--scale` crea 2 contenedores para el servicio passwordapi. En la configuración
de NGINX configuré un proxy que redirige a `http://passwordapi:8080`.
Cuando NGINX quiera resolver ese nombre de host el servidor DNS interno de
Docker le va a contestar alternadamente la IP de alguno de los 2 containers
haciendo round-robin, así que con eso alcanzaría para un balanceo simple.

El comando para arrancar los servicios es:

```
docker-compose up --scale passwordapi=2
```
