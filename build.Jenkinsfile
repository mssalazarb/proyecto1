pipeline {
    agent any

    environment {
        GITHUB_EVENT = sh(script: 'echo $GITHUB_EVENT', returnStdout: true).trim()
    }

    stages {
        stage('Checkout') {
            when {
                expression { env.GITHUB_EVENT == 'push' }
            }
            steps {
                deleteDir()
                checkout scm
            }
        }

        stage('Build') {
            when {
                expression { env.GITHUB_EVENT == 'push' }
            }
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            when {
                expression { env.GITHUB_EVENT == 'push' }
            }
            steps {
                sh 'mvn test'
            }
        }
    }
}
