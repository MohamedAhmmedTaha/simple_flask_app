pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub_credential') {
                        def customImage = docker.build("mohamedtaha55/flaskapp_v:0.0.1")
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
            agent {
                docker {
                    image 'ubuntu:latest'  
                }
            }
            steps {
                sh 'echo testing......'
            }
        }

        stage('deploy') {
            input {
                message "Do you want to deploy the container?"
            }
            steps {
                sh 'docker run -d --name flaskapp -p 5555:5000 mohamedtaha55/flaskapp_v:0.0.1'
            }
        }
    }
}
