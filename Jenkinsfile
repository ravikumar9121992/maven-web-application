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
        stage('depoytest') {
            
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://3.109.60.248:8080/')], contextPath: 'qa237', war: '**/*.war'
            }
        }
     
        stage('deployprod') {
            
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://52.66.195.125:8080/')], contextPath: 'dev237', war: '**/*.war'
            }
        }
    }
    
    }
