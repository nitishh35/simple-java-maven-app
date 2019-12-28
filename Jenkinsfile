pipeline {
    agent any

triggers{
    pollSCM('H/15 * * * *')
    }

options {
  buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '7', numToKeepStr: '10')
}
environment{
    branch = 'master'
    CID = '267219a0-9ba5-4f4d-a641-46d92b4b0bb5'
    giturl1 = 'https://github.com/nitishh35/simple-java-maven-app.git'
    junitreportpath = 'target/surefire-reports'
}    

    stages{

        stage('Checkout'){
            
            steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: "${branch}"]], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'Java-Maven']], submoduleCfg: [], userRemoteConfigs: [[credentialsId: "${cid}", url: "${giturl1}"]]])
                }

            }    
        post {
            failure {
            echo "print failure"
            }
        }
        }
        stage('build'){
            tools{
                maven 'Maven 3.3.9'
                jdk   'jdk1.8.0'
            }

            steps {
                script {
                    milestone 1
                    bat "mvn clean compile test"
                }
            }             
        }

        stage('Unit testing'){  
            steps{
                milestone 2
                junit "${junitreportpath}/**/*.xml"
            }
        }   
    }

}


