pipeline {
    agent any
	

 stages {
      stage('checkout') {
           steps {
             
                git branch: 'main', url: 'https://github.com/mickymikun/devops-practical-2.git'
             
          }
        }
       

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t jdk_mvn:latest .' 
                sh 'docker tag jdk_mvn 8249355606/jdk_mvn:$BUILD_NUMBER'
               
          }
        }
  stage('Publish image to Docker Hub') {
            steps {
        withDockerRegistry([ credentialsId: "DockerHub", url: "" ]) {
           sh  'docker push 8249355606/jdk_mvn:$BUILD_NUMBER' 
		}
                  
          }
        }
		
    }
}
