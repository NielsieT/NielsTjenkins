pipeline { agent any

stages {
    stage('Build') {
        steps {
            echo 'Building...'
        }
    }
    stage('Dev environment') {
        steps {
            input 'Do you approve deployment?'
            echo 'Hello Dev'
        }
    }
    stage('Beta environment') {
        steps {
            input 'Do you approve deployment?'
            echo 'Hello beta'
        }
    }
    stage('Production environment') {
        steps {
            input 'Do you approve deployment?'
            echo 'Hello Prod'
        }
    }
}
}
