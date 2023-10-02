pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/NielsieT/NielsTjenkins.git'
            }
        }
        
        stage('Deploy to Test Server') {
            when {
                expression { currentBuild.rawBuild.getEnvironment().get('BRANCH_NAME') == 'main' }
            }
            steps {
                echo 'Copying HTML files to the test server'
                bat 'echo y | pscp -pw student "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\Nielsie123321_main\\*.html" student@192.168.29.67:/var/www/html/'
            }
        }
    }
}
