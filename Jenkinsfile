pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'main']], userRemoteConfigs: [[url: 'https://github.com/NielsieT/NielsTjenkins.git']]])
            }
        }
        
        stage('Deploy to Test Server') {
            when {
                expression { currentBuild.branchName == 'main' }
            }
            steps {
                echo 'Deploying to Test Server'
                bat "\"C:\\Program Files\\PuTTY\\pscp.exe\" -i \"C:\\Users\\Administrator\\NIELSTEST\\Documents\\Key.ppk\" -r ./* student@192.168.29.50:/var/www/html/"
            }
        }
        
        stage('Deploy to Production Server') {
            when {
                expression { currentBuild.branchName == 'main' }
            }
            steps {
                echo 'Deploying to Production Server'
                bat "\"C:\\Program Files\\PuTTY\\pscp.exe\" -i \"C:\\Users\\Administrator\\NIELSTEST\\Documents\\Key.ppk\" -r ./* student@192.168.29.67:/var/www/html/"
            }
        }
    }
}
