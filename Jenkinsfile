pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building..."
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                 echo "Testing..."
            }
        }

        stage('Code Analysis') {
            steps {
                 echo "Analyzing..."
            }
        }

        stage('Security Scan') {
            steps {
                echo "Scaning..."
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploying..."
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                 echo "Testing..."
            }
        }

        stage('Deploy to Production') {
            steps {
                 echo "Deploying..."
            }
        }
    }

    post {
        always {
            // Archive logs as attachments
            archiveArtifacts artifacts: 'logs/**'
        }
        success {
            // Send success notification email
            emailext(
                subject: 'Pipeline Successful',
                body: 'The pipeline completed successfully.',
                to: 'nesalikarunarathne@gmail.com',
                attachmentsPattern: 'logs/**'
            )
        }
        failure {
            // Send failure notification email
            emailext(
                subject: 'Pipeline Failed',
                body: 'The pipeline failed. Please check the logs for more information.',
                to: 'nesalikarunarathne@gmail.com',
                attachmentsPattern: 'logs/**'
            )
        }
    }
}
