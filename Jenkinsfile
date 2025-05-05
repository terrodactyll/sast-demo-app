pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/terrodactyll/sast-demo-app'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install bandit
                '''
            }
        }
        stage('SAST Analysis') {
            steps {
                sh '''
                    . venv/bin/activate
                    bandit -r .
                '''
            }
        }
    }
}
