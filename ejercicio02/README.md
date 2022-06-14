1. Crear un repositorio nuevo en Docker Hub

2. Descargar la imagen original

```
docker pull nicopaez/pingapp:3.0.0
```

3. Tagear la imagen con el usuario y repositorio usados

```
docker image tag nicopaez/pingapp:3.0.0 felopez/docker-ejercicio02
```

4. Loguearse en el registry dockerhub

```
docker login
```

5. Pushear la imagen

```
docker push felopez/docker-ejercicio02
```

6. Resultado

https://hub.docker.com/repository/docker/felopez/docker-ejercicio02
