pipeline {
    agent any   // Run on any available Jenkins agent

    stages {
        stage('Checkout') {
            steps {
                // Pull code from your Git repository
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Example build step
                echo 'Building project...'
            }
        }

        stage('Test') {
            steps {
                // Example test step
                echo 'Running tests...'
            }
        }

        stage('Deploy') {
            steps {
                // Example deploy step
                echo 'Deploying application...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check logs.'
        }
    }
}

