pipeline {
    agent any
    environment {
    GIT_COMMIT = sh(script: 'git rev-parse --short HEAD', returnStdout: true).trim()
    }
    stages {
        stage('Set up Minikube Docker Environment') {
            steps {
                script {
                    // Configura el entorno Docker para Minikube usando la ruta completa
                    sh '/usr/local/bin/minikube docker-env | sed \'s/export //g\' >> ~/.bashrc'
                    sh 'source ~/.bashrc'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Construye la imagen Docker usando la ruta completa
                    sh "/usr/local/bin/docker build -t myapp:${GIT_COMMIT} ."
                }
            }
        }

        stage('Deploy to Minikube') {
            steps {
                script {
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