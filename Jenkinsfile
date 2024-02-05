pipeline {
    agent any 

    environment {
        ENV_URL = "pipeline.learning.com"
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
                
            }
        }

        stage ('stage name -3') {
            steps {
                    environment {
                        ENV_URL = "pipeline.learning.com"
                    }
            sh '''

                echo I am using pipeline syntax
                echo demo to show multiple lines
                echo printing multiple lines with a single usage of sh command
                
                '''
            }
        }
    }
}
