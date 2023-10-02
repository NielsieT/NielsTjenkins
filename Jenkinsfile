pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/NielsieT/NielsTjenkins.git'
            }
        }
        stage('Deploy to ProgramData') {
            when {
                expression { currentBuild.rawBuild.getEnvironment().get('BRANCH_NAME') == 'main' }
            }
            steps {
                echo 'Deploying to ProgramData'
                // Copy all files to ProgramData directory
                bat """
                xcopy *.html "C:/ProgramData/Jenkins/.jenkins/workspace/Nielsie123321_main/" /E /Y /EXCLUDE:exclude.txt
                """


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
