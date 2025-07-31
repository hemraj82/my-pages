// Write Jenkins pipeline code here
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    def timestamp = new Date().format("yyyyMMdd-HHmmss")
                    docker.build("my-node-app:${timestamp}")
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    def timestamp = new Date().format("yyyyMMdd-HHmmss")
                    docker.image("my-node-app:${timestamp}").inside {
                        sh 'npm test'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def timestamp = new Date().format("yyyyMMdd-HHmmss")
                    docker.image("my-node-app:${timestamp}").inside {
                        sh 'npm run deploy'
                    }
                }
            }
        }
    }
}
