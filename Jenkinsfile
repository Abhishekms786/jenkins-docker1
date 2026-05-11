pipeline {
    agent any

    environment {
        IMAGE_NAME = "abhishekms2005/my-python-app"
        DOCKERHUB_CREDENTIALS = "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"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/abhishekms786/jenkins-docker1.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build --no-cache -t ${IMAGE_NAME}:latest ."
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
