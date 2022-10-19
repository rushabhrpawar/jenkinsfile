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
    }
}
