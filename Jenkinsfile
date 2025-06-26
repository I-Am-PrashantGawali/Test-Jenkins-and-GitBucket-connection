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
        success {
            slackSend(
                channel: '#ci-alerts',
                color: 'good',
                message: "*BUILD PASSED* for ${env.JOB_NAME} #${env.BUILD_NUMBER} 🎉 <${env.BUILD_URL}|Open>"
            )
        }

        failure {
            slackSend(
                channel: '#ci-alerts',
                color: 'danger',
                message: "*BUILD FAILED* for ${env.JOB_NAME} #${env.BUILD_NUMBER} ❌ <${env.BUILD_URL}|Open>"
            )
        }
    }
}

