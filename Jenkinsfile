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
        stage('depoytest') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://43.205.94.216:8080/')], contextPath: 'gametest', war: '**/*.war'
            }
        }
        stage('deployprod') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://13.126.29.15:8080/')], contextPath: 'gameprod', war: '**/*.war'
            }
        }
    }
    
    }
