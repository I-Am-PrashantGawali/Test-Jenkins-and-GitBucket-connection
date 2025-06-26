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
    post {
        failure {
            slackSend (
                channel: '#ci-alerts',
                color: 'danger',
                message: "*BUILD FAILED* <${env.BUILD_URL}|View Details> for job ${env.JOB_NAME} #${env.BUILD_NUMBER}"
            )
        }
    }
}

