pipeline {
    agent any   // Run on any available Jenkins agent

    stages {
        stage('Checkout') {
            steps {
                // Pull the code from your Git repository
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                // If your Python file needs dependencies, install them here
                sh 'python3 -m pip install --upgrade pip'
                sh 'pip3 install -r requirements.txt || true'
            }
        }

        stage('Run Python Script') {
            steps {
                // Run your Python file
                sh 'python3 add_numbers.py'
            }
        }

        stage('Deploy') {
            steps {
                // Example deployment step (adjust to your environment)
                echo 'Deploying Python application...'
                // You could copy files, restart services, or trigger another job here
            }
        }
    }

    post {
        success {
            echo 'Deployment completed successfully!'
        }
        failure {
            echo 'Deployment failed. Please check logs.'
        }
    }
}

