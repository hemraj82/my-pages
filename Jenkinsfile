// Write Jenkins pipeline code here
pipeline {
    agent any
    environment {
        TIMESTAMP = sh(script: 'date +%Y%m%d-%H%M%S', returnStdout: true).trim()
    }
    stages {
        stage('Build') {
            steps {
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
