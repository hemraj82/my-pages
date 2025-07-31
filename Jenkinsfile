// Write Jenkins pipeline code here
pipeline {
    agent any
    environment {
        TIMESTAMP = sh(script: 'date +%Y%m%d-%H%M%S', returnStdout: true).trim()
        PATH = "/usr/local/bin:/opt/homebrew/bin:${env.PATH}"
    }
    stages {
        stage('Build') {
            steps {
                sh "which docker"
                sh "ls"
                sh "docker build -t my-node-app:${TIMESTAMP} ."
            }
        }
        stage('Test') {
            steps {
                sh "docker run --rm my-node-app:${TIMESTAMP} npm test"
            }
        }
        stage('Deploy') {
            steps {
                sh "docker run --rm my-node-app:${TIMESTAMP} npm run deploy"
            }
        }
    }
}
