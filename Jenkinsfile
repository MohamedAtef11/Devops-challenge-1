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
                // sh "sudo ssh -tt -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162"
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