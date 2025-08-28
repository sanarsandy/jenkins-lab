pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/sanarsandy/jenkins-lab.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("jenkins-lab:latest")
                }
            }
        }
        stage('Run Container') {
            steps {
                script {
                    sh 'docker stop flask-app'
                    sh 'docker rm flask-app'
                    sh 'docker run -d -p 5000:5000 --name flask-app jenkins-lab:latest'
                }
            }
        }
    }
}
