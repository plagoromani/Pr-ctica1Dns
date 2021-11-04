# ELABORACIÓN DE DOCKER-COMPOSE 
## version:3.3 -elegimos la versión a emplear
## services: -procedemos a añadir los servicios a crear
## asir_bind9: -nombre del servicio
## container_name: asir_bind9 -nombre del contenedor
## image: internetsystemsconsortium/bind9:9.16 -imagen que empleamos como SO
## networks:                -declaramos la información de la red del contenedor
##    br02:                 -asignamos el nombre de la red creada anteriormente
##       ipv4_address: 10.1.0.254       -IP fija del servidor 
##    ports:                            -Puertos de conexión
##      - 53:53
##    volumes:                          -Fichero de configuración del volumen
##      - conf:/etc/bind                
##
## asir_cliente:                    -nombre del servicio cliente
##    container_name: asir_cliente  -nombre del contenedor cliente
##    image: ubuntu                 -imagen que empleamos como SO
##    networks:                     -declaramos la información de la red del contenedor
##      - br02                      -asignamos el nombre de la red creada anteriormente
##    stdin_open: true              -Para que se nos abra un shell interactivo# ejecutarlo empleando docker run -i
##    tty: true                     -ejecutarlo empleando docker run -t
##    dns:                          -asignamos el dns al que hará peticiones
##      - 10.1.0.254                - el contenedor dns server
## volumes:                         -Se va a dar uso de las siguientes configuraciones, creadas previamente
## conf:
##    external: true # tenemos que tenerlo creado previamente
## networks:
##  br02: 
##    external: true

# CREACIÓN DE RED br02
## Empleamos comando: docker network create --subnet 10.1.0.0/24 --gateway 10.1.0.1 br02
## LISTAR REDES CREADAS: docker network ls
## INSPECCIONAR RED CREADA: docker network inspect br02

# EJECUCIÓN DOCKER COMPOSE
## LANZAR DOCKER-COMPOSE.YML:                                   docker-compose up
## PARAR SERVICIO:                                              docker stop
## ARRANCAR SERVICIO:                                           docker start
## ELIMINAR CONTENEDORES,RED,VOLUMEN E IMAGEN CREADAS:          docker-compose down
## ACCEDER A LA SHELL:                                          docker exec "name-container" bash

