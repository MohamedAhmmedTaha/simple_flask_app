pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub_credential') {
                        def customImage = docker.build("MohamedTaha55/flaskapp_v:0.0.1")
                        customImage.push()
                    }
                }
            }
        }
        stage('package') {
            steps {
                sh 'echo packaging....'
            }
        }
        stage('test') {
            steps {
                sh 'echo testing......'
            }
        }
    }
}
