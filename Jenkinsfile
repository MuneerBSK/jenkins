pipeline {
    agent any 

    environment {
        ENV_URL = "pipeline.learning.com"
        SSH_CREDENTIALS = credentials{'SSH_CRED'}
    }

    stages {

        stage ('stage name -1') {
            steps {
                sh "echo I am using pipeline syntax"
            }
        }

        stage ('stage name -2') {
            steps {
                sh "echo Printing the environment variable ${ENV_URL}"
                sh "env" //cmd which prints existing env variables
            }
        }

        stage ('stage name -3') {
            environment {
                        ENV_URL = "stage.learning.com" // declaring pipeline at stage level
                }
            steps {
  
            sh '''
                echo Printing the environment variable ${ENV_URL}
                
                '''
            }
        }
    }
}
