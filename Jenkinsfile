pipeline {
    agent any
    environment {
        DOCKER_PATH = '/usr/local/bin/docker'   // Ruta a Docker
        MINIKUBE_PATH = '/usr/local/bin/minikube' // Ruta a Minikube
        DOCKER_IMAGE = "myapp:latest"
    }
    stages {
        stage('Set up Minikube Docker Environment') {
            steps {
                script {
                    // Configurar el entorno Docker para Minikube
                    sh 'eval $(minikube docker-env)'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Construye la imagen Docker en el entorno de Minikube
                    sh "docker build -t $DOCKER_IMAGE ."
                }
            }
        }

        stage('Deploy to Minikube') {
            steps {
                script {
                    // Aplica el archivo de deployment en Minikube
                    sh "kubectl apply -f deployment.yaml"
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'There was an error during deployment.'
        }
    }
}