pipeline {
    agent any

    environment {
        PATH = "$PATH:/usr/local/bin"
        }

    stages {
        stage('stage one') {
            steps {
                
                echo "my son booooy "
                sh "ls"

            }
        }
        stage('stage two') {
            steps {
                sh "python ./web/tests/test.py"
            }
        }
        stage('stage three') {
            
            steps {
                sh "sudo docker-compose up --build"
            }
        }
    }
}