# TEMA 4 – VOLÚMENES Y REDES EN DOCKER

## 1. Introducción a la persistencia de datos

Por defecto, los contenedores Docker son **efímeros**. Esto significa que cuando un contenedor se elimina, todos los datos generados en su interior se pierden.

Este comportamiento no es un problema para aplicaciones sin estado, pero resulta crítico en servicios que manejan datos, como:
- Servidores web
- Bases de datos
- Aplicaciones empresariales

Para resolver este problema, Docker proporciona mecanismos de **persistencia de datos** y **comunicación en red** entre contenedores.

---

## 2. El problema de la persistencia en contenedores

Cuando un contenedor se detiene o elimina:
- Su sistema de archivos desaparece
- Los datos no se conservan
- El servicio debe volver a configurarse

Ejemplo:
Un contenedor con una base de datos perdería toda la información almacenada si no se utiliza un sistema de persistencia externo.

Por ello, separar la aplicación de los datos es una buena práctica fundamental.

---

## 3. Volúmenes en Docker

Un **volumen** es un mecanismo de almacenamiento gestionado por Docker que permite conservar datos fuera del ciclo de vida del contenedor.

Características principales de los volúmenes:
- Persisten aunque el contenedor se elimine
- Son gestionados por Docker
- Son reutilizables
- Son adecuados para entornos de producción

---

## 4. Creación y gestión de volúmenes

Para crear un volumen:

```
docker volume create datos_web
```

Para listar los volúmenes existentes:

```
docker volume ls
```

Para inspeccionar un volumen:

```
docker volume inspect datos_web
```

Docker se encarga de la ubicación física del volumen en el sistema anfitrión.

---

## 5. Uso de volúmenes en contenedores

Un volumen se puede montar en un contenedor con la opción `-v`.

Ejemplo:

```
docker run -d -v datos_web:/usr/share/nginx/html nginx
```

De este modo, los archivos se almacenan fuera del contenedor y se conservan aunque este se elimine.

---

## 6. Bind mounts

Un **bind mount** enlaza directamente una carpeta del sistema anfitrión con una ruta dentro del contenedor.

Ejemplo:

```
docker run -d -v /home/usuario/web:/usr/share/nginx/html nginx
```

Características de los bind mounts:
- El usuario controla la ruta
- Son útiles en desarrollo
- Menos seguros que los volúmenes
- Dependientes del sistema anfitrión

---

## 7. Volúmenes vs bind mounts

| Característica | Volúmenes | Bind mounts |
|---------------|----------|-------------|
| Gestión | Docker | Usuario |
| Persistencia | Alta | Alta |
| Portabilidad | Alta | Baja |
| Seguridad | Alta | Media |
| Uso recomendado | Producción | Desarrollo |

---

## 8. Introducción a las redes en Docker

Además del almacenamiento, los contenedores necesitan comunicarse entre sí y con el exterior.

Docker utiliza **redes virtuales** para:
- Aislar servicios
- Permitir comunicación controlada
- Gestionar puertos

Por defecto, Docker crea una red bridge.

---

## 9. Tipos de redes en Docker

Los tipos de redes más comunes son:

- **bridge**: red por defecto, usada para la mayoría de los casos
- **host**: el contenedor comparte la red del host
- **none**: sin acceso a red
- **overlay**: usada en entornos distribuidos (Docker Swarm)

En entornos ASIR se trabaja principalmente con redes bridge.

---

## 10. Publicación de puertos

Para permitir el acceso desde el exterior a un servicio dentro de un contenedor se utiliza la publicación de puertos.

Ejemplo:

```
docker run -d -p 8080:80 nginx
```

Esto conecta el puerto 8080 del host con el puerto 80 del contenedor.

---

## 11. Comunicación entre contenedores

Los contenedores conectados a la misma red pueden comunicarse entre sí utilizando su **nombre** como hostname.

Ejemplo:
- Contenedor `web`
- Contenedor `db`

El contenedor web puede acceder a la base de datos usando `db` como nombre de host.

---

## 12. Casos de uso reales

Volúmenes:
- Bases de datos
- Contenido web
- Logs

Redes:
- Aplicaciones multicapa
- Frontend y backend
- Microservicios

El uso correcto de volúmenes y redes es clave en aplicaciones reales.

---

## 13. Buenas prácticas

- No almacenar datos importantes dentro del contenedor
- Usar volúmenes para producción
- Usar bind mounts solo en desarrollo
- No exponer puertos innecesarios
- Documentar configuraciones

---

## 14. Resumen

En este tema se ha aprendido a:
- Comprender el problema de la persistencia
- Utilizar volúmenes Docker
- Diferenciar volúmenes y bind mounts
- Configurar redes Docker
- Publicar puertos
- Comunicar contenedores

Estos conceptos son fundamentales para desplegar aplicaciones reales.

---

## 15. Ejercicios

1. Crea un volumen Docker.
2. Monta el volumen en un contenedor Nginx.
3. Crea un archivo dentro del contenedor.
4. Elimina el contenedor.
5. Vuelve a crear el contenedor y comprueba que el archivo sigue existiendo.
6. Publica un puerto y accede al servicio desde el navegador.

---

## 16. Referencias

Docker Docs – Storage volumes  
https://docs.docker.com/storage/volumes/

Docker Docs – Bind mounts  
https://docs.docker.com/storage/bind-mounts/

Docker Docs – Networking overview  
https://docs.docker.com/network/
