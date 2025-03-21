pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                echo $HOME
                echo $USER
                ls
                '''
            }
        }
        stage('Test') {
            steps {
                sh 'docker --version'
            }
        }
        stage('deploy') {
            steps {
                sh 'echo deploying...'
            }
        }
    }
}
