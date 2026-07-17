pipeline{
    agent any

    stages{

        stage('Clone') {
            steps{
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps{
                bat 'docker build -t flask-app:latest .'
            }
        }

        stage('Deploy to kubernets') { 
            steps{
                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'
            }
        }

        stage('Verify Deployment') {
            stages{
                bat 'kubectl get pods'
                bat 'kubectl get services'
            }
        }
        
    }
}