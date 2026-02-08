# TEMA 2 – ADMINISTRACIÓN DE CONTENEDORES

## 1. Introducción a la administración de Docker

Una vez comprendido el concepto de contenedores y el papel de Docker como plataforma, el siguiente paso es aprender a administrar contenedores de forma práctica. La administración de Docker consiste en gestionar el ciclo de vida de los contenedores y de las imágenes que los generan.

En este tema se trabajará con la línea de comandos de Docker, que es la herramienta principal utilizada por los administradores de sistemas.

## 2. Docker Engine y Docker CLI

Docker se basa en una arquitectura cliente-servidor.

El Docker Engine es el servicio que se ejecuta en segundo plano y se encarga de crear, ejecutar y gestionar contenedores.  

El Docker CLI es la interfaz de línea de comandos que permite al usuario comunicarse con el Docker Engine.

Cuando se ejecuta un comando como `docker run`, la CLI envía la orden al daemon de Docker, que realiza la acción solicitada.

## 3. Imágenes y contenedores

### 3.1 Imágenes

Una imagen Docker es una plantilla inmutable que contiene el sistema base, las dependencias necesarias, la aplicación y su configuración.

Las imágenes se descargan normalmente desde repositorios como Docker Hub.

Ejemplo de descarga de una imagen:

``` bash
docker pull nginx
```

### 3.2 Contenedores

Un contenedor es una instancia en ejecución de una imagen.  
Una misma imagen puede generar múltiples contenedores, todos ellos independientes entre sí.

## 4. Ejecución de contenedores

Para ejecutar un contenedor se utiliza el comando `docker run`.

Ejemplo básico:

``` bash
docker run nginx
``` 

Este comando descarga la imagen si no existe, crea el contenedor y ejecuta el servicio definido en la imagen.

Para ejecutar el contenedor en segundo plano:

``` bash
docker run -d nginx
```


## 5. Listado y estado de contenedores

Para ver los contenedores en ejecución:

``` bash
docker ps
```

Para ver todos los contenedores, incluidos los detenidos:

```
docker ps -a
```

Cada contenedor tiene un identificador único, un nombre y un estado.

## 6. Gestión del ciclo de vida de los contenedores

Para detener un contenedor:

```
docker stop ID_CONTENEDOR
```

Para iniciar un contenedor detenido:

```
docker start ID_CONTENEDOR
```

Para reiniciar un contenedor:

```
docker restart ID_CONTENEDOR
```

Para eliminar un contenedor:

```
docker rm ID_CONTENEDOR
```

## 7. Gestión de imágenes

Para listar las imágenes disponibles:

```
docker images
```

Para eliminar una imagen:

```
docker rmi ID_IMAGEN
```

Las imágenes ocupan espacio en disco, por lo que es importante mantenerlas organizadas.

## 8. Limpieza de recursos no utilizados

Docker proporciona el comando:

```
docker system prune
```

Este comando elimina contenedores detenidos, imágenes no utilizadas, redes no usadas y caché de construcción. Debe usarse con precaución.

## 9. Inspección y logs de contenedores

Para obtener información detallada de un contenedor:

```
docker inspect ID_CONTENEDOR
```

Para ver los logs de un contenedor:

```
docker logs ID_CONTENEDOR
```

Los logs son fundamentales para detectar errores y problemas de funcionamiento.

## 10. Errores comunes en la administración de contenedores

Errores habituales en Docker son no detener contenedores antes de eliminarlos, acumular imágenes innecesarias, no revisar los logs, ejecutar contenedores sin conocer su configuración o exponer puertos sin control.

Una buena administración evita estos errores mediante buenas prácticas.

## 11. Resumen

En este tema se ha aprendido a comprender la arquitectura de Docker, ejecutar contenedores, gestionar su ciclo de vida, administrar imágenes, limpiar recursos y realizar diagnósticos básicos.

Estos conocimientos son imprescindibles para continuar con los siguientes temas del curso.

## 12. Ejercicios

1. Ejecuta un contenedor Nginx en segundo plano.  
2. Lista los contenedores activos y detenidos.  
3. Detén un contenedor en ejecución.  
4. Elimina un contenedor detenido.  
5. Elimina una imagen que no se esté utilizando.  
6. Consulta los logs de un contenedor.

## 13. Referencias

Docker Docs – Docker CLI Reference  
https://docs.docker.com/engine/reference/commandline/docker/

Docker Docs – Get started  
https://docs.docker.com/get-started/

Red Hat – Docker container management  
https://www.redhat.com/en/topics/containers
