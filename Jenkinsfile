pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myflaskimage .'
            }
        }
        stage('Run Container') {
            steps {
                sh '''
                  docker rm -f myflaskimage-container || true
                  docker run -d --name myflaskimage-container -p 8082:5000 myflaskimage
                '''
            }
        }
    }
}