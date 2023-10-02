pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/NielsieT/NielsTjenkins.git'
            }
        }
        
        stage('Deploy to Production Server') {
            when {
                expression { currentBuild.rawBuild.getEnvironment().get('BRANCH_NAME') == 'main' }
            }
            steps {
                echo 'Copying HTML files to the production server'
                bat 'echo y | pscp -pw student "C:\\Programdata\\Jenkins\\.jenkins\\workspace\\Nielsie123321\\index.html" student@192.168.29.67:/var/www/html/'
            }
        }
    }
}
