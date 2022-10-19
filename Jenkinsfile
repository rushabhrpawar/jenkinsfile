pipeline {
    agent any 


    tools {
         jdk 'java8'
         maven 'mavenBuild'
    }
    stages {
        stage("checking version of java and maven via commnad line "){
            steps{
                emailext attachLog: true, body: 'Build has been started by user ', recipientProviders: [developers()], subject: '$BUILD_NUMBER - $BUILD_STATUS! Building started ', to: 'rpawar@aurusinc.com'
                sh '''
                mvn -version 
                java -version
                '''
            }
        }
        stage("Cloning the git project "){
            steps{
                git branch: 'jan-feb-2020', url: 'aurusgit@10.200.10.88:products/Java-AESDK/aurus-aesdk-service-enterprise/aurus-aesdk-service-enterprise.git'
            }
        }
        stage("mvn clean compile and test stage"){
            steps{
                sh '''
                mvn clean 
                mvn compile 
                mvn test 
                '''
            }
        }
        stage("mvn build stage"){
            input {
                    message "can we start build"
                    ok "yes we can start"
                }
            steps{
                sh '''
                mvn package
                '''
                emailext attachLog: true, attachmentsPattern: '**target/aurus-aesdk-service*', body: 'Build has been successfully completed  ', postsendScript: '**target/aurus-aesdk-service*', recipientProviders: [developers()], subject: '$BUILD_NUMBER - $BUILD_STATUS! Building started ', to: 'rpawar@aurusinc.com'
            }
        }
    }
}
