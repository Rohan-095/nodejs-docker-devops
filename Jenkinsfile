pipeline {
    agent any

    stages {
        stage('Environment Check') {
            steps {
                bat 'node --version'
                bat 'npm --version'
                bat 'docker --version'
            }
        }
    }
}