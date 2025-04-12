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
                sh 'rm -rf staging/*'
                sh 'cp -r src/* staging/'
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
                sh 'rm -rf production/*'
                sh 'cp -r src/* production/'
            }
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