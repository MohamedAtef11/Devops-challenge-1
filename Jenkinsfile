pipeline {
    agent any

    // environment {
    //     PATH = "$PATH:/usr/local/bin"
    //     }

    stages {
        stage('stage one') {
            steps {
                
                echo "my son booooy "
                

            }
        }
        stage('stage two') {
            steps {
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 ' mkdir /home/ec2-user/pro'"

                sh "sudo ssh -tt -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 'scp -r /var/lib/jenkins/workspace/test1/* /home/ec2-user/pro'"

                
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 'ls /home/ec2-user/pro'"
                                
                sh "sudo ssh -i /home/matef/Downloads/dondon-monitor.pem ec2-user@3.21.162.162 'cd /home/ec2-user/pro'"
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