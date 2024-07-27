pipeline{
    agent any
    stages{
        stage("GIT checkout"){
            steps{
                git credentialsId: 'IAS-new', url: 'https://github.com/saikumar0503/project100.git'
                
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
            }
         }
    }
}
