# Curso de Docker

**Arquitectura**
La arquitectura de Docker funciona cliente - servidor y además utiliza ‘daemon’ al conectarse con los contenedores.

*Un contenedor ejecuta sus procesos de forma nativa*

Docker no es un servidor, sino un servicio de sistema operativo (daemon) que corre en nuestro pc o en otro, el cliente es otro programa que también corre en nuestro pc o en otro que le da ordenes. Es decir, el cliente (cmd) le da las ordenes o se comunica por back al daemon quien crea los contenedores.

Si corres un contenedor por primera vez, docker lo descarga o busca su imagen, pero si lo corres una segunda vez, ya no muestra la info y corre lo que tiene que correr.

**Daemon**
Una vez el cliente hace la petición, el daemon se encarga de buscar la info, traerla a nuestra pc, de generar el contenedor y mostrar el output.

**¿Qué es un contenedor?**

Los contenedores son el **concepto fundamental** al hablar de docker. Un contenedor es una entidad lógica, una agrupación de procesos que se ejecutan de forma nativa como cualquier otra aplicación en la máquina host.

- Un contenedor es la pieza fundamental de Docker.
- Un contenedor es simplemente una agrupación de uno o más procesos. Es una entidad lógica que ejecuta sus procesos de forma nativa como si fuese cualquier otro proceso del sistema operativo anfitrión, no como una máquina virtual que los emula.
- Los procesos que se ejecutan dentro de los contenedores ven su universo como el contenedor define. Es decir, no pueden ver más allá del contenedor.
- Los procesos dentro del contenedor no tienen forma de consumir más recursos que los que el contenedor les permite.
- El único software que se comparte entre un contenedor y la máquina local es el kernel del sistema operativo. Es por esto que Docker corre de forma nativa solamente en Linux, porque utiliza el kernel de Linux; las versiones de MacOS y Windows son un tipo de virtualización, pero no funcionan igual que en Linux. Por esto, los servidores productivos utilizan solamente Linux sí o sí.
- Sistema de archivos: ¿a qué parte o sector del disco puede tener acceso un contenedor? Cuando un contenedor es ejecutado, el daemon le asigna un path y el contenedor lo toma como la dirección root; es decir, no puede sobrescribir para afuera, sólo puede crear lo que necesite dentro del path, puede escalar lo que quiera.
- Esta es la forma en la que Docker hace que los procesos de un contenedor estén aislados completamente del sistema anfitrión, el daemon no le permite ver más allá de lo que se le define.

- Es una agrupación de procesos, uno o más procesos.
- Es una entidad lógica, no tiene el limite estricto de las máquinas virtuales, emulación del sistema operativo simulado por otra más abajo.
- Ejecuta sus procesos de forma nativa.
- Los procesos que se ejecutan adentro de los contenedores ven su universo como el contenedor lo define, no pueden ver mas allá del contenedor, a pesar de estar corriendo en una maquina más grande.
- No tienen forma de consumir más recursos que los que se les permite. Si esta restringido a menos memoria ram, es la única que pueden usar.
- A fines prácticos los podemos imaginar cómo maquinas virtuales, pero NO lo son.
- Cuando un contenedor es ejecutado, el daemon de docker le dice, a partir de acá para arriba este disco es tuyo, pero no puedes subir mas arriba.
- Docker hace que los procesos adentro de un contenedor este aislados del resto del sistema, no le permite ver más allá.
- Cada contenedor tiene un ID único, también tiene un nombre.


La filosofía de los contenedores es totalmente diferente a la de las VMs. Si bien tratan también de aislar a las aplicaciones y de generar un entorno replicable y estable para que funcionen, en lugar de albergar un sistema operativo completo lo que hacen es compartir los recursos del propio sistema operativo “host” sobre el que se ejecutan.

    - Un contenedor es el estado en ejecución de una imagen.
    - A partir de una imagen pueden ejecutarse uno o varios contenedores, los mismos pueden agregarse o quitarse dinámicamente.
    - Se pueden realizar cambios sobre un contenedor determinado y guardar los cambios realizando un “commit” en el repositorio de Docker. Al realizar un commit de un estado particular de un contenedor, el repositorio de docker asignará un nuevo número de versión y creará una nueva imagen con estos cambios.

Docker Engine se encarga de lanzar y gestionar los contenedores con nuestras aplicaciones, pero en lugar de exponer los diferentes recursos de hardware de la máquina de manera discreta (es decir, 1 procesador y “x” GB de RAM… para cada aplicación), lo que hace es compartirlos entre todos los contenedores optimizando su uso y eliminando la necesidad de tener sistemas operativos separados para conseguir el aislamiento.


## Instalar en Ubuntu

Para instalar docker ir a:
<https://docs.docker.com/install/linux/docker-ce/ubuntu/>

## Comandos

**docker run**

