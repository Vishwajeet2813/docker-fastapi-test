pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/RohitPatil18/docker-fastapi-test.git'
            }
        }

        stage('Build & Deploy') {
            steps {
                sh '''
                docker-compose down || true
                docker-compose up -d --build
                '''
            }
        }
    }
}