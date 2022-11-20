pipeline {
    agent any
    tools {
        maven 'Maven'
        
    }
    
    stages { 

    /*  
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

         
        */
        

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
     
        stage('depoytest') {
            
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://13.126.36.84:8080/')], contextPath: 'qaa', war: '**/*.war'
            }
        }
       
        stage('deployprod') {
            
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://3.110.85.168:8080/')], contextPath: 'devv', war: '**/*.war'
            }
        }
    }
    
    }

