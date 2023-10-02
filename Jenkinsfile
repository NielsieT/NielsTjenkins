pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Wepsel/html3.git'
            }
        }
        
        stage('Deploy to Production Server') {
            when {
                expression { currentBuild.rawBuild.getEnvironment().get('BRANCH_NAME') == 'main' }
            }
            steps {
                echo 'Copying HTML files to the production server'
                bat 'echo y | pscp -pw student "C:\\Program Files\\Jenkins\\Multipipeline\\*.html" student@10.0.0.26:/var/www/html/'
            }
        }
    }
}
