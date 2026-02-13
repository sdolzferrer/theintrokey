# GUÍA DE RESOLUCIÓN  
# TEMA 10 – PROYECTO FINAL  
# DESPLIEGUE DE GLPI CON DOCKER

---

## 1. Objetivo del proyecto

Desplegar una instancia funcional de GLPI utilizando Docker, subir las imágenes personalizadas a Docker Hub y publicar los archivos de configuración en GitLab.

El proyecto debe demostrar:

- Construcción de imágenes Docker
- Publicación en Docker Hub
- Uso de Docker Compose
- Configuración de persistencia
- Documentación correcta

---

## 2. Requisitos previos

- Docker instalado
- Docker Compose instalado
- Cuenta en Docker Hub
- Cuenta en GitLab
- Conexión a Internet

Comprobar instalación:

```bash
docker --version
docker compose version
```

---

## 3. Crear imagen personalizada de GLPI

Aunque existe la imagen oficial `glpi/glpi`, el proyecto exige subir una imagen propia al repositorio personal.

### 3.1 Crear archivo Dockerfile

```Dockerfile
FROM glpi/glpi:latest

# Personalización opcional
LABEL maintainer="TuNombre"
```

### 3.2 Construir imagen

```bash
docker build -t usuario_dockerhub/glpi:1.0 .
```

Ejemplo:

```bash
docker build -t miusuario/glpi:1.0 .
```

---

## 4. Subir imagen a Docker Hub

### 4.1 Iniciar sesión

```bash
docker login
```

### 4.2 Subir imagen

```bash
docker push usuario_dockerhub/glpi:1.0
```

Verificar que aparece en tu perfil de Docker Hub.

---

## 5. Crear archivo .env

Crear archivo `.env`:

```
GLPI_DB_HOST=db
GLPI_DB_PORT=3306
GLPI_DB_NAME=glpi
GLPI_DB_USER=glpi
GLPI_DB_PASSWORD=glpi123
```

---

## 6. Crear docker-compose.yml

```yaml
version: "3.9"

services:

  db:
    image: mariadb:10.6
    container_name: glpi_db
    restart: unless-stopped
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: ${GLPI_DB_NAME}
      MYSQL_USER: ${GLPI_DB_USER}
      MYSQL_PASSWORD: ${GLPI_DB_PASSWORD}
    volumes:
      - db_data:/var/lib/mysql

  glpi:
    image: usuario_dockerhub/glpi:1.0
    container_name: glpi_app
    restart: unless-stopped
    env_file:
      - .env
    depends_on:
      - db
    ports:
      - "8080:80"
    volumes:
      - glpi_data:/var/glpi

volumes:
  db_data:
  glpi_data:
```

IMPORTANTE:
Debe utilizarse la imagen subida al Docker Hub personal.

---

## 7. Desplegar el proyecto

Desde la carpeta del proyecto:

```bash
docker compose up -d
```

Verificar:

```bash
docker compose ps
```

Acceder desde navegador:

```
http://localhost:8080
```

---

## 8. Instalación de GLPI

Durante el asistente:

- Host base de datos: db
- Puerto: 3306
- Usuario: glpi
- Contraseña: glpi123
- Base de datos: glpi

Finalizar instalación desde navegador.

---

## 9. Subir configuración a GitLab

Subir al repositorio:

- docker-compose.yml
- Dockerfile
- README.md
- .env (si procede)

---

## 10. Contenido mínimo del README.md

```markdown
# Proyecto Final – GLPI con Docker

## Enlaces

Docker Hub:
https://hub.docker.com/r/usuario_dockerhub/glpi

GitLab:
https://gitlab.com/usuario/proyecto-glpi

## Despliegue

docker compose up -d

Acceso:
http://localhost:8080
```

---

## 11. Entregables

Se debe subir en la entrega:

- README.md
- docker-compose.yml adaptado
- Archivos Dockerfile utilizados

---

## 12. Comprobaciones finales

✔ Imagen subida correctamente a Docker Hub  
✔ docker-compose usa imagen personal  
✔ Persistencia funcionando  
✔ GLPI accesible desde navegador  
✔ Repositorio GitLab correcto  
✔ Documentación completa  

---

## 13. Buenas prácticas

- No usar la etiqueta latest en producción
- Usar volúmenes para persistencia
- Documentar claramente los pasos
- Comprobar logs si hay errores:

```bash
docker logs glpi_app
```

---

FIN DEL PROYECTO
