pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Build the code using Maven
                sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests using a test automation tool (e.g., JUnit)
                sh 'mvn test'

                // Run integration tests using a test automation tool (e.g., Selenium)
                sh 'mvn integration-test'
            }
        }

        stage('Code Analysis') {
            steps {
                // Integrate a code analysis tool (e.g., SonarQube)
                // Run code analysis using the tool
                sh 'sonar-scanner'
            }
        }

        stage('Security Scan') {
            steps {
                // Perform security scan using a security scanning tool (e.g., OWASP ZAP)
                sh 'owasp-zap scan'
            }
        }

        stage('Deploy to Staging') {
            steps {
                // Deploy the application to a staging server (e.g., AWS EC2 instance)
                sh 'ansible-playbook deploy-staging.yml'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on the staging environment
                sh 'mvn integration-test'
            }
        }

        stage('Deploy to Production') {
            steps {
                // Deploy the application to a production server (e.g., AWS EC2 instance)
                sh 'ansible-playbook deploy-production.yml'
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
