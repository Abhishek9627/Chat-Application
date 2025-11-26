pipeline {
    agent any

    environment {
        DOCKER_COMPOSE = "/usr/local/bin/docker-compose"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Abhishek9627/Chat-Application.git',
                    credentialsId: 'github-token'
            }
        }

        stage('Install Backend Dependencies') {
            steps {
                sh """
                echo "Installing Backend Dependencies..."
                cd backend
                npm install
                """
            }
        }

        stage('Install Frontend Dependencies') {
            steps {
                sh """
                echo "Installing Frontend Dependencies..."
                cd frontend
                npm install
                """
            }
        }

        stage('Build Frontend') {
            steps {
                sh """
                echo "Building React App..."
                cd frontend
                npm run build
                """
            }
        }

        stage('Docker Compose Build & Deploy') {
            steps {
                sh """
                echo "Stopping Old Containers..."
                ${DOCKER_COMPOSE} down || true

                echo "Building & Starting New Containers..."
                ${DOCKER_COMPOSE} up -d --build
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
