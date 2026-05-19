pipeline {
    agent any

    environment {
        VIRTUAL_ENV = 'venv'
        PATH = "${env.WORKSPACE}/venv/bin:${env.PATH}"
        SERVER_CRED = credentials('hope')
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/vaschiho/jenkins-project.git'
            }
        }

       stage('Install Dependencies') {
            steps {
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip setuptools wheel
                    pip install -r requirements.txt
                '''
                echo "The Path is ${env.PATH}"
                echo "echo credentials is ${SERVER_CRED_USR} and ${SERVER_CRED_PSW}"
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                    . venv/bin/activate
                    pytest
                '''
            }
        }
    }
}