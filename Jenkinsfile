pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Test') {
            steps {
                echo 'Running application test...'
                bat 'findstr /C:"CI/CD Pipeline Version 2!" index.html'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'

                bat 'docker build -t nawfel03/my-web-app:%BUILD_NUMBER% .'
            }
        }

        stage('Docker Login') {
            steps {

                withCredentials([
                    usernamePassword(
                        credentialsId: 'dockerhub',
                        usernameVariable: 'DOCKER_USERNAME',
                        passwordVariable: 'DOCKER_PASSWORD'
                    )
                ]) {

                    bat '''
    @echo off
    echo %DOCKER_PASSWORD%| docker login -u "%DOCKER_USERNAME%" --password-stdin
'''
                }
            }
        }

        stage('Push Docker Image') {
            steps {

                bat 'docker push nawfel03/my-web-app:%BUILD_NUMBER%'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {

                echo 'Deploying application to Kubernetes...'

                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'

                bat 'kubectl set image deployment/my-web-app my-web-app=nawfel03/my-web-app:%BUILD_NUMBER%'

                bat 'kubectl rollout status deployment/my-web-app --timeout=120s'
            }
        }

        stage('Verify Deployment') {
            steps {

                echo 'Checking Kubernetes deployment...'

                bat 'kubectl get deployments'
                bat 'kubectl get pods'
                bat 'kubectl get services'
            }
        }
    }
}