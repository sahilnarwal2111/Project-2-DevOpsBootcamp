pipeline {
    agent any

    stages {
        stage('Authentication') {
            steps {
                sh 'echo building...'
                sh 'echo building...'
                sh 'echo building...'
                sh 'echo building...'
                sh 'echo building...'

            }
        }
        stage('Build') {
            steps {
                 sh '''
                 echo 'build step'
                 cd yolo5
                 aws ecr get-login-password --region eu-north-1 | docker login --username AWS --password-stdin 854171615125.dkr.ecr.eu-north-1.amazonaws.com                docker build -t sahil-jenkins:$BUILD_TAG .
                docker tag sahil-jenkins:latest 854171615125.dkr.ecr.eu-north-1.amazonaws.com/sahil-jenkins:$BUILD_TAG
                docker push 854171615125.dkr.ecr.eu-north-1.amazonaws.com/sahil-jenkins:$BUILD_TAG

                     '''

            }
        }
        stage('Push to ECR') {
            steps {
                sh 'echo building...'
                sh 'echo building...'
                sh 'echo building...'
                sh 'echo building...'
                sh 'echo building...'
            }
        }
    }
}