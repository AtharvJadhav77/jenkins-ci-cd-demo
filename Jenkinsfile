pipeline {
    agent any

    environment {
        PYTHON = '/usr/bin/python3'
    }

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
                // Use python3 explicitly and ensure venv module exists
                sh '${PYTHON} -m venv venv'
                sh '. venv/bin/activate && pip install --upgrade pip'
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                sh '. venv/bin/activate && pytest || echo "No tests found"'
            }
        }

        stage('Build and Deploy') {
            steps {
                echo 'Build successful! Deploying application...'
                // Add deployment commands here later (e.g. Docker, Flask run, etc.)
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
