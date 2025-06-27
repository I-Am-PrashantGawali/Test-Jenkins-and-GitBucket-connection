pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                // git branch: 'main', url: 'https://github.com/I-Am-PrashantGawali/Test-Jenkins-and-GitBucket-connection.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // To force fail:
                // error('Force a failure!')
            }
        }
    }

    post {
        success {
            slackSend (
                channel: '#jenkins-notify',
                color: 'good',
                message: "✅ *BUILD PASSED* for ${env.JOB_NAME} #${env.BUILD_NUMBER} <${env.BUILD_URL}|Open>",
                tokenCredentialId: 'SMS',   // <<< SAME FIX
                teamDomain: '',              // <<< Empty if using xoxb bot
                botUser: true
            )
        }
        failure {
            slackSend (
                channel: '#jenkins-notify',
                color: 'danger',
                message: "❌ *BUILD FAILED* for ${env.JOB_NAME} #${env.BUILD_NUMBER} <${env.BUILD_URL}|Open>",
                tokenCredentialId: 'SMS',
                teamDomain: '',
                botUser: true
            )
        }
    }
}

