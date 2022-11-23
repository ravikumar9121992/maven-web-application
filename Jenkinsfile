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
                 sh 'docker run -itd --name RAVIBABU -p 281:8080 tomcat:${BUILD_NUMBER}'
             }
         }
        stage('Push Docker Image'){
             steps{
                  withCredentials([usernameColonPassword(credentialsId: 'DOCKER_HUB_CREDENTIALS2', variable: 'DOCKER_HUB_CREDENTIALS')]) {
                      sh "docker login -u awsdocker123456789 -p ${DOCKER_HUB_CREDENTIALS2}"
            }
            sh 'docker push awsdocker123456789/spring-boot-mongo'
        }
      }
        
        
    }
}
