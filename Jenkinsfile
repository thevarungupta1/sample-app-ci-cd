pipeline {
    agent any

    stages{
        stage('Checkout') {
            steps {
                git 'https://github.com/thevarungupta1/sample-app-ci-cd.git'
            }
        }

        stage('Docker Build'){
            steps {
                bat 'docker build -t web-app:latest .'
            }
        }

        stage('Deploy'){
            steps {
                bat '''
                  docker stop web-app || exit 0
                  docker rm web-app || exit 0
                  docker run -d -p 3000:3000 --name web-app web-app:latest
                '''
            }
        }
    }
}