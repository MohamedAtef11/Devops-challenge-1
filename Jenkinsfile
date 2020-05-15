pipeline {
    agent any

    environment {
        PATH = "$PATH:/usr/bin"
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
                sh "ssh -tt ec2-user@3.21.162.162"
                sh "ls /"
            }
        }
        stage('stage three') {
            
            steps {
                sh "sudo docker-compose up --build"
            }
        }
    }
}