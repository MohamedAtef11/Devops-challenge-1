pipeline {
    agent any

    // environment {
    //     PATH = "$PATH:/usr/local/bin"
    //     }

    stages {
        stage('Build local') {
            steps {
                sh "sudo docker build -t build-web:1.0 ./web"
            }
        }
        stage('Test') {
            steps {
                sh "sudo docker run build-web:1.0 python tests/test.py "
            }
        }
        stage('Copy project to server') {
            steps {
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.22.235.5 '[ ! -d '/home/ec2-user/pro' ] && mkdir /home/ec2-user/pro;echo Directory-exist'"
                sh "sudo rsync -P -e 'ssh -i /home/matef/Downloads/dondon-monitor.pem' -r /var/lib/jenkins/workspace/test1/* ec2-user@3.22.235.5:/home/ec2-user/pro"
                sh "sudo scp  -i /home/matef/Downloads/dondon-monitor.pem -r /var/lib/jenkins/workspace/test1/.env ec2-user@3.22.235.5:/home/ec2-user/pro"
                
            }
        }
        
        stage('Deploy on AWS server') {
            
            steps {
                sh "sudo ssh -tt -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.22.235.5 'sudo docker-compose -f /home/ec2-user/pro/docker-compose.yml  down'"
                sh "sudo ssh -tt -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.22.235.5 'sudo docker-compose -f /home/ec2-user/pro/docker-compose.yml  up --build '"
            }
        }
    }
}