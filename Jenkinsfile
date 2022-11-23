pipeline {
    agent any
    tools {
        maven 'Maven'
        
    }
    
    stages { 

    
        stage('test') {
            steps {
                sh 'mvn test'
            }
        }
        
        
         stage('build') {
            steps {
                sh 'mvn install package'
                
            }
        }

    
   /*     
 stage('Build'){
  steps{
   sh  "mvn clean package"
  }
  }    
 
 stage('SonarQube'){
   steps{
      sh  "mvn clean sonar:sonar"
  }
    }
  
  stage('nexus'){
    steps{
         sh  "mvn clean deploy"
 }
   }
  */    

stage('Build Docker Image'){
            steps{
                 sh 'docker build -t awsdocker123456789/spring-boot-mongo .'
                 sh 'docker build -t tomcat:${BUILD_NUMBER} .'
                 sh 'docker run -itd --name tomcatravi -p 558:8080 tomcat:${BUILD_NUMBER} .'
             }
         }
        
        
        
    }
}

