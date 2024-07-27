pipeline {
    agent any 

    tools {
        maven 'Maven 3.6.3' // Replace with your Maven version
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the specified repository
                git 'https://github.com/saikumar0503/project100.git'
            }
        }

        stage('Build') {
            steps {
                // Run Maven build
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run Maven tests
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                // Package the application (optional)
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the application (optional)
                sh 'mvn deploy'
            }
        }
    }

    post {
        success {
            echo 'Build and tests succeeded!'
        }

        failure {
            echo 'Build or tests failed.'
        }
    }
}
