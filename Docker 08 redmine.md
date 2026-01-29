# TEMA 8 – PROYECTO FINAL: DESPLIEGUE DE REDMINE CON DOCKER

## 1. Introducción al proyecto final

El proyecto final del curso consiste en el **despliegue de una aplicación real de uso profesional** utilizando contenedores Docker, aplicando de forma integrada todos los contenidos trabajados durante el curso.

En este caso, la aplicación seleccionada es **Redmine**, una herramienta ampliamente utilizada para la **gestión de proyectos, incidencias y tareas**, muy común en entornos de desarrollo y departamentos IT.

Este proyecto **NO utiliza Kubernetes**, ya que su objetivo es consolidar el dominio de:
- Docker
- Volúmenes
- Redes
- Docker Compose

---

## 2. Qué es Redmine

**Redmine** es una aplicación web de código abierto que permite:

- Gestión de proyectos
- Seguimiento de incidencias
- Control de tareas
- Gestión de usuarios y roles
- Integración con repositorios (Git, SVN)
- Control de tiempos

Es una herramienta real y profesional, utilizada en empresas y equipos de desarrollo.

Repositorio oficial:  
https://github.com/redmine/redmine

---

## 3. Objetivos del proyecto

El alumnado deberá ser capaz de:

- Desplegar una aplicación web real con Docker
- Utilizar Docker Compose correctamente
- Configurar una base de datos persistente
- Gestionar redes entre contenedores
- Aplicar buenas prácticas básicas de seguridad
- Documentar el proceso de despliegue

---

## 4. Arquitectura del proyecto

La arquitectura del proyecto se basa en **varios contenedores**:

- Contenedor Redmine (Ruby on Rails)
- Contenedor base de datos (MariaDB o PostgreSQL)
- Volúmenes persistentes
- Red Docker privada

Arquitectura lógica:
- Cliente (navegador)
- Aplicación web
- Base de datos

---

## 5. Requisitos del sistema

- Sistema Linux
- Docker instalado
- Docker Compose instalado
- Acceso a Internet
- Navegador web
- Editor de texto

---

## 6. Preparación del entorno

Crear un directorio de trabajo:

mkdir proyecto_redmine  
cd proyecto_redmine

Comprobar Docker y Docker Compose:

docker --version  
docker compose version

---

## 7. Archivo docker-compose.yml

El despliegue se realizará mediante Docker Compose.

Ejemplo de archivo `docker-compose.yml`:

version: "3.8"

services:
  db:
    image: mariadb:10.6
    container_name: redmine_db
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: redmine
      MYSQL_USER: redmine
      MYSQL_PASSWORD: redmine
    volumes:
      - db_data:/var/lib/mysql
    networks:
      - redmine_net

  redmine:
    image: redmine:latest
    container_name: redmine_app
    ports:
      - "8080:3000"
    environment:
      REDMINE_DB_MYSQL: db
      REDMINE_DB_DATABASE: redmine
      REDMINE_DB_USERNAME: redmine
      REDMINE_DB_PASSWORD: redmine
    depends_on:
      - db
    volumes:
      - redmine_files:/usr/src/redmine/files
    networks:
      - redmine_net

volumes:
  db_data:
  redmine_files:

networks:
  redmine_net:

---

## 8. Despliegue de la aplicación

Iniciar el proyecto:

docker compose up -d

Comprobar el estado:

docker compose ps

El primer arranque puede tardar varios minutos.

---

## 9. Acceso a Redmine

Acceder desde el navegador a:

http://localhost:8080

Credenciales por defecto:
- Usuario: admin
- Contraseña: admin

Se recomienda cambiar la contraseña tras el primer acceso.

---

## 10. Persistencia de datos

Gracias a los volúmenes Docker:
- Los proyectos creados se conservan
- Los usuarios y configuraciones persisten
- La base de datos no se pierde al reiniciar contenedores

Esto demuestra el uso correcto de volúmenes en un entorno real.

---

## 11. Seguridad básica aplicada

Durante el proyecto se deben aplicar las siguientes buenas prácticas:

- Uso de red privada Docker
- No exponer la base de datos
- Uso de contraseñas
- Separación de servicios
- No ejecución innecesaria como root
- Documentación de la configuración

---

## 12. Entrega del proyecto

El alumno deberá entregar un **PDF** que incluya:

1. Explicación de la arquitectura
2. Archivo docker-compose.yml comentado
3. Capturas de:
   - Contenedores en ejecución
   - Acceso a Redmine
4. Explicación del uso de volúmenes
5. Conclusiones personales

---

## 13. Criterios de evaluación

| Criterio | Puntuación |
|--------|------------|
| Docker Compose correcto | 2 |
| Contenedores funcionales | 2 |
| Redmine accesible | 2 |
| Uso de volúmenes | 2 |
| Seguridad básica | 1 |
| Documentación | 1 |
| TOTAL | 10 |

---

## 14. Ampliación (opcional)

Para alumnado avanzado:

- Uso de HTTPS con proxy inverso
- Copias de seguridad automáticas
- Uso de PostgreSQL
- Personalización de Redmine
- Gestión avanzada de usuarios

---

## 15. Resumen

Este proyecto final permite al alumnado:

- Aplicar todos los conceptos de Docker
- Trabajar con una herramienta profesional
- Simular un entorno real de empresa
- Desarrollar competencias prácticas de administración de sistemas

Con este proyecto se cierra el curso de forma aplicada y profesional.

---

## 16. Referencias

Redmine – Repositorio oficial  
https://github.com/redmine/redmine

Docker Hub – Imagen Redmine  
https://hub.docker.com/_/redmine

Docker Docs – Docker Compose  
https://docs.docker.com/compose/