pipeline {
    agent any
    tools {
        maven 'Maven'
        
    }
    
    stages {
       
      stage('Build'){
  steps{
  sh  "mvn clean package"
  }
      }
        
 stage('SonarQubeReport'){
  steps{
  sh  "mvn clean sonar:sonar"
  }
  }
      
        /*stage('test') {
            steps {
                sh 'mvn test'
            }
        }
         
        stage('build') {
            steps {
                sh 'mvn install'
                
            }
        }*/
        stage('depoytest') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://13.235.23.221:8080/')], contextPath: 'gametest1', war: '**/*.war'
            }
        }
       
        stage('deployprod') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://13.235.113.200:8080/')], contextPath: 'gameprod1', war: '**/*.war'
            }
        }
    }
    
    }
