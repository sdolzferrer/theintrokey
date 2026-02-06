# Docker Quick Reference Cheat Sheet

## Docker Build Commands

```bash
docker build -t <image_name> .
```

Build a Docker image from a Dockerfile in the current directory and tag it with a name.

```bash
docker build --no-cache -t <image_name> .
```

Build a Docker image without using the cache.

```bash
docker build -f <dockerfile_name> -t <image_name> .
```

Build a Docker image using a specified Dockerfile.

---

## Docker Clean Up Commands

```bash
docker system prune
```

Remove all unused Docker resources, including containers, images, networks, and volumes.

```bash
docker container prune
```

Remove all stopped containers.

```bash
docker image prune
```

Remove unused images.

```bash
docker volume prune
```

Remove unused volumes.

```bash
docker network prune
```

Remove unused networks.

---

## Container Interaction Commands

```bash
docker run <image_name>
```

Run a Docker image as a container.

```bash
docker start <container_id>
```

Start a stopped container.

```bash
docker stop <container_id>
```

Stop a running container.

```bash
docker restart <container_id>
```

Restart a running container.

```bash
docker exec -it <container_id> <command>
```

Execute a command inside a running container interactively.

---

## Container Inspection Commands

```bash
docker ps
```

List running containers.

```bash
docker ps -a
```

List all containers, including stopped ones.

```bash
docker logs <container_id>
```

Fetch the logs of a specific container.

```bash
docker inspect <container_id>
```

Inspect detailed information about a container.

---

## Image Commands

```bash
docker images
```

List available Docker images.

```bash
docker pull <image_name>
```

Pull a Docker image from a Docker registry.

```bash
docker push <image_name>
```

Push a Docker image to a Docker registry.

```bash
docker rmi <image_id>
```

Remove a Docker image.

---

## Docker Run Commands

```bash
docker run -d --name mi-contenedor --env-file .env -p 8080:3000 nombre-de-tu-imagen
```

```bash
docker run -d <image_name>
```

Run a Docker image as a container in detached mode.

```bash
docker run -p <host_port>:<container_port> <image_name>
```

Publish container ports to the host.

```bash
docker run -v <host_path>:<container_path> <image_name>
```

Mount a host directory or volume to a container.

```bash
docker run --name <container_name> <image_name>
```

Assign a custom name to the container.

---

## Docker Registry Commands

```bash
docker login
```

Log in to a Docker registry.

```bash
docker logout
```

Log out from a Docker registry.

```bash
docker search <term>
```

Search for Docker images in a Docker registry.

```bash
docker pull <registry>/<image_name>
```

Pull a Docker image from a specific registry.

---

## Docker Service Commands

```bash
docker service create --name <service_name> <image_name>
```

Create a Docker service from an image.

```bash
docker service ls
```

List running Docker services.

```bash
docker service scale <service_name>=<replicas>
```

Scale the replicas of a Docker service.

```bash
docker service logs <service_name>
```

View logs of a Docker service.

---

## Docker Network Commands

```bash
docker network create <network_name>
```

Create a Docker network.

```bash
docker network ls
```

List available Docker networks.

```bash
docker network inspect <network_name>
```

Inspect detailed information about a Docker network.

```bash
docker network connect <network_name> <container_name>
```

Connect a container to a Docker network.

---

## Docker Volume Commands

```bash
docker volume create <volume_name>
```

Create a Docker volume.

```bash
docker volume ls
```

List available Docker volumes.

```bash
docker volume inspect <volume_name>
```

Inspect detailed information about a Docker volume.

```bash
docker volume rm <volume_name>
```

Remove a Docker volume.

---

## Docker Swarm Commands

```bash
docker swarm init
```

Initialize a Docker swarm on the current node.

```bash
docker swarm join
```

Join a Docker swarm as a worker node.

```bash
docker node ls
```

List the nodes in a Docker swarm.

```bash
docker service create
```

Create a service in the Docker swarm.

```bash
docker service scale
```

Scale the replicas of a service in the Docker swarm.

---

## Docker Filesystem Commands

