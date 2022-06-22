Investigar que hacen y para que se usan los siguientes comandos dentro de un Dockerfile:

* HEALTHCHECK
    - Permite especificar un comando para verificar si un container se está ejecutando correctamente.
    - Agrega un health status al container, inicialmente en starting.
    - Dependiendo del exit code del comando el estado será:
        0: success - the container is healthy and ready for use
        1: unhealthy - the container is not working correctly
        2: reserved - do not use this exit code
    - Se puede especificar un periodo de gracia en el que se ignoran los estados unhealty, un
    intevalo para las pruebas, cuantos reintentos hacer y un timeout para cada intento con las opciones:
        --interval=DURATION (default: 30s)
        --timeout=DURATION (default: 30s)
        --start-period=DURATION (default: 0s)
        --retries=N (default: 3)
   
* ONBUILD
    - Permite guardar instrucciones como metadata de una imagen, esas instrucciones
    se ejecutarán en las imágenes derivadas de la que usa ONBUILD, justo después de
    su FROM.

* VOLUME
    - Declara un volumen para los containers. Sólo especifica el punto de montaje
    del volumen, no su ubicación en el host.