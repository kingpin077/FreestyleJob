pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
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
                //bat 'npm test'
                //bat 'set CI=true && npm test'
                bat 'set CI=true && npm test -- --passWithNoTests' // set CI=true: 파이프라인 환경임을 명시, --passWithNoTests: 테스트 코드가 0개라도 실패 처리하지 않고 성공(Code 0)으로 통과
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