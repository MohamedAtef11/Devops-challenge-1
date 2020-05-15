pipeline {
    agent any

    environment {
        PATH = "$PATH:/usr/local/bin"
        }

    stages {
        stage('stage one') {
            steps {
                
                echo "my son booooy "
            }
        }
        stage('stage two') {
            steps {
                sh "docker -v"
            }
        }
        stage('stage three') {
            
            steps {
                sh "docker-compose up --build"
            }
        }
    }
}