pipeline{
    agent any

    stages{
        stage("Git Checkout"){
            steps{
                git branch: 'master', url: 'https://github.com/georgetoolit1/notejam-django.git'
            }
        }
        stage("Docker Image Build"){
            steps{
                script {
                    app = docker.build("nevis256/notejam:${env.BUILD_ID}")
                }
            }
        }
        stage("Run tests"){
            steps{
                script {
                    sh 'docker run -it nevis256/notejam:${env.BUILD_ID} ./manage.py test'
                }
            }
        }
    }
}