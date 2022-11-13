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

         
        stage('build') {
            steps {
                sh 'mvn install'
                
            }
        }
        
     
        stage('depoytest') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://13.235.23.221:8080/')], contextPath: 'gametest11', war: '**/*.war'
            }
        }
       
        stage('deployprod') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://13.235.113.200:8080/')], contextPath: 'gameprod11', war: '**/*.war'
            }
        }
    }
    
    }




/*
 */
