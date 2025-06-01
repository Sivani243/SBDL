pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'pipenv install --dev'
            }
        }
        stage('Test') {
            steps {
                bat 'pipenv run pytest'
            }
        }
        stage('Package') {
            when {
                anyOf { branch 'master'; branch 'release' }
            }
            steps {
                bat 'powershell -Command "Compress-Archive -Path lib -DestinationPath sbdl.zip"'
            }
        }
        stage('Release') {
            when {
                branch 'release'
            }
            steps {
                bat 'echo Release step - skipping SCP on Windows for now'
                // Replace with WinSCP or skip for now if you don't have a remote server
            }
        }
        stage('Deploy') {
            when {
                branch 'master'
            }
            steps {
                bat 'echo Deploy step - skipping SCP on Windows for now'
                // Replace with WinSCP or skip for now if you don't have a remote server
            }
        }
    }
}
