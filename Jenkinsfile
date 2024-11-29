pipeline {
    environment {
        registry = 'jenk_deneme/ml_model'
        dockerImage = ''
    }
    agent any
    stages {
        stage('Build Docker Image') {
            agent any
            steps {
                script {
                    sudo chmod 666 /var/run/docker.sock
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }

    }
}
