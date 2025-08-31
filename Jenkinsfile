pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    dockerapp = docker.build("josemarcosrt/gruia-jenkins:${env.BUILD_ID}","-f ./src/Docker")
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    dockerapp.withRegistry('https://registry.hub.docker.com', 'dockerhub')
                    dockerapp.push("latest")
                    dockerapp.push("${env.BUILD_ID}")
                }
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Este é um passo de exemplo.
                // Em um cenário real, você faria o deploy em um servidor, Docker ou Kubernetes.
                sh 'echo "Deployment script here..."'
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
