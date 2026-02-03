pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/awsdevopspractice677/real-time-devops-project.git'
            }
        }

        stage('Build Backend JAR') {
            steps {
                sh '''
                  cd app
                  mvn clean package -DskipTests
                '''
            }
        }

        stage('Build Backend Image') {
            steps {
                sh '''
                  cd app
                  docker build -t backend:v1 .
                '''
            }
        }

        stage('Build Frontend Image') {
            steps {
                sh '''
                  cd frontend
                  docker build -t frontend:v1 .
                '''
            }
        }
    }

    post {
        success {
            echo "✅ CI pipeline completed successfully"
        }
        failure {
            echo "❌ CI pipeline failed"
        }
    }
}

