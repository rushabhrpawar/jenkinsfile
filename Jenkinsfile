pipeline{
    agent any
    tools {
        maven 'mavenBuild'
        jdk 'javaversion8'
        
    }
    stages{
        //  stage('git checking '){
        //     steps{ 
        //         sh '''
        //         git clone --branch jan-feb-2020 aurusgit@10.200.10.88:products/Java-AESDK/aurus-aesdk-service-enterprise/aurus-aesdk-service-enterprise.git
        //     '''            
        //     }
        // }
        stage("Maven testing stage "){
            steps{
                 sh "mvn --version"
                 emailext body: 'Checking mail by rushabh pawar to write jenkinsfile ', recipientProviders: [developers()], subject: '$BUILD_NUMBER - $BUILD_STATUS! Testing mail by RSP', to: 'rpawar@aurusinc.com'
                echo "========testing A========"
            }
            
        }
       
        stage("java version check"){
            steps{
                sh '''
                java -version
                '''
            }
            post{
                always{
                    echo "checking java version always"
                }
                success{
                    echo "java verion checking done successfully"
                }
                failure{
                    echo "java version not able to check please check properly "
                }
            }
        }   
        stage("Maven compile stage"){
           input {
            message "Should we continue ?"
            ok "yes we should "
           }
            steps{
                // sh '''
                // mvn compile && mvn test 
                
                // ''' 
                echo "========compile A========"
            }
        }
        stage("Maven build stage package"){
            steps{
                // sh ''' 
                //  mvn install 
                // '''
                
                echo "========building A========"
            }
        }
        stage("Deploy on server testing one "){
            steps{
                echo "========deploy on testing A========"
            }
        }
        stage("Deploy on prod server"){
            steps{
                echo "deploy on prod server"
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
