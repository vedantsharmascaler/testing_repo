pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = "ap-south-1"
    }

    stages {
        stage('Checkout Source') {
            steps {
                git branch: 'e2e_project', url: 'https://github.com/adityaloka/testing_repo.git'
            }
        }

        stage('Build Image') {
            steps {
                script {
                    sh 'docker build -t adityalokapalli309/react-app:v4 .'
                }
            }
        }
        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhubcreds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo "$PASS" | docker login -u "$USER" --password-stdin'
                }
            }
        }

        stage('Push') {
            steps {
                sh 'docker push adityalokapalli309/react-app:v4'
            }
        }

        stage('Deploy to EKS') {
            steps {
                sh 'kubectl config use-context arn:aws:eks:ap-south-1:074004850362:cluster/Final-EKS-Scaler'
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
    }
}
