// pipeline {
//     agent any

//     stages {
//         stage('Checkout Code') {
//             steps {
//                 git branch: 'main',
//                     url: 'https://github.com/Abhishek9627/Chat-Application.git',
//                     credentialsId: 'github-token'
//             }
//         }

//         stage('Build & Deploy with Docker Compose') {
//             steps {
//                 sh """
//                 echo "Stopping existing containers..."
//                 docker-compose down || true

//                 echo "Building and starting new containers..."
//                 docker-compose up -d --build
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
        // Define Docker Compose command path if not in PATH environment.
        // For example, if docker-compose is installed at /usr/local/bin/docker-compose, set below:
        // DOCKER_COMPOSE = "/usr/local/bin/docker-compose"
        // If docker-compose is directly accessible, you can omit this or set as "docker-compose"
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

        stage('Build & Deploy with Docker Compose') {
            steps {
                sh """
                echo "Stopping existing containers..."
                ${DOCKER_COMPOSE} down || true

                echo "Building and starting new containers..."
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