-   Genera un contenedor nuevo.
    -   detach/-d: Correr Docker sin salida a terminal.
    -   docker run -d --name server -p 8080:80 nginx
    -   docker run -d --name db mongo
    -   docker run -d --name db -v path_local:path_contenedor imagen
    -   docker run -d --name db --mout src=nombre_volumne,dst=path_contenedor
    -   \--env: agrega una variable de entorno

**docker ps -a**

-   Muestra todos los procesos.
-   Status EXITED nos dice que el contenedor está apagado
-   docker ps -q
    -   Lista id de containers.

**docker inspect id/nombre_contenedor**

-   Muestra la meta data del contenedor.
-   El resultado es un **json**
-   Filtro:


    `$ docker inspect -f '{{json .Config.Env}}' id/nombre_contenedor
    $ ["PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"]`

    `docker inspect --format='{{ json .NetworkSettings.IPAddress }}' nginx1`
**docker rename nombre_contenedor nuevo_nombre**

-   Renombrar contenedor
-   Los nombres no se pueden repetir
-   docker run --rename nuevo_nombre nombre_contenedor
    -   Genera un contenedor nuevo que comparte la imagen con el contenedor anterior.

**docker log nombre_contenedor**

-   Crea un contenedor nuevo.

**docker log nombre_contenedor**

-   Muestra los outputs de los contenedores.

**docker rm nombre_contenedor**

-   Elimina el contenedor.
-   Eliminar todos los contenedores.
-   rm -f: fuerza la eliminación del contenedor.

    `docker rm -f $(docker ps -aq)`

**docker image ls**

-   Mostrar las imágenes

**docker history [param] nombre_imagen**

-   Lista las capas de una imagen.
-   no-truc: salida completa

## Ubuntu en contenedor

**docker run [params] nombre_imagen**

-   `-it`: Corre la terminal de Ubuntu contenido.
    -   Comprobar con: cat /etc/lsb-release
-   **docker run -it ubuntu comando**: ejecuta un comando
-   `--rm`: cuando termine de correr la imagen elimina el contenedor

**docker exec -it nombre_contenedor comando**

-   Ejecuta un comando en un contenedor que ya está corriendo.
    -   `ps -fea`: procesos de todas las sesiones.

**Ciclo de vida**: cuando el _rut command_ finalice, el contenedor también finaliza.

**docker kill nombre_contenedor**

-   Mata el proceso de un contenedor

## Docker vulumes

En Linux se encuentran en **/var/lib/docker/volumes**

**docker volume**

-   _ls_: muestra los volumenes.
-   _prune_: elimina los volumenes que no están en uso.
-   _create_ nombre: crea un nuevo volumen: `docker volume create volumeName`
-   `docker run it --name ubuntu7 -v vol1:/dir1 ubuntu bash`: monta un volumen creado con el comando docker volume create vol1.
-   `docker run it --name ubuntu8 -v vol1:/dir1:ro ubuntu bash`: monta un volumen creado con el comando docker volume create vol1, a diferencia del anterior es montado en modo lectura, esto se sabe por la opcion **:ro** al final de parámetro de volúmen.
-   `docker run -d --name db --mout src=nombre_volumne,dst=path_contenedor`
-   `docker run -d --name sys -v /datos ubuntu`
-   `docker run -it -v /root/dir1:/dir1 --name ubuntu2 ubuntu`  
-   Compartir volumenes: `docker run -it --name ubuntu2 --volumes-from ubuntu1 ubuntu bash` -> ubuntu2 usa los volumenes de ubuntu1 
-   _docker volume rm volumeNameORid_: borra un volumen.

## Imágenes

Las **imágenes** son un componente fundamental de Docker y sin ellas los contenedores no tendrían sentido. ***Estas imágenes son fundamentalmente plantillas o templates***.

Algo que debemos tener en cuenta es que las imágenes no van a cambiar, es decir, una vez este realizada no la podremos cambiar.

Las imágenes son plantillas de contenedores. A partir de las imágenes, generamos los contenedores que vamos a utilizar.

Una imagen de Docker no es un solo archivo, es un conjunto de capas. Una imagen está siempre construida con una capa base y capas que hay sobre la base. Cada capa es una pequeña diferencia de la anterior. Es esto lo que hace que las imágenes de Docker sean livianas.

Cuando se trabaja con una misma imagen con diferentes versiones, no va a descargar completamente todas las versiones, porque algunas capas ya habrán sido descargadas por otras versiones. Por lo cual, al descargar otra versión, sólo descargará las capas diferentes.

Cada capa de las imágenes es inmutables, y marca una diferencia respecto de la anterior.

**docker pull usuario/nombre_imagen**

-   solo nombre de imagen si es un repositorio oficial.
-   Descarga una imagen.
-   Para descargar una versión determinada: `docker pull ubuntu:18.10`



# Docker networking

**docker network [params]**

-   ls: muestra las redes.
-   create --attachable nombre_red
-   inspect
-   connect:
    -   docker network connect red contenedor

