pipeline {
    agent any

    environment {
        PATH = "$PATH:/usr/local/bin"
        }

    stages {
        
        stage('stage Test') {
            steps {
                sh "python ./web/tests/test.py"
            }
        }
        stage('stage Build') {
            
            steps {
                sh "sudo docker-compose up --build"
            }
        }
    }
}