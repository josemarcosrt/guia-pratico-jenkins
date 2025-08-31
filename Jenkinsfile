pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                // Exemplo: `git checkout`
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                // Assume que o projeto tem um pom.xml
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Assume que os testes estão configurados com Maven
                sh 'mvn test'
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
