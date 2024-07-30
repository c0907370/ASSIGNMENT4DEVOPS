pipeline {
    agent any
    environment {
        DOCKER_CREDENTIALS_ID = 'docker-hub'
        DOCKER_REPO = 'c0907370@mylambton.ca/assignment4devops'
    }
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/c0907370/ASSIGNMENT4DEVOPS'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    def app = docker.build("${env.DOCKER_REPO}:${env.BUILD_ID}")
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('', env.c0907370@mylambton.ca) {
                        def app = docker.build("${env.DOCKER_REPO}:${env.BUILD_ID}")
                        app.push("${env.BUILD_ID}")
                        app.push("latest")
                    }
                }
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
