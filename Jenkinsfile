
pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
        timestamps()
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mkdir -p dist'
                sh 'cp index.html dist/index.html'
            }
        }

        stage('Test') {
            steps {
                sh 'test -f dist/index.html'
                sh 'grep -q "DevOps Lab" dist/index.html'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'dist/index.html', fingerprint: true
            }
        }
    }
}
