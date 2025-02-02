pipeline {
    agent any
    environment {
        DOCKER_CREDENTIALS_ID = 'docker-hub-credentials'
        DOCKER_IMAGE = 'MohamedTaha55/simple_flask_app'
    }
    stages {
        stage('Build and Push Docker Image') {
            steps {
                script {
                    def image = docker.build(DOCKER_IMAGE, '.')
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub_credential') {
                        image.push('latest')
                    }
                }
            }
        }
    }
}
