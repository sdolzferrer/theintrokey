# TEMA 6 – BUENAS PRÁCTICAS Y SEGURIDAD EN DOCKER

## 1. Importancia de la seguridad en contenedores

Docker facilita el despliegue de aplicaciones, pero **no es seguro por defecto**.  
Una mala configuración puede provocar accesos no autorizados, exposición de servicios o incluso el compromiso del sistema anfitrión.

Por ello, aplicar buenas prácticas de seguridad es una responsabilidad clave del administrador de sistemas.

---

## 2. Principales riesgos en Docker

Algunos riesgos habituales en entornos Docker son:

- Uso de imágenes no oficiales o no verificadas
- Ejecución de contenedores con privilegios excesivos
- Exposición innecesaria de puertos
- Uso de versiones obsoletas
- Inclusión de credenciales en imágenes
- Montaje de directorios sensibles del host

Identificar estos riesgos es el primer paso para mitigarlos.

---

## 3. Uso de imágenes seguras

Para reducir riesgos se recomienda:

- Utilizar imágenes oficiales
- Elegir imágenes ligeras (alpine)
- Evitar imágenes sin mantenimiento
- Actualizar imágenes periódicamente

Ejemplo de imagen recomendada:

nginx:alpine

Las imágenes ligeras reducen la superficie de ataque y el consumo de recursos.

---

## 4. Principio de mínimo privilegio

Por defecto, muchos contenedores se ejecutan como **root**, lo cual supone un riesgo.

Es recomendable:
- Crear usuarios específicos dentro del contenedor
- Evitar privilegios innecesarios
- No usar la opción `--privileged` salvo casos excepcionales

Ejemplo en Dockerfile:

FROM nginx:alpine  
RUN adduser -D appuser  
USER appuser

---

## 5. Gestión de puertos y redes

Exponer puertos innecesarios aumenta el riesgo de ataques.

Buenas prácticas:
- Publicar solo los puertos estrictamente necesarios
- Usar redes internas para comunicación entre servicios
- Evitar exponer bases de datos directamente

Ejemplo:

docker run -d -p 8080:80 nginx

No se deben publicar puertos si no es imprescindible.

---

## 6. Volúmenes y seguridad

Al montar volúmenes hay que extremar las precauciones:

- No montar directorios sensibles como `/`, `/etc` o `/home`
- Limitar permisos de escritura
- Usar volúmenes Docker en lugar de bind mounts en producción

Ejemplo inseguro:

docker run -v /:/host ubuntu

Este comando da acceso completo al sistema anfitrión.

---

## 7. Actualizaciones y mantenimiento

La seguridad depende también del mantenimiento:

- Actualizar imágenes regularmente
- Reconstruir imágenes periódicamente
- Eliminar imágenes y contenedores antiguos
- Mantener Docker actualizado

Ejemplo:

docker pull nginx  
docker build --no-cache .

---

## 8. Logs y monitorización

Supervisar el comportamiento de los contenedores permite detectar problemas de seguridad.

Herramientas básicas:
- docker logs
- docker inspect
- Monitorización del sistema anfitrión

Una monitorización adecuada ayuda a detectar accesos no autorizados o comportamientos anómalos.

---

## 9. Buenas prácticas generales

Resumen de recomendaciones clave:

- Usar imágenes oficiales y ligeras
- Aplicar el principio de mínimo privilegio
- No exponer servicios innecesarios
- Separar entornos (desarrollo, pruebas, producción)
- Documentar configuraciones
- Revisar logs regularmente

---

## 10. Casos reales de fallos de seguridad

Algunos incidentes comunes incluyen:
- Bases de datos expuestas sin contraseña
- Contenedores con acceso total al host
- Credenciales incluidas en imágenes públicas

Las consecuencias pueden ser:
- Pérdida de datos
- Caídas de servicio
- Compromiso del sistema

---

## 11. Resumen

En este tema se ha aprendido que:
- Docker requiere configuración segura
- Las malas prácticas generan riesgos importantes
- La seguridad depende tanto de Docker como del administrador
- Aplicar buenas prácticas reduce drásticamente los riesgos

Este tema cierra el bloque de Docker antes de pasar a Kubernetes.

---

## 12. Ejercicios

1. Enumera tres riesgos de seguridad en Docker.
2. Explica por qué no se recomienda ejecutar contenedores como root.
3. Indica dos buenas prácticas relacionadas con imágenes.
4. Analiza un comando Docker inseguro y propón una alternativa.

---

## 13. Referencias

Docker Docs – Docker security  
https://docs.docker.com/engine/security/

Docker Docs – Security best practices  
https://docs.docker.com/develop/security-best-practices/

Red Hat – Container security  
https://www.redhat.com/en/topics/containers/what-is-container-security
