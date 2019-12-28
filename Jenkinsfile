pipeline {
    agent any

triggers{
    pollSCM('H/15 * * * *')
    }

    stages{

        stage('Checkout'){
            
            steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '267219a0-9ba5-4f4d-a641-46d92b4b0bb5', url: 'https://github.com/nitishh35/simple-java-maven-app.git']]])
                }

            }    
        }

    }

}