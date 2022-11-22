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
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://13.126.28.219:8080/')], contextPath: 'qa236', war: '**/*.war'
            }
        }
     
        stage('deployprod') {
            
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://13.126.28.219:8080/')], contextPath: 'dev236', war: '**/*.war'
            }
        }
    }
    
    }
