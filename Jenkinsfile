pipeline {
    agent any  // Runs on any available Jenkins agent
    stages {
        stage('Clone Repository') {  // First stage: Cloning the repo
            steps {
                git branch: 'jenkins', url: 'https://github.com/vedantsharmascaler/testing_repo.git'  // Cloning the repo
            }
        }
        stage('Run Script') {  // Second stage: Executing the script
            steps {
                sh 'chmod +x script.sh'  // Make the script executable
                sh './script.sh'  // Execute the script
            }
        }
    }
}
