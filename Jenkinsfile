pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                docker image build -t myapp .
                '''
            }
        }
        stage('Test') {
            steps {
                sh 'docker container run -d --name myapp myapp'
            }
        }
        stage('deploy') {
            steps {
                sh 'echo deploying...'
            }
        }
    }
}
