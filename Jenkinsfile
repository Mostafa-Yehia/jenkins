pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                echo $HOME
                echo $USER
                '''
            }
        }
        stage('Test') {
            steps {
                sh 'echo testing...'
            }
        }
        stage('deploy') {
            steps {
                sh 'echo deploying...'
            }
        }
    }
}
