pipeline {
    agent any

    // environment {
    //     PATH = "$PATH:/usr/local/bin"
    //     }

    stages {
        stage('stage one') {
            steps {
                
                echo "my son booooy "
                // sh "scp -r ./* ec2-user@3.21.162.162:/"
                sh "ls"
                sh " pwd"

            }
        }
        stage('stage two') {
            steps {
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 'ls '"
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 'pwd'"
            }
        }
        // stage('stage three') {
            
        //     steps {
        //         sh "python ./web/tests/test.py"
        //         sh "sudo docker-compose up --build"
        //     }
        // }
    }
}