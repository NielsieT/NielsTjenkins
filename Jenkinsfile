pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'main') {
                        echo 'Checking out the main branch...'
                        checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/NielsieT/NielsTjenkins.git']]])
                    } else {
                        echo "Skipping checkout for branch: ${env.BRANCH_NAME}"
                    }
                }
            }
        }

        stage('Deploy to Test Server') {
            when {
                expression { env.BRANCH_NAME == 'main' }
            }
            steps {
                echo 'Copying HTML files to the test server...'
                bat 'echo y | pscp -pw student "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\Nielsie123321_main\\*.html" student@192.168.29.67:/var/www/html/'
            }
        }
    }
}
