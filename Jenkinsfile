pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout your code from your version control system (e.g., Git)
                checkout scm
            }
        }
        
        stage('Deploy to Web Server') {
            steps {
                script {
                    def remoteServer = [:]
                    remoteServer.name = 'WebServer'
                    remoteServer.host = '192.168.29.50'
                    remoteServer.user = 'student'
                    
                    // Use the Jenkins credential for SSH password
                    remoteServer.password = credentials('student')
                    
                    // Copy your HTML file to the web server directory using SSH
                    sshPut remote: remoteServer, from: 'index.html', into: '/var/www/html/'
                }
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
