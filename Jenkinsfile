pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    dockerapp = docker.build("josemarcosrt/guia-jenkins:${env.BUILD_ID}","-f ./src/Dockerfile ./src")
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    dockerapp.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                      dockerapp.push("latest")
                      dockerapp.push("${env.BUILD_ID}")
                    }    
                }
            }
        }
        
        stage('Deploy no Kubernetes') {
            steps {
                // Este é um passo de exemplo.
                // Em um cenário real, você faria o deploy em um servidor, Docker ou Kubernetes.
                sh 'echo "Execultando o comando kubectl apply"'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished!'
            // Limpa o workspace após a execução, independentemente do resultado
            deleteDir()
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
