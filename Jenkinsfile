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
        /* 
        stage('depoytest') {
            
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://3.109.60.248:8080/')], contextPath: 'qa237', war: '**/*.war'
            }
        }*/
/*
        stage('deployprod') {
            
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://52.66.195.125:8080/')], contextPath: 'dev237', war: '**/*.war'
            }
        }
    }
    
    }*/


stage('Build Docker Image'){
            steps{
                 sh 'docker build -t awsdocker123456789/spring-boot-mongo .'
                 sh 'docker build -t tomcat:${BUILD_NUMBER} .'
                 sh 'docker run -itd --name tomcatravi -p 2900:8080 tomcat:${BUILD_NUMBER}'
             }
         }
        stage('Push Docker Image'){
             steps{
                  withCredentials([usernameColonPassword(credentialsId: 'DOCKER_HUB_CREDENTIALS', variable: 'DOCKER_HUB_CREDENTIALS')]) {
                      sh "docker login -u awsdocker123456789 -p ${DOCKER_HUB_CREDENTIALS}"
            }
            sh 'docker push awsdocker123456789/spring-boot-mongo'
        }
      }
        
        
    }
}
