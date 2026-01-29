# TEMA 3 – AUTOMATIZACIÓN CON DOCKERFILE

## 1. Introducción a la automatización con Docker

En los temas anteriores se ha trabajado con imágenes ya existentes. Sin embargo, en entornos profesionales es habitual **crear imágenes personalizadas** que incluyan aplicaciones propias, configuraciones específicas y dependencias concretas.

Para ello, Docker proporciona el **Dockerfile**, una herramienta fundamental para la automatización y la reproducibilidad de entornos.

Este tema introduce el uso de Dockerfile como base para la creación de imágenes propias.

---

## 2. Qué es un Dockerfile

Un **Dockerfile** es un archivo de texto plano que contiene una serie de instrucciones que Docker utiliza para construir una imagen de forma automática.

Cada instrucción del Dockerfile:
- Describe una acción
- Añade una capa a la imagen
- Permite reproducir exactamente el mismo entorno

Gracias a los Dockerfile se evita la configuración manual y se garantiza que todos los sistemas sean idénticos.

---

## 3. Estructura básica de un Dockerfile

Un Dockerfile está compuesto por instrucciones escritas en mayúsculas, una por línea.

Ejemplo mínimo de Dockerfile:

FROM nginx

Cada Dockerfile debe comenzar siempre con la instrucción `FROM`, que indica la imagen base sobre la que se construirá la nueva imagen.

---

## 4. Instrucciones principales del Dockerfile

### 4.1 FROM

Define la imagen base.

Ejemplo:

FROM ubuntu

---

### 4.2 RUN

Ejecuta comandos durante la construcción de la imagen.

Se utiliza normalmente para instalar paquetes o configurar el sistema.

Ejemplo:

RUN apt update  
RUN apt install -y nginx

---

### 4.3 COPY

Copia archivos o directorios desde el sistema anfitrión al interior de la imagen.

Ejemplo:

COPY index.html /var/www/html/

---

### 4.4 ADD

Funciona de forma similar a COPY, pero permite además descargar archivos desde URLs y descomprimir archivos comprimidos.

En la práctica se recomienda usar COPY salvo casos concretos.

---

### 4.5 WORKDIR

Define el directorio de trabajo dentro del contenedor.

Ejemplo:

WORKDIR /app

---

### 4.6 CMD

Define el comando que se ejecutará cuando el contenedor se inicie.

Ejemplo:

CMD ["nginx", "-g", "daemon off;"]

Solo puede haber una instrucción CMD activa.

---

## 5. Construcción de imágenes con Dockerfile

Para construir una imagen a partir de un Dockerfile se utiliza el comando:

docker build -t nombre_imagen .

El punto indica el contexto de construcción, normalmente el directorio actual.

Para comprobar que la imagen se ha creado:

docker images

---

## 6. Ejecución de una imagen creada

Una vez construida la imagen, se puede ejecutar un contenedor:

docker run nombre_imagen

O en segundo plano:

docker run -d -p 8080:80 nombre_imagen

---

## 7. Capas y caché en Docker

Cada instrucción del Dockerfile crea una **capa**.

Docker reutiliza capas mediante un sistema de caché, lo que acelera la construcción de imágenes si no han cambiado las instrucciones anteriores.

Por este motivo, el orden de las instrucciones es importante.

---

## 8. Buenas prácticas en Dockerfile

Algunas buenas prácticas recomendadas son:

- Usar imágenes base ligeras (alpine)
- Reducir el número de capas
- Agrupar comandos RUN
- Eliminar archivos temporales
- No incluir credenciales
- Documentar el Dockerfile

Ejemplo de imagen ligera:

FROM nginx:alpine

---

## 9. Ejemplo completo de Dockerfile

Ejemplo de Dockerfile para un servidor web sencillo:

FROM nginx:alpine  
COPY index.html /usr/share/nginx/html  
CMD ["nginx", "-g", "daemon off;"]

Este Dockerfile crea una imagen funcional en muy pocas líneas.

---

## 10. Errores comunes al usar Dockerfile

Errores frecuentes incluyen:
- Olvidar la instrucción FROM
- Copiar archivos incorrectos
- Usar imágenes demasiado grandes
- Ejecutar procesos en segundo plano
- No exponer los puertos necesarios

Detectar estos errores es clave para una buena automatización.

---

## 11. Resumen

En este tema se ha aprendido a:
- Comprender qué es un Dockerfile
- Crear imágenes personalizadas
- Automatizar entornos
- Utilizar las principales instrucciones
- Aplicar buenas prácticas

El uso de Dockerfile es esencial para entornos profesionales y será la base de los siguientes temas.

---

## 12. Ejercicios

1. Crea un Dockerfile basado en nginx.  
2. Copia un archivo HTML personalizado.  
3. Construye la imagen.  
4. Ejecuta el contenedor y accede desde el navegador.  
5. Modifica el Dockerfile y vuelve a construir la imagen.

---

## 13. Referencias

Docker Docs – Dockerfile reference  
https://docs.docker.com/engine/reference/builder/

Docker Docs – Best practices for Dockerfile  
https://docs.docker.com/develop/develop-images/dockerfile_best-practices/

Red Hat – Dockerfile explained  
https://www.redhat.com/en/topics/containers/what-is-a-dockerfile
