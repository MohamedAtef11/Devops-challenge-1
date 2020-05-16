pipeline {
    agent any

    // environment {
    //     PATH = "$PATH:/usr/local/bin"
    //     }

    stages {
        stage('stage test') {
            steps {
                
                sh "python ./web/tests/test.py"
                

            }
        }
        stage('stage Copy ') {
            steps {
                // sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 ' mkdir /home/ec2-user/pro'"
                sh "sudo rsync -P -e 'ssh -i /home/matef/Downloads/dondon-monitor.pem' -r /var/lib/jenkins/workspace/test1/* ec2-user@3.21.162.162:/home/ec2-user/pro"
                // sh "sudo scp  -i /home/matef/Downloads/dondon-monitor.pem -r /var/lib/jenkins/workspace/test1/* ec2-user@3.21.162.162:/home/ec2-user/pro"
                sh "sudo scp  -i /home/matef/Downloads/dondon-monitor.pem -r /var/lib/jenkins/workspace/test1/.env ec2-user@3.21.162.162:/home/ec2-user/pro"

                
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 'ls /home/ec2-user/pro'"
                                
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 'cd /home/ec2-user/pro'"
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 'pwd'"
            }
        }
        stage('stage test2') {
            
            steps {
                sh "sudo ssh -tt -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 'python3 /home/ec2-user/pro/web/tests/test.py'"
            }
        }
        stage('stage build') {
            
            steps {
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 'cd /home/ec2-user/pro/'"
                sh "sudo ssh -tt -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 'sudo docker-compose -f /home/ec2-user/pro/docker-compose.yml  up --build '"
            }
        }
    }
}