pipeline {
    agent any

    stages {
        stage('Authentication') {
            steps {
                sh 'aws ecr get-login-password --region us-west-1 | docker login --username AWS --password-stdin 854171615125.dkr.ecr.us-west-1.amazonaws.com'


            }
        }
        stage('Build') {
            steps {
                 sh '''
                 echo 'build step'
                 cd yolo5

                 docker build -t sahil-jenkins .
                     '''

            }
        }
        stage('Push to ECR') {
            steps {
                 sh '''
                 echo 'build step'
                 docker tag sahil-jenkins:latest 854171615125.dkr.ecr.us-west-1.amazonaws.com/sahil-jenkins:${BUILD_NUMBER}
                    docker push 854171615125.dkr.ecr.us-west-1.amazonaws.com/sahil-jenkins:${BUILD_NUMBER}
                     '''
            }
        }
    }
}