```bash
docker cp <container_id>:<container_path> <host_path>
```

Copy files from a container to the host.

```bash
docker cp <host_path> <container_id>:<container_path>
```

Copy files from the host to a container.

---

## Docker Environment Variables

```bash
docker run -e <variable_name>=<value> <image_name>
```

Set an environment variable when running a container.

**Flag:** `-e` or `--env` - Set environment variables when running a container.

---

## Docker Health Checks

```bash
docker container inspect --format='{{json .State.Health}}' <container_name>
```

Check the health status of a container.

**Dockerfile instruction:** `HEALTHCHECK` - Define a command to check the health of a container.

---

## Docker Compose Commands

```bash
docker compose --env-file .env.pro -f docker-compose-pro.yml up -d
```

```bash
docker-compose up
```

Create and start containers defined in a Docker Compose file.

```bash
docker-compose down
```

Stop and remove containers defined in a Docker Compose file.

```bash
docker-compose ps
```

List containers defined in a Docker Compose file.

```bash
docker-compose logs
```

View logs of containers defined in a Docker Compose file.

---

## Docker Stats

```bash
docker stats
```

Display a live stream of resource usage by containers.

```bash
docker stats <container_name>
```

Display the resource usage of a specific container.

# Docker:

Es una plataforma de virtualización a nivel de sistema operativo que permite empaquetar, distribuir y ejecutar aplicaciones en contenedores.
Docker se utiliza principalmente para crear y administrar entornos de desarrollo y producción.

## Containers:

Los contenedores son entornos aislados que contienen todo lo necesario para ejecutar una aplicación, incluidas las dependencias y configuraciones.

## Dockerfile:

Un Dockerfile es un archivo de texto que contiene instrucciones **para construir una imagen Docker**. Define cómo se crea una imagen desde una base y cómo se instalan las dependencias y se configuran los elementos en esa imagen.

## docker-compose.yml:

Un archivo docker-compose.yml es utilizado para definir y gestionar múltiples servicios, redes y volúmenes en un entorno de Docker. Puedes usarlo para orquestar contenedores basados en las imágenes definidas en los Dockerfiles o en imágenes de hub.docker.com

- Servicio:
  Un servicio en docker-compose.yml es una definición de cómo se ejecuta un contenedor específico. Aquí puedes configurar la imagen, puertos expuestos, variables de entorno, volúmenes compartidos, enlaces entre contenedores y más.
- Volume:
  Un volume es un mecanismo para persistir y compartir datos entre contenedores y el host. Puedes usar volúmenes para mantener datos que deben sobrevivir a la vida del contenedor.
- Red:
  Una NETWORK en Docker es un espacio aislado en el cual los contenedores pueden comunicarse entre sí. Puedes definir redes personalizadas para aislar y conectar contenedores.

# Comandos Básicos

- `docker stats`: Muestra uso de CPU, RAM y otros datos de consumo de cada container activo. El formato por defecto es 'table' (docker stats --format 'table') pero tambien se puede cambiar a 'json' (docker stats --format 'json')
  - Para solo mostrar info de CPU y RAM: `docker stats --format "table {{.Container}}\t{{.CPUPerc}}\t{{.MemUsage}}"`

- `docker cp <nombre o ID del contenedor>:/etc/apache2/sites-available/000-default.conf .`: Copiar un archivo del container a tu directorio.

- `docker pull <imagen>`
  Descarga una imagen de Docker desde un registro (como Docker Hub) a tu sistema local.

- `docker run <opciones> <imagen>`
  Crea un contenedor a partir de una imagen y lo ejecuta.

- `docker ps`
  Muestra una lista de contenedores en ejecución.
  - Parámetros:
    - `-a`: Muestra todos los contenedores tanto activos como detenidos.
    - `-q`: Muestra solo los IDs de los contenedores en vez de toda la información detallada.
    - `-a -f status=exited`: Muestra solo los contenedores detenido (Exited)
    - `-a -q -f status=exited`: Muestra solo los IDs de contenedores detenido (Exited)
    - `--no-trunc`: Para no cortar el texto de salida, muestra todo con detalles. A veces el texto es muy largo y no cabe en la columna asi que docker corta el texto. Si queremos saber toda la info usamos --no-trunc.

