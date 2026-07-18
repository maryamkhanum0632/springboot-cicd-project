pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Repository already checked out by Jenkins'
            }
        }

        stage('Build') {
            steps {
                sh 'chmod +x mvnw'
                sh './mvnw clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t springboot-cicd-project:latest .'
            }
        }
    }
}