pipeline {
    agent any

    triggers {
       githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                deleteDir()
                checkout scm
                echo "Tag: ${env.GIT_REF}"
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}
