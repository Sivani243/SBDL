pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'pipenv install --dev'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pipenv run pytest'
            }
        }

        stage('Package Project') {
            steps {
                sh 'zip -r sbdl.zip lib conf log4j2.xml sbdl_main.py sbdl_submit.sh'
            }
        }
    }
}
