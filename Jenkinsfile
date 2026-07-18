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

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f springboot-app || true
                docker run -d \
                  --name springboot-app \
                  -p 8083:8082 \
                  springboot-cicd-project:latest
                '''
            }
        }
    }
}