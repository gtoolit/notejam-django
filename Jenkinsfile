pipeline{
    agent any

    stages{
        stage("git checkout code"){
            steps{
                git branch: 'master', url: 'https://github.com/georgetoolit1/notejam-django.git'
            }
        }
        stage("build docker image"){
            steps{
                script {
                    app = docker.build("nevis256/pipeline:${env.BUILD_ID}")
                }
            }
        }
    }
}