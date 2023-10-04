pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Replace 'https://github.com/NielsieT/NielsTjenkins.git' with your Git repository URL
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
                xcopy *.html "C:/ProgramData/Jenkins/.jenkins/workspace/Nielsie123321_main/" /E /Y
                """
            }
        }
        stage('Deploy to Apache Web Server') {
            when {
                expression { currentBuild.rawBuild.getBranch().getName() == 'main' }
            }
            steps {
                echo 'Deploying to Apache Web Server'

                // Replace placeholders with appropriate values
                // - Update the paths, private key file, and IP address
                bat '"C:\\Program Files\\PuTTY\\pscp.exe" -i "C:\\Path\\To\\Your\\Key.ppk" -r "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\Nielsie123321_main\\*.html" student@192.168.29.67:/var/www/html/'
            }
        }
    }
}