- `docker images`
  Lista las imágenes de Docker disponibles en tu sistema.

- `docker rm <contenedor>`
  Elimina uno o más contenedores.

- `docker rmi <imagen>`:
  Elimina una o más imágenes.
  - Por nombre y tag: `docker rmi uptask:1.0`
  - Por Imagen Id: `docker rmi de19be19cd42`
    - Es tambien posible solo con los 3 primeros digitos de la ImagenID: `docker rmi de1`

- `docker stop <contenedor>`
  Detiene un contenedor en ejecución.

- `docker stop $(docker ps -q)`
  Detiene todos los contenedores activos. Este comando utiliza una subshell para obtener la lista de IDs de todos los contenedores en ejecución a través del comando docker ps -q y luego pasa esos IDs al comando docker stop, que detendrá cada uno de esos contenedores. la opción -q es un atajo para indicarle a Docker que solo queremos que se muestren los IDs de los contenedores en lugar de toda la información detallada.

- `docker start <contenedor>`
  Inicia un contenedor detenido.

- `docker restart <contenedor>`
  Reinicia un contenedor en ejecución.

- `docker logs <contenedor>`
  Muestra los registros de salida de un contenedor.

- `docker exec <opciones> <contenedor> <comando>`
  Ejecuta un comando dentro de un contenedor en ejecución.

- `docker build <opciones> <ruta>`
  Construye una imagen de Docker a partir de un archivo Dockerfile y un contexto.

# Administración de Imágenes

- `docker image pull <imagen>`
  Descarga una imagen desde un registro.

- `docker image ls` o `docker images`:
  Lista imágenes en tu sistema.

- `docker image rm <imagen>`
  Elimina una o más imágenes.

- `docker image prune`
  Elimina imágenes no utilizadas.

# Administración de Contenedores

- `docker container ls`
  Lista contenedores en ejecución.
  - Parámetros:
    - `-a`: incluye los detenidos.

## Mostrar containers inactivos:

- `docker ps -a -f "status=exited"`: --filter se abrevia con solo -f

- `docker container rm <contenedor>`
  Elimina uno o más contenedores.

- `docker container prune`
  Elimina contenedores detenidos.

- `docker container inspect <contenedor>`
  Muestra información detallada sobre un contenedor.

- `docker container logs <contenedor>`
  Muestra los registros de un contenedor.

## Ejecutar comandos dentro de un container

- `docker container exec <opciones> <contenedor> <comando>`
  Ejecuta un comando dentro de un contenedor en ejecución.
  - Ejemplo: `docker container exec -it b8b70da89ea1 /bin/bash`
    - El comando `docker container exec` te permite ejecutar comandos dentro del contenedor, y en este caso, estás ejecutando una instancia interactiva del intérprete de comandos Bash dentro del contenedor especificado.
    - Contenedor Docker: Cuando se crea un contenedor, puede tener su propio sistema de archivos independiente. En este sistema de archivos del contenedor, las ubicaciones de los archivos y directorios son específicas para ese contenedor y no están relacionadas con el sistema de archivos del host.
    - Ubicación del Intérprete de Comandos en el Contenedor: La ruta `/bin/bash` se refiere al intérprete de comandos Bash ubicado dentro del sistema de archivos del contenedor. En los sistemas Unix-like, el directorio /bin es donde se almacenan los archivos ejecutables esenciales del sistema.
    - Ejecución del Comando: Al ejecutar el comando `docker container exec -it b8b70da89ea1 /bin/bash`, estás indicando a Docker que quieras ejecutar una instancia del intérprete de comandos Bash dentro del contenedor con ID b8b70da89ea1.
    - El comando `docker container exec -it b8b70da89ea1 /bin/bash` se utiliza para ejecutar un shell interactivo dentro de un contenedor Docker específico. Veamos el significado de las opciones -it:
      - La opción `-i` (abreviatura de "interactive") indica que quieres tener una sesión interactiva con el contenedor. Esto significa que podrás enviar comandos al shell del contenedor y recibir respuestas en tiempo real.

      - La opción `-t` (abreviatura de "tty") se utiliza para asignar un pseudo terminal (TTY) en la sesión interactiva. Esto permite que los comandos que ingreses y las respuestas del contenedor se muestren de manera adecuada, como si estuvieras interactuando con un terminal normal.

      - Al usar ambas opciones `-i` y `-t`, puedes acceder a una sesión de terminal dentro del contenedor de manera interactiva. En este caso, el comando ejecuta /bin/bash, que es el intérprete de comandos Bash, dentro del contenedor con ID b8b70da89ea1. Esto te proporciona un shell dentro del contenedor para ejecutar comandos y explorar su entorno.

