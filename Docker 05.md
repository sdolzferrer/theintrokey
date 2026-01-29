# TEMA 5 – DOCKER COMPOSE

## 1. Introducción a Docker Compose

En aplicaciones reales es habitual trabajar con **más de un contenedor** al mismo tiempo, por ejemplo:
- Un servidor web
- Una base de datos
- Un backend
- Un frontend

Gestionar estos contenedores uno a uno con comandos `docker run` resulta complejo y poco práctico.  
Para resolver este problema, Docker proporciona **Docker Compose**, una herramienta que permite definir y ejecutar aplicaciones multicontenedor de forma sencilla.

---

## 2. Qué es Docker Compose

Docker Compose es una herramienta que permite:
- Definir varios servicios
- Configurar redes y volúmenes
- Arrancar y detener toda la aplicación con un solo comando

Todo ello se describe en un archivo llamado `docker-compose.yml`.

Docker Compose es especialmente útil en:
- Entornos de desarrollo
- Pruebas
- Aplicaciones multicapa
- Proyectos educativos

---

## 3. El archivo docker-compose.yml

El archivo `docker-compose.yml` utiliza el formato **YAML**, que se basa en indentación.

Estructura básica:

``` bash
version: "3.8"

services:

  servicio1:
    image: imagen
    ports:
      - "puerto_host:puerto_contenedor"
```
Es fundamental respetar la indentación para evitar errores.

---

## 4. Definición de servicios

Cada **servicio** representa un contenedor.

Ejemplo de servicio web:

services:
  web:
    image: nginx
    ports:
      - "8080:80"

Docker Compose se encarga de crear el contenedor, la red y los enlaces necesarios.

---

## 5. Uso de varios servicios

Ejemplo de aplicación con web y base de datos:

services:
  web:
    image: nginx
    ports:
      - "8080:80"

  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: root

Ambos servicios se comunican automáticamente a través de la red creada por Docker Compose.

---

## 6. Redes en Docker Compose

Por defecto, Docker Compose crea:
- Una red bridge
- Un nombre de red asociado al proyecto

Los servicios pueden comunicarse usando el nombre del servicio como hostname.

Ejemplo:
- El servicio `web` puede acceder a `db` usando `db` como nombre de host.

---

## 7. Volúmenes en Docker Compose

Docker Compose permite definir volúmenes de forma sencilla.

Ejemplo:

services:
  web:
    image: nginx
    volumes:
      - datos_web:/usr/share/nginx/html

volumes:
  datos_web:

Los volúmenes se crean automáticamente si no existen.

---

## 8. Comandos principales de Docker Compose

Para iniciar la aplicación:

docker compose up

Para iniciar en segundo plano:

docker compose up -d

Para detener y eliminar los contenedores:

docker compose down

Para ver el estado de los servicios:

docker compose ps

---

## 9. Variables de entorno

Docker Compose permite definir variables de entorno para configurar servicios.

Ejemplo:

environment:
  MYSQL_DATABASE: app
  MYSQL_USER: user
  MYSQL_PASSWORD: pass

Esto facilita la configuración sin modificar imágenes.

---

## 10. Ejemplo completo de Docker Compose

Ejemplo de aplicación web sencilla:

version: "3.8"

services:
  web:
    image: nginx
    ports:
      - "8080:80"
    volumes:
      - datos_web:/usr/share/nginx/html

volumes:
  datos_web:

Este archivo permite desplegar la aplicación con un solo comando.

---

## 11. Errores comunes en Docker Compose

Errores frecuentes incluyen:
- Mala indentación del archivo YAML
- Usar imágenes inexistentes
- Conflictos de puertos
- Olvidar definir volúmenes
- No detener correctamente los servicios

La mayoría de errores se detectan al ejecutar `docker compose up`.

---

## 12. Buenas prácticas

- Usar nombres claros para los servicios
- Documentar el archivo compose
- No exponer puertos innecesarios
- Usar volúmenes para datos persistentes
- Separar servicios por responsabilidad

---

## 13. Resumen

En este tema se ha aprendido a:
- Comprender qué es Docker Compose
- Definir aplicaciones multicontenedor
- Gestionar servicios, redes y volúmenes
- Utilizar comandos básicos
- Desplegar aplicaciones reales de forma sencilla

Docker Compose es un paso clave antes de introducir la orquestación con Kubernetes.

---

## 14. Ejercicios

1. Crea un archivo docker-compose.yml con un servicio Nginx.
2. Publica el puerto 8080.
3. Añade un volumen persistente.
4. Arranca la aplicación.
5. Detén y elimina los servicios.
6. Modifica el archivo y vuelve a desplegar.

---

## 15. Referencias

Docker Docs – Docker Compose overview  
https://docs.docker.com/compose/

Docker Docs – Compose file reference  
https://docs.docker.com/compose/compose-file/

Docker Docs – Docker Compose CLI  
https://docs.docker.com/engine/reference/commandline/compose/
