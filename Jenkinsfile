pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Abhishek9627/Chat-Application.git', credentialsId: 'github-token'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                cd backend
                npm install

                cd ../frontend
                npm install
                npm run build
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                pm2 stop all || true

                cd backend
                pm2 start index.js --name backend

                cd ../frontend
                serve -s build -l 3000 || true
                '''
            }
        }
    }
}
