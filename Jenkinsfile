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
        stage('Project Complete'){
            steps {
                 echo "completed..."
           }
        }
        
    }

   post {
        success {
            // Send success notification email
            mail (
                to: 'nesalikarunarathne@gmail.com'
                subject: 'Pipeline Successful',
                body: 'The pipeline completed successfully.',
                
            )
        }
        failure {
            // Send failure notification email
            mail (
                to: 'nesalikarunarathne@gmail.com'
                subject: 'Pipeline Failed',
                body: 'The pipeline failed. Please check the logs for more information.',
               
            )
        }
    }
}
