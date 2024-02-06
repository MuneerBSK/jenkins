pipeline {
    agent any 

    environment {
        ENV_URL = "pipeline.learning.com"
        SSH_CREDENTIALS = credentials('SSH_CRED')
    }

    stages {
        stage('stage name -1') {
            steps {
                sh "echo 'I am using pipeline syntax'"
                // Add more steps for stage name -1 if needed
            }
        }

        stage('stage name -2') {
            steps {
                sh "echo 'Printing the environment variable ${ENV_URL}'"
                sh "env" // Command which prints existing environment variables
                // Add more steps for stage name -2 if needed
            }
        }

        stage('Stage Name - 3') {
            environment {
                ENV_URL = "stage.learning.com" // Declaring pipeline at stage level
            }
            steps {
                sh '''
                    echo 'I am using Pipeline Syntax Help'
                    echo 'demo to show multiple lines'
                    echo 'Printing multiple lines with a single usage of sh command'
                    echo 'Printing the environment variable ${ENV_URL}'
                '''
            }
        }

    }
}
