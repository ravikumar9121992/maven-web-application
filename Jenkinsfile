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
        
        */
        
     
        stage('depoytest') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://13.235.23.221:8080/')], contextPath: 'qa', war: '**/*.war'
            }
        }
       
        stage('deployprod') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://13.235.113.200:8080/')], contextPath: 'dev', war: '**/*.war'
            }
        }
    }
    
    }

