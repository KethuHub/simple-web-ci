pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/YOUR_USERNAME/simple-web-ci.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                echo 'Building project...'
                sh 'ls -l'
            }
        }

        stage('Test') {
            steps {
                echo 'No tests configured'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage completed'
            }
        }
    }
}
