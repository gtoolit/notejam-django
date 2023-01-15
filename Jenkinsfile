pipeline{
    agent any

     environment {
        DOCKER_USER = credentials('docker_user')
        DOCKER_PSWD = credentials('docker_password')
    }

    stages{
        stage("Git Checkout"){
            steps{
                git branch: 'master', url: 'https://github.com/georgetoolit1/notejam-django.git'
            }
        }
        stage("Docker Image Build"){
            steps{
                script {
                    sh 'docker image build -t $JOB_NAME:v1.$BUILD_ID .'
                    sh 'docker image tag $JOB_NAME:v1.$BUILD_ID nevis256/$JOB_NAME:v1.$BUILD_ID'
                    sh 'docker image tag $JOB_NAME:v1.$BUILD_ID nevis256/$JOB_NAME:latest'
                }
            }
        }

        stage('Push Image to Dockerhub') {
            steps{
                script{
                    sh 'docker login -u ${DOCKER_USER} -p ${DOCKER_PSWD}'
                    sh 'docker image push nevis256/$JOB_NAME:v1.$BUILD_ID'
                    sh 'docker image push nevis256/$JOB_NAME:latest'
                }
            }
        }
    }
}