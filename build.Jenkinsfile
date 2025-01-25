pipeline {
    agent any

    stages {
        stage('Checkout') {
            when {
                branch 'master'
            }
            steps {
                deleteDir()
                checkout scm
            }
        }

        stage('Build') {
            when {
                branch 'master'
            }
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            when {
                branch 'master'
            }
            steps {
                sh 'mvn test'
            }
        }
    }
}