pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker-token')
        DOCKER_IMAGE = 'mssalazarb/first-api-rest-f'
        DOCKER_TAG = 'latest'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    sh "sudo docker build -t ${DOCKER_IMAGE}:${DOCKER_TAG} ."
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    sh "echo ${DOCKERHUB_CREDENTIALS} | docker login -u mssalazarb --password-stdin"

                    sh "sudo docker push ${DOCKER_IMAGE}:${DOCKER_TAG}"
                }
            }
        }
    }

    post {
        always {
            script {
                sh "sudo docker logout"
            }
        }
    }
}
