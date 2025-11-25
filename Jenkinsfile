pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Abhishek9627/Chat-Application.git',
                    credentialsId: 'github-token'
            }
        }

        stage('Build & Deploy with Docker Compose') {
            steps {
                sh """
                echo "Stopping existing containers..."
                docker-compose down || true

                echo "Building and starting new containers..."
                docker-compose up -d --build
                """
            }
        }
    }

    post {
        always {
            echo "Deployment Completed Successfully!"
        }
    }
}
