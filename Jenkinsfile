pipeline {
    agent any

    environment {
        DOCKERHUB_UN = 'mostafaye7ia'
    }

    stages {
        stage('Build') {
            steps {
                sh '''
                    docker image build -t $DOCKERHUB_UN/myapp .
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''
                    docker container rm myapp -f
                    docker container run -d --name myapp -p 9090:80 $DOCKERHUB_UN/myapp
                    sleep 5
                    curl localhost:9090
                '''
            }
        }
        stage('Deliver') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKERHUB_UN', passwordVariable: 'DOCKERHUB_PASS')]) {
                    sh '''
                        docker login -u $DOCKERHUB_UN -p $DOCKERHUB_PASS
                        docker push $DOCKERHUB_UN/myapp
                    '''
                }
            }
        }
        stage('deploy') {
            steps {
                sh 'kubectl run myapp --image $DOCKERHUB_UN/myapp'
            }
        }
    }
}
