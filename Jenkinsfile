pipeline{
    agent any
    
    environment{
        PATH = "/opt/maven3/bin:$PATH"
    }
    stages{
        stage("Git Checkout"){
            steps{
                git credentialsId: 'IAS-new', url: 'https://github.com/saikumar0503/project100.git'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
                sh "mv target/*.jar target/myweb.war"
            }
        }
        stage("deploy-dev"){
            steps{
                sshagent(['IAS-one']) {
                sh """
                    scp -o StrictHostKeyChecking=no target/myweb.war  ec2-user@172.16.10.244:/opt/tomcat/webapps/
                    
                    ssh ec2-user@172.16.10.244 /opt/tomcat/bin/shutdown.sh
                    
                    ssh ec2-user@172.16.10.244 /opt/tomcat/bin/startup.sh
                
                """
            }
            
            }
        }
    }
}
