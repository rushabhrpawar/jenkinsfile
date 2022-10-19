pipeline {
    agent any 


    tools {
         jdk 'java8'
         maven 'mavenBuild'
    }
    stages {
        stage("checking version of java and maven via commnad line "){
            steps{
                sh '''
                mvn -version 
                java -version
                '''
            }
        }
        stage("Cloning the git project "){
            steps{
                git branch: '*/jan-feb-2020', url: 'aurusgit@10.200.10.88:products/Java-AESDK/aurus-aesdk-service-enterprise/aurus-aesdk-service-enterprise.git'
            }
        }
        stage("mvn clean compile and test stage"){
            steps{
                sh '''
                cd aurus-aesdk-service-enterprise/
                mvn clean 
                mvn compile 
                mvn test 
                '''
            }
        }
    }
}
