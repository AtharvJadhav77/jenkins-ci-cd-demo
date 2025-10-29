pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/AtharvJadhav77/jenkins-ci-cd-demo.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Run App') {
            steps {
                sh 'nohup python3 app.py &'
            }
        }
    }
    post {
        success {
            echo '✅ Flask app deployed successfully!'
        }
        failure {
            echo '❌ Deployment failed.'
        }
    }
}
