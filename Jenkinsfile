pipeline {
    agent any

    environment {
        // Docker Desktop default binary path for Windows
        PATH = "C:\\Program Files\\Docker\\Docker\\resources\\bin;${env.PATH}"
    }

    stages {

        stage('Environment Check') {
            steps {
                bat 'node --version'
                bat 'npm --version'
                bat 'docker --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm ci'
            }
        }

        stage('Test') {
            steps {
                bat 'npm test'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t nodejs-docker-devops:latest .'
            }
        }

        stage('Docker Run / Deploy') {
            steps {
                bat 'docker stop nodejs-app-container || exit 0'
                bat 'docker rm nodejs-app-container || exit 0'
                bat 'docker run -d -p 3000:3000 --name nodejs-app-container nodejs-docker-devops:latest'
            }
        }
    }
}