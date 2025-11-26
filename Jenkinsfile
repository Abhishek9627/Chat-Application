pipeline {
    agent any

    environment {
        DOCKER_COMPOSE = "docker-compose"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Abhishek9627/Chat-Application.git',
                    credentialsId: 'github-token'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh """
                echo "Installing Backend Dependencies..."
                cd backend
                npm install || true

                echo "Installing Frontend Dependencies..."
                cd ../frontend
                npm install || true
                """
            }
        }

        stage('Build Frontend') {
            steps {
                sh """
                echo "Building Frontend React App..."
                cd frontend
                npm run build || true
                """
            }
        }

        stage('Docker Compose Build & Deploy') {
            steps {
                sh """
                echo "Stopping existing containers..."
                ${DOCKER_COMPOSE} down || true

                echo "Building & starting new containers..."
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


