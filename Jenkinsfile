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
                sh "export DOCKER_HOST=127.0.0.1"
                sh "/usr/local/bin/docker-compose up --build"
            }
        }
    }
}