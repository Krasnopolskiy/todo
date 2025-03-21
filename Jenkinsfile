pipeline {
    agent any
    
    environment {
        BASE_IMAGE = 'node:18-alpine'
        NODE_ENV = 'production'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Install Dependencies') {
            agent {
                docker {
                    image "$BASE_IMAGE"
                    reuseNode true
                }
            }
            steps {
                sh 'npm ci || npm install'
            }
        }
        
        stage('Run Linter') {
            agent {
                docker {
                    image "$BASE_IMAGE"
                    reuseNode true
                }
            }
            steps {
                sh 'npm run lint'
            }
        }
        
        stage('Run Tests') {
            agent {
                docker {
                    image "$BASE_IMAGE"
                    reuseNode true
                }
            }
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
