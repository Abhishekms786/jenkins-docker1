pipeline {
    agent any

    environment {
        IMAGE_NAME = "abhishekms2005/my-python-app"
        DOCKERHUB_CREDENTIALS = "a51ddc25ddd9445b89ab2e71609cbf7b"
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
