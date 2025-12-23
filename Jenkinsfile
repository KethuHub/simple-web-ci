pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub'
                checkout scm
            }
        }

        stage('Verify Files') {
            steps {
                echo 'Listing workspace files'
                bat 'dir'
            }
        }

        stage('Deploy to IIS') {
            steps {
                echo 'Deploying index.html to IIS'
                bat '''
                copy /Y "%WORKSPACE%\\index.html" "C:\\inetpub\\wwwroot\\index.html"
                '''
            }
        }
    }

    post {
        success {
            echo 'Deployment completed successfully'
        }
        failure {
            echo 'Deployment failed'
        }
    }
}
