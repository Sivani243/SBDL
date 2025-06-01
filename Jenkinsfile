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
                bat 'echo Release step - SCP skipped on Windows'
                // If needed: implement file copy using WinSCP or similar here
            }
        }

        stage('Deploy') {
            when {
                branch 'master'
            }
            steps {
                bat 'echo Deploy step - SCP skipped on Windows'
                // If needed: implement file copy using WinSCP or similar here
            }
        }
    }
}
