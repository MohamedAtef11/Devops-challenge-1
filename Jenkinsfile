pipeline {
    agent any

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
        stage('Build and push images ') {
            steps {
                sh "sudo docker login -u '$Dockerhub_username' -p '$Dockerhub_password'"

                sh "sudo docker build -t muhammadatef/project-nginx:latest -t muhammadatef/project-nginx:\$(git rev-parse HEAD) -f ./nginx/Dockerfile ./nginx"
                sh "sudo docker push muhammadatef/project-nginx:latest" 
                sh "sudo docker push muhammadatef/project-nginx:\$(git rev-parse HEAD)" 

                sh "sudo docker build -t muhammadatef/project-web:latest -t muhammadatef/project-web:\$(git rev-parse HEAD) -f ./web/Dockerfile ./web"
                sh "sudo docker push muhammadatef/project-web:latest" 
                sh "sudo docker push muhammadatef/project-web:\$(git rev-parse HEAD)" 

                
            }
        }

         stage('copy docker-compose file to AWS server') {
            
            steps {
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.22.235.5 '[ ! -d '/home/ec2-user/pro' ] && mkdir /home/ec2-user/pro;echo Directory-exist'"
                sh "sudo scp  -i /home/matef/Downloads/dondon-monitor.pem -r /var/lib/jenkins/workspace/test1/.env ec2-user@3.22.235.5:/home/ec2-user/pro"
                sh "sudo scp  -i /home/matef/Downloads/dondon-monitor.pem -r /var/lib/jenkins/workspace/test1/docker-compose.yml ec2-user@3.22.235.5:/home/ec2-user/pro"
                sh "sudo scp  -i /home/matef/Downloads/dondon-monitor.pem -r -p /var/lib/jenkins/workspace/test1/web/static/ ec2-user@3.22.235.5:/home/ec2-user/pro"
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