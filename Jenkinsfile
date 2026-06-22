pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // 깃허브에서 코드를 받아오는 단계
                checkout scm
            }
        }
        stage('Install') {
            steps {
                bat 'npm install'
            }
        }
        stage('Test') {
            steps {
                bat 'set CI=true && npm test'
            }
        }
        stage('Start') {
            when {
                branch 'main'
            }
            steps {
                // main.bat 파일을 실행해보는 단계
                bat 'main.bat'
            }
        }
    }
    post {
        success {
            echo 'Pipeline 성공적으로 완료!'
        }
        failure {
            echo 'Pipeline 실패!'
        }
    }
}