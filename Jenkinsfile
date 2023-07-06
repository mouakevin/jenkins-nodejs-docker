pipeline {
    agent any 

    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test'){
            steps{
                sh 'npm test'
            }
        }
        stage('Docker Build and Push') {
            steps {
                script {
                    dockerImage = docker.build("my-nodejs-app:latest")
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}

