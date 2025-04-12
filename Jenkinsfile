pipeline {
    agent any  // Runs on any available agent (node)
    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning code from GitHub...'
                git branch: 'main', url: 'https://github.com/radhikapathak-devops/radhika-devops-assignment.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building the project for devops assignment'
            }
        }
        stage('Test') {
            steps {
                echo 'Running testst for devops assignment'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying code to Staging Environment...'
                bat 'if not exist staging mkdir staging'
                bat 'del /Q staging\\*'
                bat 'xcopy src\\* staging\\ /E /Y /I'
            }
        }
        stage('Manual Approval') {
            steps {
                input message: 'Approve deployment to production?', ok: 'Deploy Now'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying code to Production Environment...'
                bat 'if not exist production mkdir production'
                bat 'del /Q production\\*'
                bat 'xcopy src\\* production\\ /E /Y /I'
        }
    }
    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs!'
        }
    }
}