Conectar un contenedor a la red: docker network connect nombre_red nombre_imagen
docker run -d --name app -p 3000:3000 --env MONGO_URL=mongodb://db:27017/test platziapp
docker network connect platzinet app

# Dockerfile

**docker image**:
- ls: listar imagen

## Imágenes propias

**Crear un archivo Dockerfile**:

<code>
FROM ubuntu

RUN touch /usr/src/hola-platzi
</code>

En terminal ejecutar:
`docker build -t nombre_imagen path_contexto_de_build`

Ejemplo:
`Docker build -t ubuntu:quattro /home/quattro/my_docker_files`

**Contexto de build**: Sector de un disco que usa el daemon de Docker

Cambiar tag:
`docker image tag nombre_imagen usaurio_docker/nombre_imangen`
`docker image tag image:v7 repoName/image:v7` -> ahora el nombre del sepositorio sería reponame/image

**docker push usuario/nombreImagen**

-   Hace push al hub de docker

**Comandos**

- RUN: ejecuta comandos.

- CMD: comando por defecto del contenedor, solo puede haber uno por Dockerfile.

- ENTRYPOINT: como CMD, pero adiferencial de aquél, éste se ejecuta siempre, sólo puede haber unoi, usa la sintaxis de un array json.

- WORKDIR: Nos permite que los comandos  se ejecuten en determinado contexto.

- COPY: Copia archivos del host al contenedor. Sólo permite copiar de forma local o desde un directorio del host donde se construye la propia imágen.

- ADD: Como copy, pero permite descomprimir archivos tar y usar locaciones remotas.
    ADD f.tar .

- ENV: Agrega una variable de entorno, en línea de comandos se puede agregar así: `docker run -it --rm --env x="Valor" image:v4`. Las variables declaradas aquí se pueden usar en el pripo Docker file:
    ENV dir=/data dir1=/data1
    RUN mkdir $dir && mkdir $dir1

- ARG: Similar a ENV, sin embargo nos permite pasar variables al momento de construir la imágen, pero no se hereda en el contenedor, solo en la creación de la imágen, si queremos que se herede en la imágen es necesario usar ARG en conjunto con ENV como en el Ejemplo 2.
    # Ejemplo 1
    # Docker file:
    ARG: dir2
    RUN: mkdir $dir2
    
    # Línea de comandos:
    docker build -t image:v6 --build-arg dir2=/data2 .

    # Ejmeplo 2
    ARG user
    ENV user_docker=$user
    ADD add_user.sg /datos1
    RUN /datos1/add_user.sh

- EXPOSE: Expone puertos, pero no se hace públicos.  
    RUN apt-get install -y apache2
    EXPOSE 80
    CMD /datos1/entrypoint.sh
    ENTRYPOINT ["/bin/bash"]

- VOLUME:
    ADD paginas /var/www/html
    VOLUME ["/var/www/html"]

# Docker Compose

**docker-compose up**

- Inicia los contenedores.
- `--d` detach, no muestra salida.

**docker-compose down**
- Para todos los servicios.

**docker-compose logs**
- Muestra los registros.
- Agregar el nombre del contenedor delante de `logs` para ver únicamente los registros de esa aplicación.
- `-f contenedor` para ver lo que escupe el contenedor en la terminal.

**docker-compose exec**
- Ejecuta comando dentro del contenedor.
- Para ingresar al contenedor: `docker-compose exec nombre_contenedor bash`

**docker-compose scale**
- Escala la cantidad de contenedores:
  `docker-compose scale app=4`


# Docker in docker

docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock dokcer:VesionDocker

# Swarm

- docker swarm: gestión del cluster.
- docker service: permite crear servicios, tareas dentro del cluster.
- docker swarm init: inicia swarm, pero se debe tener sólo una ip, si se tienen más habrá que especificarla. Al host que se le pone este comando, se inicia como manager.
- docker swarm join-token worker: obtiene el token y comando para la conexión de un host al cluster.
- doker node: permite realizar las operaciones de docker en los nodos, también permite promover o degradar nodos a manager o worker.
    - docker node ls: lista los nodos
    - docker node inspect --preatty nodoName
    - docker node promote nodeName: promueve un nodo a manager.
    - docker node denoted nodeName: degrada un nodo mamager a worker.
    - Nota: los comandos de administración sólo pueden ejecutarse en un nodo manager leader.
    - docker swarm leave: nodo desactiva el cluster.
    -  dokcer node rm nodeName: remueve completamente el nodo del cluster.
- docker service create --replicas X --name serviceName image command: crea un servicio con X replicas y un nombre.
- docker service ls: muestra los servicios.
- docker service ps serviceName: muestra los procesos de los servicios.
- docker service logs serviceName: muestra los logs del servicio indicado.
- docker service inspect --pretty serviceName: muestra las propiedades del servicio.
- docker service scale serviceName=2


# Extras

<https://github.com/wagoodman/dive>: A tool for exploring a docker image, layer contents, and discovering ways to shrink the size of your Docker/OCI image.
