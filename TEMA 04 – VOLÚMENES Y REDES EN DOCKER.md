# TEMA 4 – VOLÚMENES Y PERSISTENCIA EN DOCKER

## Índice

1. Introducción a la persistencia en contenedores  
2. Problema de los datos efímeros  
3. Qué es un volumen Docker  
4. Tipos de almacenamiento en Docker  
5. Creación y gestión de volúmenes  
6. Uso de volúmenes en contenedores  
7. Ubicación física de los volúmenes  
8. Diferencia entre volumen y bind mount  
9. Buenas prácticas  
10. Resumen  
11. Ejercicios  
12. Referencias  

---

## 1. Introducción a la persistencia en contenedores

Los contenedores están diseñados para ser:
- ligeros
- rápidos
- desechables

Cuando un contenedor se elimina, **todo su sistema de archivos interno desaparece**.

Esto es un problema para servicios como:
- servidores web
- bases de datos
- aplicaciones empresariales

Estos servicios necesitan **guardar datos de forma permanente**.

---

## 2. Problema de los datos efímeros

Ejemplo:

1. Se crea un contenedor con un servidor web.
2. Se suben archivos al contenedor.
3. Se elimina el contenedor.

Resultado:
- Todos los archivos desaparecen.

Esto ocurre porque los datos están dentro del contenedor.

---

## 3. Qué es un volumen Docker

Un volumen es un **mecanismo de almacenamiento persistente** gestionado por Docker.

Permite:
- Guardar datos fuera del contenedor
- Mantener los datos aunque el contenedor se elimine
- Compartir datos entre contenedores

Ejemplo de creación:

```bash
docker volume create datos_web
```

---

## 4. Tipos de almacenamiento en Docker

Docker ofrece tres opciones principales:

| Tipo | Descripción |
|------|-------------|
| Volumen Docker | Gestionado automáticamente por Docker |
| Bind mount | Carpeta del sistema anfitrión |
| tmpfs | Almacenamiento temporal en memoria |

---

## 5. Creación y gestión de volúmenes

### Crear un volumen
```bash
docker volume create mi_volumen
```

### Listar volúmenes
```bash
docker volume ls
```

### Inspeccionar volumen
```bash
docker volume inspect mi_volumen
```

### Eliminar volumen
```bash
docker volume rm mi_volumen
```

---

## 6. Uso de volúmenes en contenedores

Ejemplo:

```bash
docker run -d \
-v datos_web:/usr/share/nginx/html \
-p 8080:80 \
nginx
```

Aquí:
- `datos_web` es el volumen
- `/usr/share/nginx/html` es la carpeta dentro del contenedor

Los datos del servidor web se guardarán en el volumen.

---

## 7. Ubicación física de los volúmenes

Docker se encarga automáticamente de:
- crear el volumen
- elegir la ubicación
- gestionar permisos
- montar el volumen en el contenedor

### Cuadro didáctico: ¿Dónde se guarda un volumen Docker?

| Concepto | Explicación sencilla | Ejemplo / comando |
|----------|----------------------|-------------------|
| Volumen Docker | Espacio de almacenamiento persistente gestionado por Docker | `docker volume create datos_web` |
| Ubicación física | Docker decide automáticamente dónde se guarda en el sistema anfitrión | `/var/lib/docker/volumes/` |
| Carpeta real del volumen | Directorio donde se almacenan los datos del contenedor | `/var/lib/docker/volumes/datos_web/_data` |
| Consulta de ubicación | Permite ver la ruta exacta del volumen en el sistema | `docker volume inspect datos_web` |
| Campo importante | Indica la ruta real del volumen | `"Mountpoint"` |
| Gestión de permisos | Docker configura automáticamente los permisos adecuados | Automático |
| Intervención del administrador | No es necesario conocer la ruta física para usar el volumen | Solo se usa el nombre del volumen |

### Comprobar la ubicación real

```bash
docker volume inspect datos_web
```

Salida típica:

```json
"Mountpoint": "/var/lib/docker/volumes/datos_web/_data"
```

---

## 8. Diferencia entre volumen y bind mount

| Característica | Volumen Docker | Bind mount |
|----------------|----------------|------------|
| Ubicación de datos | Gestionada por Docker | Definida por el usuario |
| Ruta en el sistema | Automática | Manual |
| Seguridad | Mayor | Depende del usuario |
| Uso recomendado | Producción | Desarrollo o pruebas |
| Ejemplo | `-v datos:/app` | `-v /home/user/app:/app` |

### Idea clave

> **Con los volúmenes, Docker decide dónde guardar los datos.  
> Con los bind mounts, lo decide el administrador.**

---

## 9. Buenas prácticas

- Usar volúmenes para datos persistentes
- No guardar datos importantes dentro del contenedor
- Nombrar los volúmenes de forma clara
- Eliminar volúmenes no utilizados

---

## 10. Resumen

- Los contenedores son efímeros
- Los volúmenes permiten persistencia
- Docker gestiona la ubicación automáticamente
- Los volúmenes son la opción recomendada en producción

---

## 11. Ejercicios

1. Crea un volumen llamado `datos_prueba`
2. Inspecciona su ubicación física
3. Ejecuta un contenedor Nginx usando ese volumen
4. Elimina el contenedor y comprueba si los datos siguen existiendo
5. Explica la diferencia entre volumen y bind mount

---

## 12. Referencias

- https://docs.docker.com/storage/volumes/
- Documentación oficial Docker
