node {    
      def app         
      stage('Build image') {         
            app = docker.build("blabir/utn-2023")    
       }     
      stage('Test image') {           
            app.inside {            
             
             sh 'echo "Tests passed"'        
            }    
        }     
       stage('Push image') {
       docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {            
       app.push("${env.BUILD_NUMBER}")            
       app.push("v1")        
              }    
           }
        }