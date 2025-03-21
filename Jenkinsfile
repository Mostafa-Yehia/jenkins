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
                sh '''
                    docker container run -d --name myapp -p 9090:80 myapp
                    curl localhost:9090
                '''
            }
        }
        stage('Deliver') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKERHUB_UN', passwordVariable: 'DOCKERHUB_PASS')]) {
                    sh '''
                        docker login -u $DOCKERHUB_UN -p $DOCKERHUB_PASS
                        docker push myapp
                    '''
                }
            }
        }
        stage('deploy') {
            steps {
                sh 'echo deploying...'
            }
        }
    }
}
