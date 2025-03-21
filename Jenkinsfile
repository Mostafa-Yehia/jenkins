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
                sh 'docker conatiner run -d --name nginx nginx:alpine'
            }
        }
        stage('deploy') {
            steps {
                sh 'echo deploying...'
            }
        }
    }
}
