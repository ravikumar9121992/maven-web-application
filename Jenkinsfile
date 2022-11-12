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
        stage('ExecuteSonarQubeReport'){
  steps{
  sh  "mvn clean sonar:sonar"
  }
  }
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
        stage('depoytest') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://43.205.195.71:8080/')], contextPath: 'gametest', war: '**/*.war'
            }
        }
       
        stage('deployprod') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://13.127.115.88:8080/')], contextPath: 'gameprod', war: '**/*.war'
            }
        }
    }
    
    }
