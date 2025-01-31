pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the source code...'
                checkout scm
            }
        }

        stage('Restore Dependencies') {
            steps {
                echo 'Restoring project dependencies...'
                sh 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'dotnet build --configuration Release'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'dotnet test --no-restore --configuration Release'
            }
        }

        stage('Publish') {
            steps {
                echo 'Publishing the application...'
                sh 'dotnet publish --no-restore --configuration Release --output ./publish'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully! The build, test, and publish stages passed.'
        }
        failure {
            echo 'Pipeline failed. Check the logs for details.'
        }
    }
}
