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
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://13.127.132.149:8080/')], contextPath: '/apps', war: '**/*.war'
            }
        }
        stage('deployprod') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'adminid', path: '', url: 'http://3.110.193.22:8080/')], contextPath: '/prod', war: '**/*.war'
            }
        }
    }
    
    post{
        always{
            echo "always"
        }
        success{
            echo "success"
        }
        failore{
            echo "failore"
        }
    }
}
