pipeline {
    agent any 
    stages {
        stage ('stage name -1') {
            steps {
                sh "echo I am using pipeline syntax"
            }
        }

        stage ('stage name -2') {
            steps {
                sh "echo I am executing stage 2"
            }
        }

        stage ('stage name -3') {
            steps {
                sh '''
                echo I am using pipeline syntax
                echo demo to show multiple lines
                echo printing multiple lines with a single usage of sh command
                
                '''
            }
        }
    }
}
