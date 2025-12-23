pipeline {
    agent any

    environment {
        IMAGE_NAME = "simple-web:latest"
        CONTAINER_NAME = "simple-web-container"
        HOST_PORT = "8081"
        CONTAINER_PORT = "80"
    }

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Pulling code from GitHub'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image from Dockerfile'
                bat 'docker build -t %IMAGE_NAME% .'
            }
        }

        stage('Stop Old Container') {
            steps {
                echo 'Stopping old container if it exists'
                bat '''
                docker rm -f %CONTAINER_NAME% || exit 0
                '''
            }
        }

        stage('Run New Container') {
            steps {
                echo 'Running new Docker container'
                bat '''
                docker run -d -p %HOST_PORT%:%CONTAINER_PORT% --name %CONTAINER_NAME% %IMAGE_NAME%
                '''
            }
        }
    }

    post {
        success {
            echo 'Docker container deployed successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
