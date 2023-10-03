pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                script {
                    def dockerImageName = 'utn-2023'
                    def dockerImageTag = 'v1'
                    // Showing Docker version
                    sh "docker --version"
                    sh "docker build -t ${dockerImageName}:${dockerImageTag} ."
                    // docker push using my credentials
                    withDockerRegistry([credentialsId: 'dockerhub', url: '']) {
                        sh "docker push ${dockerImageName}:${dockerImageTag}"
                        sh "docker push ${dockerImageName}:latest"
                    }
                }
            }
        }
    }
}