pipeline {
    agent any

    environment {
        IMAGE_NAME = "abhishekms786/my-python-app"
        DOCKERHUB_CREDENTIALS = "dockerhub-creds"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/abhishekms786/jenkins-docker1.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:latest")
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('', DOCKERHUB_CREDENTIALS) {
                        docker.image("${IMAGE_NAME}:latest").push()
                    }
                }
            }
        }
    }
}
