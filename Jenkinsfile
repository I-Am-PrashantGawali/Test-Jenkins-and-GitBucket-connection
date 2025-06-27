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
            sh '''
                curl -X POST -H 'Content-type: application/json' \
                --data '{"text":"✅ *BUILD PASSED* for ${JOB_NAME} #${BUILD_NUMBER} 🎉 <${BUILD_URL}|Open>"}' \
                https://hooks.slack.com/services/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
            '''
        }

        failure {
            sh '''
                curl -X POST -H 'Content-type: application/json' \
                --data '{"text":"❌ *BUILD FAILED* for ${JOB_NAME} #${BUILD_NUMBER} <${BUILD_URL}|Open>"}' \
                https://hooks.slack.com/services/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
            '''
        }
    }
}

