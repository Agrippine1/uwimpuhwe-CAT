
pipeline {
    agent any

    options {
        timestamps()
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Downloading Juice Shop source code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Installing project dependencies'
                sh 'npm ci'

                echo 'Building Juice Shop application'
                sh 'npm run build'
            }
        }

        stage('Automated Testing') {
            steps {
                echo 'Running automated tests'
                sh 'npm test'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Build and tests completed!'
        }

        failure {
            echo 'FAILURE: Check the Jenkins console output.'
        }

        always {
            echo 'Jenkins pipeline execution finished.'
        }
    }
}
