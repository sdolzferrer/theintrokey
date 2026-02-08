# TEMA 7 – ADMINISTRACIÓN DE DOCKER CON PORTAINER

## 1. Introducción

Hasta ahora, la administración de Docker se ha realizado mediante línea de comandos (CLI). Este método es potente, flexible y fundamental para cualquier administrador de sistemas.

Sin embargo, en muchos entornos reales se utilizan herramientas gráficas que facilitan la visualización y gestión de infraestructuras complejas. Una de las más utilizadas es Portainer.

Portainer no sustituye a Docker ni a la CLI, sino que la complementa.

## 2. ¿Qué es Portainer?

Portainer es una herramienta de administración gráfica para Docker que permite gestionar contenedores, imágenes, volúmenes y redes desde un navegador web.

Proporciona:

- Interfaz visual clara
- Gestión centralizada
- Reducción de errores operativos
- Mejor comprensión del estado del sistema

## 3. ¿Por qué usar Portainer en administración de sistemas?

Ventajas principales:

- Visualización inmediata del estado de Docker
- Gestión rápida de contenedores
- Ideal para supervisión y tareas rutinarias
- Muy útil en entornos educativos

Limitaciones:

- No sustituye el conocimiento técnico
- No reemplaza automatización avanzada
- No evita malas configuraciones

## 4. Arquitectura básica de Portainer

Portainer se ejecuta como un contenedor Docker más.

Componentes:

- Contenedor Portainer
- Volumen para persistencia
- Acceso al socket Docker (/var/run/docker.sock)
  
Gracias a este acceso, Portainer puede:

- ver contenedores
- gestionarlos
- supervisar recursos

## 5. Instalación de Portainer con Docker
Creación del volumen
docker volume create portainer_data

Ejecución del contenedor Portainer
``` 
docker run -d \
  -p 9000:9000 \
  --name portainer \
  --restart=always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data \
  portainer/portainer-ce
```

Comprobación:
```
docker ps
```
## 6. Acceso inicial y configuración

Acceder desde el navegador a:
```
http://localhost:9000
```

Pasos iniciales:

- Crear usuario administrador
- Seleccionar entorno Docker local
- Acceder al panel principal

## 7. Gestión de contenedores

Desde Portainer se puede:

- Ver contenedores en ejecución y detenidos
- Arrancar y detener contenedores
- Eliminar contenedores
- Consultar logs
- Acceder a consola

Comparación:

- CLI → docker ps
- Portainer → vista gráfica

## 8. Gestión de imágenes

Portainer permite:

- Ver imágenes descargadas
- Eliminar imágenes
- Descargar nuevas imágenes
- Ver etiquetas y tamaños

Esto facilita la limpieza del sistema.

## 9. Gestión de volúmenes

Desde Portainer se pueden:

- Visualizar volúmenes
- Comprobar qué contenedores los usan
- Eliminar volúmenes no utilizados

Es especialmente útil para entender la persistencia de datos.

## 10. Relación CLI vs GUI

Portainer no reemplaza la CLI:

| CLI           | Portainer      |
| ------------- | -------------- |
| Automatizable | Visual         |
| Scripts       | Supervisión    |
| Precisión     | Facilidad      |
| Fundamental   | Complementaria |

Un buen administrador debe dominar ambas.

## 11. Cuándo usar Portainer y cuándo no

Usar Portainer para:

- Supervisión
- Gestión diaria
- Enseñanza
- Entornos pequeños/medios

No usar Portainer para:

- Automatización masiva
- Producción crítica sin control
- Sustituir conocimientos técnicos

## 12. Resumen

Portainer facilita la administración de Docker mediante una interfaz gráfica clara.
Debe utilizarse como herramienta de apoyo, no como sustituto del conocimiento técnico.

## 13. Ejercicios

1. Explica qué es Portainer
2. Indica dos ventajas y dos limitaciones
3. Compara una acción por CLI y por Portainer

## 14. Referencias

https://www.portainer.io

https://docs.docker.com
