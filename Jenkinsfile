pipeline {
    agent any
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
                    sh "/usr/local/bin/docker build -t myapp:latest ."
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