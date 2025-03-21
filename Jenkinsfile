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
                checkout scm
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
                // Placeholder for Docker build step
                echo 'Building Docker image (placeholder)'
                
                // Uncomment and modify this when you're ready to implement Docker build
                // sh '''
                //     docker build -t devops-todo:${BUILD_NUMBER} .
                // '''
            }
        }
    }
}
