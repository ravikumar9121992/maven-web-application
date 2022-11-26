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
                sh 'mvn install package'
                
            }
        }
*/
    
       
 stage("Maven Build"){
            steps{
                sh "mvn clean package sonar:sonar"
                
            }
        }
        stage('Upload War To Nexus'){
            steps{
                  nexusArtifactUploader artifacts: [
                       [
                            artifactId: 'maven-web-application', 
                            classifier: '', 
                            file: "target/maven-wen-application-8.2.0.war", 
                            type: 'war'
                       ]
                  ], 
                  credentialsId: 'nexus3', 
                  groupId: 'in.javahome', 
                  nexusUrl: '172.31.4.63:8081', 
                  nexusVersion: 'nexus3', 
                  protocol: 'http', 
                  repository: 'sample-releases', 
                  version: '8.2.0'  
              }
            }

stage('Build Docker Image'){
            steps{
                 sh 'docker build -t awsdocker123456789/spring-boot-mongo .'
                 sh 'docker build -t awsdocker123456789/qc .'
                 sh 'docker build -t awsdocker123456789/qa .'
                 sh 'docker build -t awsdocker123456789/dev .'
                 sh 'docker build -t awsdocker123456789/prod .'
                 sh 'docker build -t tomcat:${BUILD_NUMBER} .'
                 sh 'docker run -itd --name ramji -p 457:8080 tomcat:${BUILD_NUMBER}'

             }
         }
        stage('Push Docker Image'){
             steps{
                     withCredentials([usernamePassword(credentialsId: 'DOCKER_HUB_CREDENTIALSi', passwordVariable: 'DOCKER_HUB_CREDENTIALSp', usernameVariable: 'DOCKER_HUB_CREDENTIALSu')]) {

                         sh "docker login -u awsdocker123456789 -p ${DOCKER_HUB_CREDENTIALSp}"
            }
            sh 'docker push awsdocker123456789/spring-boot-mongo'
            sh 'docker push awsdocker123456789/qa'
            sh 'docker push awsdocker123456789/qc'
            sh 'docker push awsdocker123456789/dev'
            sh 'docker push awsdocker123456789/prod'
        }
      }
        
        
    }
}
