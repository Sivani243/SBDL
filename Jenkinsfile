pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'pipenv install --dev'
            }
        }

        stage('Test') {
            steps {
                sh 'pipenv run pytest'
            }
        }

        stage('Package') {
            when {
                anyOf {
                    branch 'master'
                    branch 'release'
                }
            }
            steps {
                sh 'zip -r sbdl.zip lib'
            }
        }

        stage('Release') {
            when {
                branch 'release'
            }
            steps {
                echo 'Release stage: Add deployment logic if server available'
            }
        }

        stage('Deploy') {
            when {
                branch 'master'
            }
            steps {
                echo 'Deploy stage: Add production deployment logic if server available'
            }
        }
    }
}
