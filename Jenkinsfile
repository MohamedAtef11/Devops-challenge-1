pipeline {
    agent any

    environment {
        PATH = "$PATH:/usr/local/bin"
        }

    stages {
        stage('stage one') {
            steps {
                
                echo "my son booooy "
                sh "docker-compose -v"

            }
        }
        stage('stage two') {
            steps {
                sh "docker -v"
            }
        }
        stage('stage three') {
            
            steps {
                sh "sudo docker-compose up --build"
            }
        }
    }
}