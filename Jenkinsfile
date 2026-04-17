pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Vishwajeet2813/docker-fastapi-test.git'
            }
        }

        stage('Build & Deploy') {
            steps {
                bat '''
                cd "D:\\DovOps Fastapi project\\docker-fastapi-test"
                docker compose down
                docker compose up -d --build
                '''
            }
        }
    }
}