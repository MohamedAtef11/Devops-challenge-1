pipeline {
    agent any

    stages {
        stage('stage one') {
            steps {
                
                echo "my son booooy 1"
            }
        }
        stage('stage two') {
            steps {
                echo "twoooooooooooooooo"
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