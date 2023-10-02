pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'main']], userRemoteConfigs: [[url: 'https://github.com/NielsTjenkins/Jenkinsfile.git']]])
            }
        }
        stage('Deploy to ProgramData') {
            when {
                expression { currentBuild.rawBuild.getBranch().getName() == 'main' }
            }
            steps {
                echo 'Deploying to ProgramData'
                // Copy all files to ProgramData directory
                bat 'xcopy .\\* "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\Nielsie123321_main\\*.html" /E /Y'
            }
        }
        stage('Deploy to Apache Web Server') {
            when {
                expression { currentBuild.rawBuild.getBranch().getName() == 'main' }
            }
            steps {
                echo 'Deploying to Apache Web Server'

                // Copy all files from ProgramData to Apache web server directory
                bat '"C:\\Program Files\\PuTTY\\pscp.exe" -i "C:\\Program Files\\Key.ppk" -r "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\Nielsie123321_main*.html\\" student@192.168.29.67:/var/www/html/'
            }
        }
    }
}
