pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git url: 'https://github.com/vaschiho/jenkins-project.git', branch: 'main'
                sh "ls -ltr"
            }
        }

        stage('Setup') {
            steps {
                sh "pip3 install -r requirements.txt
            }
        }

        stage('Test') {
            steps {
                sh "pytest"
            }
        }

    }
}
