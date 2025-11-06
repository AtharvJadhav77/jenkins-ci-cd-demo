pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-creds',
                    url: 'https://github.com/AtharvJadhav77/jenkins-ci-cd-demo.git'
            }
        }

        stage('Set up Python Environment') {
            steps {
                echo 'Setting up virtual environment...'
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                sh '. venv/bin/activate && pytest'
            }
        }

        stage('Build and Deploy') {
            steps {
                echo 'Build successful! Deploying application...'
                // Example placeholder; add deployment steps here
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed. Check logs for errors.'
        }
    }
}
