pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t kesariakshitha/devops-demo-app .'
            }
        }
        stage('Push Docker Image') {
    steps {
        withCredentials([usernamePassword(credentialsId: 'DOCKER_HUB', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
            sh 'docker login -u $USERNAME -p $PASSWORD'
            sh 'docker push kesariakshitha/devops-demo-app:latest'
        }
    }
}
    }
}