# Ejecutar comandos MySQL en container de Docker

- `docker exec -it mi_contenedor_mysql mysql -u usuario -p`: Enter password.

## Limpiar la pantalla sin salid de MySQL

Dentro del monitor de MariaDB, puedes usar un comando específico de MariaDB llamado `\!` . Este comando permite ejecutar comandos del sistema operativo sin salir del monitor de MariaDB.

Para limpiar la pantalla, puedes usar el comando `\! clear` y presiona Enter.

# Redes en Docker

- `docker network ls`
  Lista las redes de Docker en tu sistema.

- `docker network create <nombre>`
  Crea una nueva red de Docker.

- `docker network connect <red> <contenedor>`
  Conecta un contenedor a una red.

- `docker network disconnect <red> <contenedor>`
  Desconecta un contenedor de una red.

# Volúmenes en Docker

- `docker volume ls`
  Lista los volúmenes de Docker en tu sistema.

- `docker volume create <nombre>`
  Crea un nuevo volumen de Docker.

- `docker volume inspect <volumen>`
  Muestra información detallada sobre un volumen.

# Docker Compose

- `docker compose up`
  Inicia contenedores definidos en un archivo docker-compose.yml.
  - Parámetros:
    - `-d` (detached mode): Se utiliza para indicar que deseas ejecutar los contenedores en segundo plano, lo que en inglés se llama "detached mode".
    - `-p my_proyect_name`: Si deseas personalizar el `compose stack` en lugar de utilizar el nombre de la carpeta del proyecto por defecto, usa esta bandera '-p' seguido de un nombre personalizado para el proyecto. Ejemplo: `docker compose -p my_proyect_name up -d`

- `docker compose down`
  Detiene y elimina contenedores definidos en un archivo docker-compose.yml.

- `docker compose down --volumes --rmi all`
  Detendrá todos los contenedores definidos en el archivo docker-compose.yml.
  Eliminará los contenedores detenidos.
  Eliminará las redes definidas en el archivo docker-compose.yml.
  Eliminará los volúmenes definidos en el archivo docker-compose.yml.
  Eliminará todas las imágenes que fueron creadas por el archivo docker-compose.yml.

- `docker compose logs`
  Muestra los registros de contenedores definidos en un archivo docker-compose.yml.

# Comandos de Inspección y Gestión

- `docker info`
  Muestra información sobre la instalación de Docker.

- `docker version`
  Muestra la versión de Docker que está instalada.

- `docker inspect <objeto>`
  Muestra información detallada sobre un objeto Docker (imagen, contenedor, volumen, red, etc.)

# Limpieza general

- `docker system prune`: Limpia recursos no utilizados, como imágenes no utilizadas, contenedores detenidos, redes no utilizadas y volúmenes sin usar. Puede liberar espacio en disco y mantener el entorno de Docker más limpio.
  - Parámetros adicionales:
    - `--all`: Esta variante del comando docker system prune elimina más tipos de recursos, incluyendo networks, volumes y build cache. Es más agresiva en la limpieza.

- `docker builder prune`: Limpia componentes de construcción, incluyendo imágenes intermedias y caches de construcción, liberando espacio y manteniendo un entorno más ordenado.

