pipeline{
    agent any

    stages{
        stage("Checkout"){
            steps{
                git branch: 'master', url: 'https://github.com/georgetoolit1/notejam-django.git'
            }
        }
        stage("Build"){
            steps{
                script {
                    app = docker.build("nevis256/notejam:${env.BUILD_ID}")
                }
            }
        }
        stage("Run tests"){
            steps{
                step {
                    sh 'docker run -it nevis256/notejam:${env.BUILD_ID} ./manage.py test'
                }
            }
        }
    }
}