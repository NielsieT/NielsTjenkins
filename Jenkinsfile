pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from the 'main' branch
                script {
                    def scmVars = checkout([
                        $class: 'GitSCM',
                        branches: [[name: 'main']],
                        userRemoteConfigs: [[url: 'https://github.com/NielsieT/NielsTjenkins.git']]
                    ])
                }
            }
        }
        
        stage('Deploy to Server') {
            when {
                expression { currentBuild.rawBuild.getEnvironment().get('BRANCH_NAME') == 'main' }
            }
            steps {
                echo 'Copying HTML files to the server'
                bat 'echo y | pscp -pw student "${WORKSPACE}/*.html" student@192.168.29.67:/var/www/html/'
            }
        }
    }
}
