pipeline {
    agent any

    stages {
        stage('stage gd3na mny kda') {
            steps {
                sh 'ls' 
            }
        }
        stage('Test') {
            def testResult = ... // run command executing tests
            if (testResult == 'Failed') {
                error "test failed"
            }
        }

        stage('Build') {
            sh 'docker-compose up --build' 
        }
    }
}