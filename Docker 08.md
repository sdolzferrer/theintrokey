# TEMA 7 – KUBERNETES (AMPLIACIÓN)

## 1. Introducción a la orquestación de contenedores

A medida que las aplicaciones crecen en complejidad y número de contenedores, gestionarlas manualmente se vuelve inviable.  
La **orquestación de contenedores** surge para automatizar tareas como el despliegue, la escalabilidad, la alta disponibilidad y la recuperación ante fallos.

**Kubernetes** es la plataforma de orquestación de contenedores más utilizada en la actualidad y se ha convertido en un estándar de facto en entornos profesionales.

---

## 2. Qué es Kubernetes

Kubernetes es una plataforma de código abierto que permite:
- Desplegar aplicaciones en contenedores
- Escalar servicios automáticamente
- Gestionar la comunicación entre contenedores
- Recuperarse de fallos
- Automatizar el ciclo de vida de las aplicaciones

Kubernetes no sustituye a Docker, sino que **trabaja sobre contenedores** creados previamente.

---

## 3. Arquitectura básica de Kubernetes

La arquitectura de Kubernetes se basa en un **clúster**, formado por varios nodos.

### Componentes principales:

- **Master (Control Plane)**: gestiona el clúster
- **Nodes (Workers)**: ejecutan los contenedores
- **API Server**: punto de entrada de Kubernetes
- **Scheduler**: decide dónde se ejecutan los Pods
- **Controller Manager**: mantiene el estado deseado
- **etcd**: base de datos de configuración

Esta arquitectura permite un control centralizado y escalable.

---

## 4. Pods

Un **Pod** es la unidad mínima de ejecución en Kubernetes.

Características:
- Puede contener uno o varios contenedores
- Comparte red y almacenamiento
- Es efímero
- No se gestiona directamente en producción

Normalmente, los Pods se crean mediante recursos de nivel superior como Deployments.

---

## 5. Deployments

Un **Deployment** define cómo debe ejecutarse una aplicación.

Permite:
- Definir el número de réplicas
- Actualizar versiones sin interrupciones
- Garantizar alta disponibilidad

Ejemplo de creación de un Deployment:

kubectl create deployment web --image=nginx

---

## 6. Réplicas y escalado

Kubernetes permite escalar aplicaciones fácilmente.

Escalar un Deployment:

kubectl scale deployment web --replicas=3

Kubernetes se encarga de:
- Crear nuevos Pods
- Distribuirlos entre los nodos
- Mantener el estado deseado

---

## 7. Services

Los Pods tienen direcciones IP cambiantes.  
Para acceder a ellos de forma estable se utilizan los **Services**.

Tipos comunes de Service:
- ClusterIP
- NodePort
- LoadBalancer

Ejemplo:

kubectl expose deployment web --type=NodePort --port=80

---

## 8. Acceso a aplicaciones en Kubernetes

En entornos locales como Minikube, se puede acceder a un servicio mediante:

minikube service web

Esto abre el navegador con la aplicación desplegada.

---

## 9. Archivos YAML en Kubernetes

Kubernetes utiliza archivos **YAML** para definir recursos.

Ejemplo de Deployment en YAML:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: web
spec:
  replicas: 2
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:
        - containerPort: 80

Aplicar el archivo:

kubectl apply -f deployment.yaml

---

## 10. Kubectl: herramienta de gestión

`kubectl` es la herramienta principal para interactuar con Kubernetes.

Comandos básicos:
- kubectl get pods
- kubectl get services
- kubectl describe pod
- kubectl delete pod
- kubectl apply -f archivo.yaml

El dominio de `kubectl` es esencial para trabajar con Kubernetes.

---

## 11. Kubernetes en entornos educativos

En formación ASIR se utilizan entornos simplificados como:
- **Minikube**
- **K3s**
- **MicroK8s**

Estos entornos permiten:
- Practicar sin infraestructuras complejas
- Simular entornos reales
- Prepararse para entornos profesionales

---

## 12. Relación Docker – Kubernetes

Docker:
- Crea imágenes
- Ejecuta contenedores

Kubernetes:
- Orquesta contenedores
- Gestiona escalado
- Asegura disponibilidad

Ambas tecnologías son complementarias y se utilizan juntas en entornos reales.

---

## 13. Casos de uso reales

Kubernetes se utiliza para:
- Aplicaciones web escalables
- Microservicios
- Plataformas cloud
- Entornos empresariales
- Alta disponibilidad

Grandes empresas basan su infraestructura en Kubernetes.

---

## 14. Resumen

En este tema se ha aprendido:
- Qué es Kubernetes
- Por qué es necesario
- Su arquitectura básica
- El concepto de Pods, Deployments y Services
- El uso de kubectl
- El papel de Kubernetes en entornos reales

Este tema prepara el camino para el proyecto final.

---

## 15. Ejercicios

1. Explica qué es Kubernetes y para qué se utiliza.
2. Describe la diferencia entre Pod y Deployment.
3. Crea un Deployment con Nginx.
4. Escala el Deployment a tres réplicas.
5. Expón el servicio y accede desde el navegador.

---

## 16. Referencias

Kubernetes Documentation  
https://kubernetes.io/docs/

Kubernetes Basics  
https://kubernetes.io/docs/tutorials/kubernetes-basics/

Red Hat – What is Kubernetes  
https://www.redhat.com/en/topics/containers/what-is-kubernetes
