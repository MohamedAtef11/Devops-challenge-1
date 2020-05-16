pipeline {
    agent any

    // environment {
    //     PATH = "$PATH:/usr/local/bin"
    //     }

    stages {
        stage('stage one') {
            steps {
                
                echo "test onlyyyyyyyyyyyyyyyyyyyyyyyyy "
                

            }
        }
        stage('stage Copy ') {
            steps {
                 sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 ' mkdir /home/ec2-user/pro'"

                sh "sudo scp  -i /home/matef/Downloads/dondon-monitor.pem -r /var/lib/jenkins/workspace/test1/* ec2-user@3.21.162.162:/home/ec2-user/pro"

                
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 'ls /home/ec2-user/pro'"
                                
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 'cd /home/ec2-user/pro'"
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 'pwd'"
            }
        }
        stage('stage test') {
            
            steps {
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162'python /home/ec2-user/pro/web/tests/test.py'"
            }
        }
        stage('stage build') {
            
            steps {
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162'sudo docker-compose up --build'"
            }
        }
    }
}