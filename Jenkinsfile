pipeline {
    environment {
        BASE_IMAGE = 'node:18-alpine'
        NODE_ENV = 'production'
    }

    agent {
        docker {
            image "$BASE_IMAGE"
            reuseNode true
        }
    }
    
    stages {
        stage('Checkout') {
            steps {
                // More explicit checkout configuration
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    extensions: [],
                    userRemoteConfigs: [[
                        url: 'https://github.com/Krasnopolskiy/todo.git'
                    ]]
                ])
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
