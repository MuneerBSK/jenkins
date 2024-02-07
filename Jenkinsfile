pipeline {
    agent { label 'ws' }

    environment {
        ENV_URL = 'pipeline.learning.com'
        SSH_CREDENTIALS = credentials('SSH_CRED')
    }

    tools {
        maven 'maven-3.9.6' 
    }

    stages {

        stage('Example on parallel stages') {
            parallel {
                stage('One') {
                    steps {
                        sh "ifconfig"
                        sh "echo STAGE ONE"
                        sh "sleep 5"
                    }
                }
                stage('Two') {
                    steps {
                        sh "echo STAGE TWO"
                        sh "sleep 5"
                    }
                }
                stage('Three') {
                    steps {
                        sh "echo STAGE THREE"
                        sh "sleep 5"
                    }
                }
            }
        }

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
            when {
                branch 'dev'
            }
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
