pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            reuseNode true
        }
    }
    
    environment {
        NODE_ENV = 'production'
    }
    
    stages {
        stage('Checkout') {
            steps {
                git url: 'http://gogs:3000/owner/todo.git',
                    credentialsId: 'a7345ab7-808a-4b24-ad99-1af417c51aac'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'npm ci || npm install'
            }
        }
        
        stage('Run Linter') {
            steps {
                sh 'npm run lint'
            }
        }
        
        stage('Run Tests') {
            steps {
                sh 'npm run test'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image (placeholder)'
            }
        }
    }
}
