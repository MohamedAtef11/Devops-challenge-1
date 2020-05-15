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
            }
        }
        stage('stage three') {
            
            steps {
                sh "docker-compose up --build"
            }
        }
    }
}