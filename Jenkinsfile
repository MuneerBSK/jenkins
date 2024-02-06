pipeline {
    agent any 

    environment {
        ENV_URL = 'pipeline.learning.com'
        SSH_CREDENTIALS = credentials('SSH_CRED')
    }

z

    // parameters {
    //     string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
    //     text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
    //     booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
    //     choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    //     password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    // }
    
    tools {
        maven 'maven-3.9.6' 
    }

    stages {

        stage('Example on parallel stages') {
            parallel {
                stage('One') {
                    steps {
                        sh "echo STAGE ONE"
                        sh "sleep 100"
                    }
                }
                stage('Two') {
                    steps {
                        sh "echo STAGE TWO"
                        sh "sleep 100"
                    }
                }
                stage('Three') {
                    steps {
                        sh "echo STAGE THREE"
                        sh "sleep 100"
                    }
                }
            }
        }


    stages {

        stage('Testing mvn commands') {
            steps {
                sh "mvn --version"
            }
        }

        stage('stage name -1') {
            steps {
                sh "echo 'I am using pipeline syntax'"
                
            }
        }

        stage('stage name -2') {
            when {branch 'dev'}
            steps {
                sh "echo 'Printing the environment variable ${ENV_URL}'"
                sh 'env' // Command which prints existing environment variables
                
            }
        }

        stage('Final stage needs attention') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            environment {
                ENV_URL = 'stage.learning.com' // Declaring pipeline at stage level
            }
            steps {
                sh "echo 'Printing the environment variable ${ENV_URL}'"
                
            }
        }
    }
}
