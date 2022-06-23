* ¿Cuántos contenedores se están ejecutando? (pueden verlo en el archivo docker-compose-jobvacancy.yml y también ejecutando docker ps)

2 contenedores

* ¿Cuales son las imágenes en las que están basados los mencionados contenedores?
    - ejercicio07_db_1 está basado en la imagen postgres:latest
    - ejercicio07_web_1 está basado en la imagen nicopaez/jobvacancy-ruby:1.3.0

* ¿Puedes leer el docker-compose-jobvacancy.yml y describir lo que hace cada una de sus lineas?

```yaml
version: '2' # Versión del formato de docker-compose.yml
services:    # Acá se especifican los containers
  web:       # Crear un container con nombre "web"
    image: nicopaez/jobvacancy-ruby:1.3.0  # Imagen para crear el container
    links:
      - db   # Opción legacy para que "db" esté accesible por red desde "web"
    ports:
      - "3000:3000"  # Mapea el puerto 3000 del host con el 3000 del container
    environment:     # Setea variables de entorno para el container
      PORT: "3000"
      RACK_ENV: "production"
      DATABASE_URL: "postgres://postgres:Passw0rd!@db:5432/postgres"
    depends_on:
      - db           # Especifica que "db" debe arrancarse antes de "web"
  db:       # Crear un contenedor con el nombre "db"
    image: postgres  # Imagen para crear el container
    environment:     # Setea variables de entorno para el container
      POSTGRES_PASSWORD: Passw0rd!
```

* Dado que cada contenedor corre en forma aislada ¿Cómo es posible que esos contenedores se vean entre sí?

Ambos containers están en la misma red bridgeada por defecto y la opción links hace que "db" sea accesible a través del hostname "db" desde "web".