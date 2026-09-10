pipeline {
    agent any

    stages {

        stage('Environment Check') {
            steps {
                bat 'node --version'
                bat 'npm --version'
                bat '"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker.exe" --version'
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
                bat '"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker.exe" build -t nodejs-docker-devops:latest .'
            }
        }

        stage('Docker Run / Deploy') {
            steps {
                bat '"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker.exe" stop nodejs-app-container || exit 0'
                bat '"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker.exe" rm nodejs-app-container || exit 0'
                bat '"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker.exe" run -d -p 3000:3000 --name nodejs-app-container nodejs-docker-devops:latest'
            }
        }
    }
}