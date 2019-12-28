pipeline {
    agent any

triggers{
    pollSCM('H/15 * * * *')
    }
environment{
    branch = 'master'
    CID = '267219a0-9ba5-4f4d-a641-46d92b4b0bb5'
    giturl1 = 'https://github.com/nitishh35/simple-java-maven-app.git'
}    

    stages{

        stage('Checkout'){
            
            steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name:"${branch}"]], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: "${cid}", url: "${giturl1}"]]])
                }

            }    
        }
        stage('build'){
            tools{
                maven 'Maven 3.3.9'
                jdk   'jdk1.8.0'

            step{
                script{
                    bat "mvn clean compile test"
                }
            }    
            }            




        }


    }

}