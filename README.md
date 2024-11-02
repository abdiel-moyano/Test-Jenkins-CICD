# Python Hello World with CI/CD Pipeline using Jenkins and Kubernetes

## Descripción

Este proyecto es un ejemplo básico de una aplicación "Hello World" en Python usando Flask, con un pipeline CI/CD configurado en Jenkins. El objetivo es demostrar cómo construir, probar y desplegar una aplicación en un clúster de Kubernetes (usando Minikube) a través de un pipeline automatizado en Jenkins.

## Estructura del Proyecto

- **app.py**: Archivo principal de la aplicación en Flask que devuelve "Hello, World from Dockerized Python!".
- **Dockerfile**: Archivo Docker para construir una imagen de la aplicación.
- **requirements.txt**: Lista de dependencias necesarias para la aplicación Flask.
- **deployment.yaml**: Manifiesto de Kubernetes para desplegar la aplicación en el clúster.

## Prerrequisitos

- **Docker**: Para construir y ejecutar la imagen Docker de la aplicación.
- **Minikube**: Para ejecutar el clúster de Kubernetes localmente.
- **Jenkins**: Para configurar y ejecutar el pipeline CI/CD.
- **kubectl**: Para interactuar con el clúster de Kubernetes.
- **Git**: Para clonar y gestionar el repositorio.

## Configuración del Entorno

1. Asegúrate de tener Docker y Minikube instalados y configurados.
2. Configura Minikube para usar Docker con el comando:

   ```bash
   eval $(minikube docker-env)