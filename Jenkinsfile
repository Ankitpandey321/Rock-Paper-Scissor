pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/Ankitpandey321/Rock-Paper-Scissor.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t rps-game:latest .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop rps || true'
                sh 'docker rm rps || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 8081:80 --name rps rps-game:latest'
            }
        }
    }
}
