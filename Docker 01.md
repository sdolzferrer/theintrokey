# TEMA 1 – CONTENEDORES Y SISTEMA OPERATIVO

## 1. Introducción a la virtualización

En la administración moderna de sistemas informáticos, la virtualización es una técnica fundamental que permite ejecutar múltiples sistemas o servicios aislados sobre un mismo hardware físico. Esta técnica ha sido clave para optimizar recursos, reducir costes y mejorar la flexibilidad de los entornos de TI.

Tradicionalmente, la virtualización se ha implementado mediante **máquinas virtuales (VM)**. Cada máquina virtual incluye un sistema operativo completo, sus propias librerías y las aplicaciones que se desean ejecutar. Para ello, se utiliza un **hipervisor**, que actúa como intermediario entre el hardware físico y las máquinas virtuales.

Este enfoque ha permitido:
- Consolidar servidores
- Aprovechar mejor el hardware
- Aislar servicios y sistemas

Sin embargo, también presenta importantes limitaciones, especialmente en entornos modernos donde se requiere rapidez, escalabilidad y automatización.

---

## 2. Evolución hacia los contenedores

Con la aparición de arquitecturas basadas en microservicios, despliegues continuos y metodologías DevOps, las máquinas virtuales comenzaron a resultar pesadas y poco ágiles.

Algunos de sus principales inconvenientes son:
- Alto consumo de recursos
- Arranques lentos
- Mayor complejidad de gestión
- Dificultad para escalar rápidamente

Para resolver estos problemas surge el concepto de **contenedor**, una forma de virtualización más ligera que permite ejecutar aplicaciones aisladas compartiendo el mismo sistema operativo anfitrión.

Los contenedores no sustituyen a las máquinas virtuales, sino que las complementan, ofreciendo una solución más eficiente para muchos casos de uso actuales.

---

## 3. Qué es un contenedor

Un **contenedor** es un entorno aislado que permite ejecutar una aplicación junto con todas sus dependencias (librerías, configuraciones, variables de entorno), sin necesidad de incluir un sistema operativo completo.

Características principales:
- Comparte el kernel del sistema anfitrión
- Es ligero y rápido
- Se crea y destruye fácilmente
- Es portable entre sistemas

Un contenedor garantiza que una aplicación se ejecute siempre de la misma forma, independientemente del entorno en el que se despliegue.

---

## 4. Docker como plataforma de contenedores

**Docker** es la plataforma de contenedores más extendida actualmente. Proporciona herramientas para crear, ejecutar, gestionar y distribuir contenedores de forma sencilla.

Docker permite:
- Crear imágenes reutilizables
- Ejecutar aplicaciones en contenedores
- Automatizar despliegues
- Facilitar el trabajo en equipo

Gracias a Docker, los contenedores se han convertido en una tecnología accesible y ampliamente adoptada tanto en entornos educativos como profesionales.

---

## 5. Arquitectura básica de Docker

La arquitectura de Docker se compone de varios elementos fundamentales:

- **Docker Engine**: motor que permite crear y ejecutar contenedores
- **Docker CLI**: interfaz de línea de comandos para interactuar con Docker
- **Docker Images**: plantillas a partir de las cuales se crean contenedores
- **Docker Containers**: instancias en ejecución de una imagen
- **Docker Hub / Registry**: repositorios de imágenes

El flujo habitual es:
1. Descargar o crear una imagen
2. Ejecutar un contenedor a partir de esa imagen
3. Gestionar el ciclo de vida del contenedor



---

## 6. Comparativa: máquinas virtuales vs contenedores

| Característica | Máquinas virtuales | Contenedores |
|---------------|-------------------|--------------|
| Sistema operativo | Propio | Compartido |
| Arranque | Lento | Muy rápido |
| Consumo de recursos | Alto | Bajo |
| Portabilidad | Media | Alta |
| Aislamiento | Muy alto | Alto |

Las máquinas virtuales siguen siendo útiles cuando se necesita un aislamiento completo o sistemas operativos distintos, mientras que los contenedores son ideales para aplicaciones y servicios ligeros.

---

## 7. Casos de uso reales en administración de sistemas

En entornos ASIR y profesionales, los contenedores se utilizan para:

- Servidores web (Apache, Nginx)
- Aplicaciones empresariales
- Entornos de desarrollo y pruebas
- Microservicios
- Integración continua (CI/CD)
- Laboratorios educativos

Su facilidad de uso y rapidez los convierte en una herramienta esencial para los administradores de sistemas modernos.

---

## 8. Ampliación técnica

A nivel interno, los contenedores se basan en mecanismos del kernel de Linux como:

- **Namespaces**: aíslan procesos, red, usuarios y sistemas de archivos
- **cgroups**: limitan y controlan el uso de recursos (CPU, memoria)
- **Sistemas de archivos en capas**: optimizan el almacenamiento de imágenes

Estos mecanismos permiten ofrecer aislamiento sin necesidad de virtualizar completamente el hardware.

---

## 9. Resumen

En este tema hemos visto que:

- La virtualización tradicional se basa en máquinas virtuales
- Los contenedores ofrecen una alternativa más ligera
- Docker es la plataforma más utilizada para contenedores
- Los contenedores son rápidos, portables y eficientes
- Son una herramienta clave en la administración moderna de sistemas

Este conocimiento será la base para todos los temas posteriores del curso.

---

## 10. Ejercicios

1. Explica la diferencia entre una máquina virtual y un contenedor.
2. Indica tres ventajas de los contenedores frente a las VM.
3. ¿Qué es Docker y para qué se utiliza?
4. Describe un caso de uso real de contenedores en ASIR.

---

## 11. Referencias

- Docker Inc. (2024). *What is a container?*  
  https://www.docker.com/resources/what-container/

- Red Hat. (2024). *Containers vs virtual machines*  
  https://www.redhat.com/en/topics/containers/containers-vs-vms

- IBM. (2024). *Containerization explained*  
  https://www.ibm.com/topics/containerization
