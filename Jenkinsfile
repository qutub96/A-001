pipeline {
    agent any
    environment {
        DOCKER_HUB = credentials('docker-hub-creds')
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t yourusername/ml-model:${GIT_COMMIT} .'
            }
        }
        stage('Push') {
            steps {
                sh '''
                    echo $DOCKER_HUB_PSW | docker login -u $DOCKER_HUB_USR --password-stdin
                    docker push yourusername/ml-model:${GIT_COMMIT}
                '''
            }
        }
    }
}
