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
        
        stage('Build') {
              steps {
      
                  sh  'mvn clean package'
      
                 }
                   }
        
        stage('ExecuteSonarQubeReport') {
            
                 steps {
      
                     sh  'mvn clean sonar:sonar'
      
                    }
                       }
        
        stage('UploadArtifactsIntoNexus'){
  steps{
  sh  "mvn clean deploy"
  }
  }
     
        stage('depoytest') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://65.0.12.177:8080/')], contextPath: 'qa1', war: '**/*.war'
            }
        }
       
        stage('deployprod') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://43.205.114.82:8080/')], contextPath: 'dev1', war: '**/*.war'
            }
        }
    }
    
    }

