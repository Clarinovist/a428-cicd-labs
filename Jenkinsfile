pipeline {
    agent none
    stages {
        stage('Start Containers') {
            steps {
                sh 'docker-compose up -d'
            }
        }
        stage('Build') {
            agent {
                docker {
                    image 'node:lts-buster-slim'
                    args '-p 3000:3000'
                }
            }
            steps {
                sh 'npm install'
            }
        }
        stage('Stop Containers') {
            steps {
                sh 'docker-compose down'
            }
        }
    }
}
