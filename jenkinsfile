pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout your HTML file from your version control system (e.g., Git)
                checkout scm
            }
        }
        
        stage('Deploy to Web Server') {
            steps {
                // Copy your HTML file to the web server directory
                sh 'cp index.html /var/www/html/'
            }
        }
    }
    
    post {
        success {
            // If the deployment is successful, you can perform additional actions here
            // For example, you might trigger a notification or perform further testing
        }
        
        failure {
            // If the deployment fails, you can perform actions here
            // For example, you might send a notification or log the failure
        }
    }
}
