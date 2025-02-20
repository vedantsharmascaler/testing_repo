pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'jenkins', url: 'https://github.com/vedantsharmascaler/testing_repo.git'
            }
        }
        stage('Build') {
            steps {
                echo "Building the application..."
                sh 'echo Build Successful!'
            }
        }
        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'echo All tests passed!'
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying application..."
                sh 'echo Deployment Complete!'
            }
        }
    }
}
