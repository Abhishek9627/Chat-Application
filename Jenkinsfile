// pipeline {
//     agent any

//     environment {
//         DOCKER_COMPOSE = "/usr/local/bin/docker-compose"
//     }

//     stages {

//         stage('Checkout Code') {
//             steps {
//                 git branch: 'main',
//                     url: 'https://github.com/Abhishek9627/Chat-Application.git',
//                     credentialsId: 'github-token'
//             }
//         }

//         stage('Install Backend Dependencies') {
//             steps {
//                 sh """
//                 set -e
//                 echo "Installing Backend Dependencies..."
//                 cd backend
//                 npm install
//                 """
//             }
//         }

//         stage('Install Frontend Dependencies') {
//             steps {
//                 sh """
//                 echo "Installing Frontend Dependencies..."
//                 cd frontend
//                 npm install
//                 """
//             }
//         }

//         stage('Build Frontend') {
//             steps {
//                 sh """
//                 echo "Building React App..."
//                 cd frontend
//                 npm run build
//                 """
//             }
//         }

//         stage('Docker Compose Build & Deploy') {
//             steps {
//                 sh """
//                 echo "Stopping Old Containers..."
//                 ${DOCKER_COMPOSE} down || true

//                 echo "Building & Starting New Containers..."
//                 ${DOCKER_COMPOSE} up -d --build
//                 """
//             }
//         }
//     }

//     post {
//         always {
//             echo "Deployment Completed Successfully!"
//         }
//     }
// }
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

        stage('Check Tools') {
            steps {
                sh '''
                echo "Checking docker-compose..."
                ${DOCKER_COMPOSE} --version

                echo "Checking Node..."
                node -v

                echo "Checking npm..."
                npm -v
                '''
            }
        }

        stage('Install Backend Dependencies') {
            steps {
                sh '''
                set -e
                echo "Installing Backend Dependencies..."
                cd backend
                npm install
                '''
            }
        }

        stage('Install Frontend Dependencies') {
            steps {
                sh '''
                set -e
                echo "Installing Frontend Dependencies..."
                cd frontend
                npm install
                '''
            }
        }

        stage('Build Frontend') {
            steps {
                sh '''
                set -e
                echo "Building React App..."
                cd frontend
                npm run build
                '''
            }
        }

        stage('Docker Compose Build & Deploy') {
            steps {
                sh '''
                set -e
                echo "Stopping old containers..."
                ${DOCKER_COMPOSE} down || true

                echo "Building & starting new containers..."
                ${DOCKER_COMPOSE} up -d --build
                '''
            }
        }
    }

    post {
        success {
            echo "Deployment completed successfully."
        }
        failure {
            echo "Deployment failed. Check console output for errors."
        }
    }
}

