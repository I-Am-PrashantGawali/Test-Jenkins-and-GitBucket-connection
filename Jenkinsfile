pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/I-Am-PrashantGawali/Test-Jenkins-and-GitBucket-connection.git'
            }
        }
        stage('Build') {
            steps {
                sh 'echo Building the app...'
            }
        }
        stage('Test') {
            steps {
                sh 'echo Running tests...'
            }
        }
    }
}

