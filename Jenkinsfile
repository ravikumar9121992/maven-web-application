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
                deploy adapters: [tomcat9(credentialsId: 'appid', path: '', url: 'http://43.205.237.31:8080/')], contextPath: 'apps', war: '**/*.war'
            }
        }
        stage('deployprod') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'appid', path: '', url: 'http://35.154.76.84:8080/')], contextPath: 'prods', war: '**/*.war'
            }
        }
    }
    
    }
