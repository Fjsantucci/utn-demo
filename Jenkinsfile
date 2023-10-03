pipeline {
  environment {
    registry = "blabir/utn-2023"
    registryCredential = 'dockerhub'
  }
  agent any
  stages {
    stage('Building image') {
      steps{
        script {
          echo "$registry"
          docker.build("blabir/utn-2023:$BUILD_NUMBER")
        }
      }
    }
  stage('Push image') {
    steps {
    script {
    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {            
    app.push("${env.BUILD_NUMBER}")            
    app.push("v1")        
            }
          }
         }    
        }
  }
}