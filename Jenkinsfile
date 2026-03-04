pipeline {
    agent {
        docker {
            image 'node:22-alpine'
            args '-u root:root' 
        }
    }

    options {
        ansiColor('xterm')
    }

    environment {
        CI = 'true'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm ci'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npx vitest run --reporter=verbose'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Mock deployment was successful!'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Build SUCCESS ✅'
        }
        failure {
            echo 'Build FAILED ❌'
        }
    }
}