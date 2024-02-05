pipeline {
    agent any 

    environment {
        ENV_URL = 'pipeline.learning.com'
        SSH_CREDENTIALS = credentials('SSH_CRED')
    }

    triggers { pollSCM('*/1 * * * *') }

    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    
    stages {
        stage('stage name -1') {
            steps {
                sh "echo 'I am using pipeline syntax'"
                
            }
        }

        stage('stage name -2') {
            steps {
                sh "echo 'Printing the environment variable ${ENV_URL}'"
                sh 'env' // Command which prints existing environment variables
                
            }
        }

        stage('stage name -3') {
            environment {
                ENV_URL = 'stage.learning.com' // Declaring pipeline at stage level
            }
            steps {
                sh "echo 'Printing the environment variable ${ENV_URL}'"
                
            }
        }
    }
}
