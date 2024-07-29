pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockercrd') // Jenkins credentials ID for Docker Hub
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/neel52700/Day_15.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    docker.build('neelpatel5270/day_15:latest')
                }
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
                // Add your test commands here
            }
        }
        stage('Push') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockercrd') {
                        docker.image('neelpatel5270/day_15:latest').push()
                    }
                }
            }
        }
    }
}
