pipeline {
    agent any
    environment{
        ECR_REPO = 'sahil-jenkins'
        ECR_URL='854171615125.dkr.ecr.us-west-1.amazonaws.com'
    }

    stages {
        stage('Authentication') {
            steps {
                sh 'aws ecr get-login-password --region us-west-1 | docker login --username AWS --password-stdin ${ECR_URL}'


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
                 docker tag sahil-jenkins:latest ${ECR_URL}/sahil-jenkins:${BUILD_NUMBER}
                    docker push ${ECR_URL}/${ECR_REPO}:${BUILD_NUMBER}
                     '''
            }
        }
            stage('Trigger Deploy') {
                steps {
                    build job: 'Yolo5Deploy', wait: false, parameters: [
                        string(name: 'YOLO5_IMAGE_URL', value: "854171615125.dkr.ecr.us-west-1.amazonaws.com/sahil-jenkins:${BUILD_NUMBER}")
                    ]
                }
            }


    }
}