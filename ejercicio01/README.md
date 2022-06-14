1. Clonar imagen

```
docker pull nginx:1.22
```

2. Crear un container, ejecutarlo con un bind mount del directorio donde se
encuentra `index.html` y exponiendo el puerto 80 del container en el 8888
de localhost.

```
docker run --name ejercicio01 -v $PWD:/usr/share/nginx/html:ro -p 8888:80 -d nginx:1.22
```

