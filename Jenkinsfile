pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Haal de openbare Git-repository op
                git branch: 'main', url: 'https://github.com/NielsieT/NielsTjenkins.git'
            }
        }

        stage('Deploy to Test Apache') {
            steps {
                // Kopieer het HTML-bestand naar de test-Apache-webserver
                sh 'cp NielsTjenkins/index.html /var/www/test-html/'
            }
        }

        stage('Deploy to Main Webserver') {
            steps {
                // Verplaats het HTML-bestand van de test-Apache-webserver naar de hoofdwebserver
                sh 'mv /var/www/test-html/je-html-bestand.html /var/www/html/'
            }
        }
    }

    post {
        success {
            // Als de
