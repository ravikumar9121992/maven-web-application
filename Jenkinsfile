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
                sh 'mvn install'
                
            }
        }

         
        
        
 /* 
 stage('SonarQube'){
   steps{
      sh  "mvn clean sonar:sonar package"
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
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://43.205.206.231:8080/')], contextPath: 'qaaa', war: '**/*.war'
            }
        }
     
        stage('deployprod') {
            
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://65.2.151.116:8080/')], contextPath: 'devvv', war: '**/*.war'
            }
        }
    }
    
    }
