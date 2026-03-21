// Jenkins Declarative Pipeline Example
pipeline {
    agent any  // Run on any available agent

    // Define environment variables
    environment {
        APP_NAME = "MyApp"
        DEPLOY_ENV = "staging"
    }

    options {
        timeout(time: 30, unit: 'MINUTES') // Fail if pipeline runs too long
        buildDiscarder(logRotator(numToKeepStr: '10')) // Keep last 10 builds
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out source code..."
                // Replace with your repository URL
                git branch: 'testing', url: 'https://github.com/Manikandankk12/New-Project.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building ${APP_NAME}..."
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml' // Publish test results
                }
            }
        }
        stage('Deploy') {
            when {
                branch 'main' // Deploy only from main branch
            }
            steps {
                echo "Deploying ${APP_NAME} to ${DEPLOY_ENV}..."
                sh './deploy.sh ${DEPLOY_ENV}'
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed. Please check the logs."
        }
        always {
            cleanWs() // Clean workspace after build
        }
    }
}