# Comandos Básicos

- `docker pull <imagen>`
  Descarga una imagen de Docker desde un registro (como Docker Hub) a tu sistema local.

- `docker run <opciones> <imagen>`
  Crea un contenedor a partir de una imagen y lo ejecuta.

- `docker ps`
  Muestra una lista de contenedores en ejecución.

- `docker images`
  Lista las imágenes de Docker disponibles en tu sistema.

- `docker rm <contenedor>`
  Elimina uno o más contenedores.

- `docker rmi <imagen>`
  Elimina una o más imágenes.

- `docker stop <contenedor>`
  Detiene un contenedor en ejecución.

- `docker stop $(docker ps -q)`
  Detiene todos los contenedores activos. Este comando utiliza una subshell para obtener la lista de IDs de todos los contenedores en ejecución a través del comando docker ps -q y luego pasa esos IDs al comando docker stop, que detendrá cada uno de esos contenedores.

- `docker start <contenedor>`
  Inicia un contenedor detenido.

- `docker restart <contenedor>`
  Reinicia un contenedor en ejecución.

- `docker logs <contenedor>`
  Muestra los registros de salida de un contenedor.

- `docker exec <opciones> <contenedor> <comando>`
  Ejecuta un comando dentro de un contenedor en ejecución.

- `docker build <opciones> <ruta>`: Ejemplo: `docker build -f <ruta> -t <nombre:tag> .`
  Construye una imagen de Docker a partir de un archivo Dockerfile y un contexto.

# Administración de Imágenes

- `docker image pull <imagen>`
  Descarga una imagen desde un registro.

- `docker image ls`
  Lista imágenes en tu sistema.

- `docker image rm <imagen>`
  Elimina una o más imágenes.

- `docker image prune`
  Elimina imágenes no utilizadas.

# Administración de Contenedores

- `docker container ls`
  Lista contenedores en ejecución.

- `docker container ls -a`
  Lista todos los contenedores, incluyendo los detenidos.

- `docker container rm <contenedor>`
  Elimina uno o más contenedores.

- `docker container prune`
  Elimina contenedores detenidos.

- `docker container inspect <contenedor>`
  Muestra información detallada sobre un contenedor.

- `docker container logs <contenedor>`
  Muestra los registros de un contenedor.

- `docker container exec <opciones> <contenedor> <comando>`
  Ejecuta un comando dentro de un contenedor en ejecución.

# Redes en Docker

- `docker network ls`
  Lista las redes de Docker en tu sistema.

- `docker network create <nombre>`
  Crea una nueva red de Docker.

- `docker network connect <red> <contenedor>`
  Conecta un contenedor a una red.

- `docker network disconnect <red> <contenedor>`
  Desconecta un contenedor de una red.

# Volúmenes en Docker

- `docker volume ls`
  Lista los volúmenes de Docker en tu sistema.

- `docker volume create <nombre>`
  Crea un nuevo volumen de Docker.

- `docker volume inspect <volumen>`
  Muestra información detallada sobre un volumen.

# Docker Compose

- `docker compose up -d`
  Inicia contenedores definidos en un archivo docker-compose.yml en background

- `docker compose down`
  Detiene y elimina contenedores definidos en un archivo docker-compose.yml.

- `docker compose down --volumes --rmi all`
  Detendrá todos los contenedores definidos en el archivo docker-compose.yml.
  Eliminará los contenedores detenidos.
  Eliminará las redes definidas en el archivo docker-compose.yml.
  Eliminará los volúmenes definidos en el archivo docker-compose.yml.
  Eliminará todas las imágenes que fueron creadas por el archivo docker-compose.yml.

- `docker compose logs`
  Muestra los registros de contenedores definidos en un archivo docker-compose.yml.

# Comandos de Inspección y Gestión

- `docker info`
  Muestra información sobre la instalación de Docker.

- `docker version`
  Muestra la versión de Docker que está instalada.

- `docker inspect <objeto>`
  Muestra información detallada sobre un objeto Docker (imagen, contenedor, volumen, red, etc.)
